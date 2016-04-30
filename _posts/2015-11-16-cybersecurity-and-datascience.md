---
layout: post
title: Cybersecurity and Data Science
---

At Ognitio, we develop large scale infrastructures in order to prepare
startups and companies to a world that is in perpetual change. As we
solve problems in a wide variety of domains by applying recent
techniques in data science, we couldn't get away without undertaking
extensive researches in cybersecurity. 

As computers have become more connected than ever before, security has
become a major concern. Today, we report for you some of our
knowledge.

Not surprisingly, despite the success of modern methods, there are
still opportunities for further enhancements. Furthermore, data mining
and machine learning approaches seem to have taken over the discipline
and are now predominantly present in most of our recent accomplishments. 

Today, cyberinfrastructure define complex system with loads of
interactions between hosts and applications. This complexity
dramatically diversifies the methods applied to protect us against
potential threats.

We can derive plenty of features to train very sophisticated models,
including sequences of system calls, start time, duration of a network
flow, source IP and source port, destination IP and destination port,
protocol, number of bytes, and number of packets. This vast amount of
data extracted from large scale infrastructures makes data mining and
machine learning, statistics and other inter disciplinary capabilities
very useful to address the challenges of cybercrime.

Throughout the years, several algorithms have been extensively used to
solve very specific problems in cybersecurity. It is usefull to
categorize them into subgroups. Here's a non-exhaustive list:

- Misuse/signature detection
- Anomaly/outlier detection
- Scan detection
- Profiling modules

We'll go through some of them in the following subsections.

# Misuse/signature detection

Misuse/signature detection is, perhaps, the easiest principle to get
our hand on. The concept is to use the power of supervised learning
algorithms to detect known malicious patterns.

Supervised learning algorithms are well understood techniques in
machine learning where the underlying goal is to figure out
parameters via optimization methods to transform a given input space
to an output space. The optimization methods can be quite diverse. To
name a few popular techniques: linear regression, logistic regression,
SVMs...

Misuse/signature detection techniques works by gathering past labeled
examples of, let's say, network packets or system calls from which an
algorithm can learn about threats. An obvious limitation lies on the
fact that our data doesn't cover every aspect of vulnerabilities. Even
through these techniques are very efficient against known threts, they
present several drawbacks, namely false positives, novel attacks and
complication of obtaining initial data from the training phase.

- SVM. Input: **TCP/IP data offline**. (Mukkamala and Sung (2003))
- Classification and regression trees. Input: **Frequency of system
calls offline**. (Chebrolu et al. (2005))
- Decision trees. Input: **TCP/IP data online**. (Kruegel and Toth (2003))
- Artificial Neural Networks. Input: **TCP/IP data offline**. (Mukkamala
and Sung (2003))
- Bayesian Network. Input: **Frequency of system calls offline**.
(Chebrolu et al. (2005))

# Anomaly/outliers detection

Anomaly/outlier detection techniques are a direct consequence of
the lack of labeled data. In this scenario, we usually attempt to
detect "uncommon" behaviors by looking for deviation from normal or
established patterns within given data.

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*smmwkEQPJNgzJCwhIuzOIg.png)

Anomaly detection systems constantly evolve. This approach allows us
to detect previously unknown attacks. In the machine learning
literature, we would tend to label these problems as unsupervised
problems.

Netflix, in fairly recent post, described a unsupervised machine
learning algorithm used to detect outliers (i.e. sick hosts) among
thousands of servers. Although they've got promising results, some of
the commenters proposed far less complex approaches such as integral
analysis. This ...

Hybrid versions have been discussed in the past to combine all the
benefits of anomaly detection and misuse detection techniques.

- Principal component analysis (PCA). Input: **TCP/IP data, online**.
(Ringberg et al. (2007))
- SVM. Input: **TCP/IP data, offline**. (Hu et al. (2003), Chen et al.
(2005))
- Unsupervised clustering algorithm. Input: **TCP/IP data, offline**.
  (Leung and Leckie (2005))
