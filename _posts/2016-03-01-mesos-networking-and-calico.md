---
layout: post
title: Mesos Networking and Calico
---

We’ve been focused quite a lot on
[Apache Mesos](http://mesos.apache.org/) and a few frameworks 
lately. As we progress on the implementation of our distributed
infrastructure, new problems continuously emerge. This is obviously
what it takes to run large scale systems.

A recent problem we encoutered, involved the current state of Mesos
networking. Especially, the fact that containers share the slaves’ IP
addresses. As we plan to run multiple versions of machine learning
models in our cluster for multiples clients, this constraint makes our
development cycle very painful.

In fact, this limitation engender several problems. For example, an
obvious one is port conflict, where if two apps want to use the same
port on a slave, one will fail to start. (we often ended up with
Zookeeper instances listening on diverse uncommon ports such as
_2182_, _2183_,… instead of the traditionally used _2181_ port) This
obstacle also makes it harder to manage and update proxy settings.
More, knowing which version of a service is at each port is difficult
and isolating different users, services, or divisions becomes quite
confusing.

A lot is currently discussed among the Mesos contributors to take on
theses issues. (i.e. [MESOS-2044](https://issues.apache.org/jira/browse/MESOS-2044))

On the other hand, projects such as [Kubernetes](http://kubernetes.io/) already implement
`IP-per-container` in their network isolation where an `IP-per-pod`
approach is used to help them create clean, backward-compatible model
where pods can be treated much like VMs or physical hosts from the
perspectives of port allocation, networking, naming, service
discovery, load balancing, application configuration and migration.

Kubernetes seems to answer our problems conveniently but nothing is
lost with Apache Mesos as it implements a useful feature called [Mesos
Modules](http://mesos.apache.org/documentation/latest/modules/) since
v0.21.0. It allowed developers to integrate interesting networking
module solutions without getting their hands too much dirty.

# The Project Calico

We’re currently experimenting with a project called
[Project Calico](http://www.projectcalico.org/learn/) which solve most
of the issues previously stated. 

Project Calico is a Layer 3 approach to virtual networking for highly
scalable data centers. Calico as a networking model is applicable to a
multitude of cloud systems. It provides us with network isolation
between workloads using
[BGP](https://en.wikipedia.org/wiki/Border_Gateway_Protocol) route
management rather than an encapsulating overlay network.

<center>
<img src="https://d262ilb51hltx0.cloudfront.net/max/800/1*us5m2r7XNpqnz0wQ1QclLQ.png" height="400" />
</center>

As documented in their website, Calico connects each workloads via a
vRouter directly to the infrastructure network without overlay,
tunneling or VRF tables. There is no requirement for NAT in Calico
network, since any workload can be assigned a public IP address which
is directly reachable from the internet — provided you configure a
security policy to allow this.

Calico comes up with several interdependent components:

- Felix, the primary Calico agent that runs on each machine that hosts
  endpoints.
- Orchestrator Plugin, orchestrator-specific code that tightly
  integrates Calico into that orchestrator. (i.e. in our case [Apache
  Mesos modules for network isoluation](https://github.com/mesosphere/net-modules)) 
- [Etcd](https://coreos.com/etcd/), the data store.
- BGP Client (BIRD), a BGP client that distributes routing
  information. 
- BGP Route Reflector (BIRD), an optional BGP route reflector for
  higher scale.

The Project Calico seems to fit well in our infrastructure to overcome
the networking isolation limitations we talked about through this
report. As we’re already running ZooKeeper in our cluster for Mesos
and other realated frameworks, deploying etcd was a bit irritating but
we’ve quickly been overwhelmed by how much Calico facilitate our
networking workflow. To keep up with Calico releases:
[@projectcalico](http://twitter.com/projectcalico) on Twitter. To
learn more about what’s being discussed for the per-container IP
assignment, enforcement and isolation in Apache Mesos, a design
document is publicly accessible
[right here](https://docs.google.com/document/d/17mXtAmdAXcNBwp_JfrxmZcQrs7EO6ancSbejrqjLQ0g/edit).
