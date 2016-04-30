---
layout: post
title: Frameworks on Apache Mesos
---

We previously talked a bit about our production stack. We’re now going
deeper into the container orchestration system used at Ognitio: Apache
Mesos. Mesos plays a central role in the management of our services as
it provides us with very convenient abstractions to control complex
systems and our resources.

Apache Mesos is an open source project originally developed at the
University of California, Berkeley. The project has been deployed in
several large companies such as Twitter, Netflix or Apple. It has
extensively been inspired by a few large-scale cluster management
schedulers like
[Borg](http://static.googleusercontent.com/media/research.google.com/en//pubs/archive/43438.pdf)
and
[Omega](http://eurosys2013.tudos.org/wp-content/uploads/2013/paper/Schwarzkopf.pdf)
running at Google. Today, Mesos gathers hundreds of contributors and
thousands of enthusiasts around the globe. 


<center>
<img
src="https://raw.githubusercontent.com/ServiceStack/Assets/master/img/livedemos/techstacks/apache-mesos-logo.png"
width="500">
</center>

To describe it simply, Apache Mesos is a cluster management system
which allows you to run a huge amount of jobs across multiple
machines. It assures fault-tolerant operations and elastic distributed
systems to run tasks effectively.

The “data centers as a computer” crusade has been going on for a
number of years. These ideas were mainly made possible via the usage
of containers isolation instead of virtual machines which helped
developers launch new instances in a few seconds. One can imagine the
effect of such improvements at the scale of a company like Google.
This evolution resulted in an avalanche of new tools and gained an
enormous amount of energy in software development processes.

These recent advancements allow developers to build better products,
measure revenues and losses efficiently, optimize infrastructure costs
and confidently iterate releases for their applications. As a business
is growing, visibility, control and reactivity become major
requirements.

Orchestration systems such as Mesos have been developed with a lot of
expectations:

- Effective usage of resources
- Scalability
- Fault tolerance
- Job allocation problems (i.e. services, batch jobs and cron jobs)
- Load trend monitoring (e.g. autoscaling, automatic rollback…)
- and more…

In this article we will describe how Apache Mesos and his framework
abstraction are used at Ognitio to solve our problems and provide
distinguished services.

# Mesos Architecture

As stated before, Apache Mesos manages cluster of machines and provide
practical abstraction to manipulate resources. It consists of master
and slave daemons running in the cluster’s nodes.

<center>
<img src="http://mesos.apache.org/assets/img/documentation/architecture3.jpg" height="400" />
</center>

The masters, a quorum of replicas, manage the slaves where your tasks
will run. There is no scheduling logic built-in around Mesos. For such
thing, you’ll need a framework to schedule your tasks. What the Mesos
masters do, is constantly provide frameworks with updated resources
offers. The frameworks then accept or decline these offers in order to
execute new tasks. A framework can be viewed in two distinct parts: a
scheduler and an executor.

The schedulers act like services which manage resources offers from
the Mesos masters. When it accepts an offer, it then gives the master
needed information about what’s to run in the slave (i.e. executor &
task). A scheduler also provides further capabilities to manage the
kind of apps it is supposed to control. In fact, it is the
intelligence around what’s running. For example, a Kafka framework
might interface methods to add/update/list topics, partitions and
brokers.

The executors are generally very short programs that get executed in
the Mesos slaves and run the tasks it has been requested by the
scheduler.

The frameworks often come with a REST API and a CLI to help human
operators or other systems granularly manage their tasks. You could,
for instance, build up an auto scaling orchestration system outside of
your schedulers.

<center>
<img src="https://d262ilb51hltx0.cloudfront.net/max/800/1*BqKvLFbTnu8D-AZWBHeWaQ.jpeg" height="400" />
</center>

To name a few popular frameworks, Marathon is one of them. It runs on
top of Apache Mesos and provides needed scheduling features for long
running services such as high availability, service discovery,
constraints or health checks. It also comes with a neat web interface.

Apache Aurora is another, more sophisticated, framework that we use in
our clusters.

Mesos frameworks are elegant ways to think about your cluster. In the
next section we’ll see a very quick overview about multi-frameworks
infrastructures and how they make our development life cycle easier.

# Multi-Frameworks Infrastructure

There are numerous of reasons why you might want to write your own
frameworks. One of them being operational automation for your tasks.
If there were no schedulers, you would have to write down most of the
intelligence and configurations independently in each one of your
apps. With frameworks you have the convenient ability to namespace and
control your environment effectively.

<center>
<img src="https://d262ilb51hltx0.cloudfront.net/max/800/1*Fy7quS5FFXwlt2idvkEiXg.jpeg" height="400" />
</center>

Things get exciting as you get hierarchical dependencies between your
schedulers. For example, a logging framework might depends on a
several other schedulers such as Kafka (which in turn depends on
Zookeeper), Flume and Elasticsearch.

<center>
<img src="https://d262ilb51hltx0.cloudfront.net/max/800/1*f29bx4KSntOdeAaS-6YUmQ.jpeg" height="400" />
</center>

Schedulers generally get started via another frameworks for high
availability. As they get launched, we give them information on where
to localize the Mesos masters in order to run and manage further
tasks.

Another attractive feature is that some of the service’s names can be
generated from the schedulers and pass down to other running
frameworks and services. This lets us not having to worry about
service discovery.

In a future article, we’ll see more about the underlying function of
our homemade frameworks.
