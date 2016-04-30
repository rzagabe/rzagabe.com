---
layout: post
title: An Introduction to Artificial Neural Networks
---

These last few months, I've been focusing on several fascinating
machine learning fields as part of my second internship at _Google_,
and one of them, is about **Artificial Neural Networks**.

Even though, I'm a software engineer, I've always been captivated by
everything related to neuroscience. This is an incredible subject in
which the mysteries around our cognitive abilities constantly amaze
me.

What makes the human brain so special? What does the human brain has
that other animals don't? Is consciousness just a purely subjective
experience? If you have no control whatsoever over your genome or
development of your brain, is free will simply an illusion?[1](#ab)
How does psychedelic drugs dramatically affect our
subconscient?[2](#cd) What profile are more subject to false memory
syndromes?

Artificial neural network is one of those fields showing us by how
much there's still room for creativity and advancements in computer
science.

<center><img height="400" src="http://annmaryliu.files.wordpress.com/2012/05/neuron-network_invert.jpg"></center>

[<a name="update">**Note 08/11/14:**</a> I've got a few comments concerning the fact that we should avoid using biological analogies to describe artificial neural networks.

I deeply agree with those claims and I've never argued the opposite. I often get frustrated when reading mainstream media writing about ANNs. But don't blame them, blame the readers. Still, there are plenty of good reasons to talk about neural processing in order to introduce people to ANNs. Please, check out the following interview of Michael Jordan, a consequent contributor in the field, to understand my position in this matter: [Machine-Learning Maestro Michael Jordan on the Delusions of Big Data and Other Huge Engineering Efforts](http://spectrum.ieee.org/robotics/artificial-intelligence/machinelearning-maestro-michael-jordan-on-the-delusions-of-big-data-and-other-huge-engineering-efforts).]

# "We are our brains"

Brains are constituted on average of 86 billions neurons in which
almost 16 billions are located in the cerebral cortex which the
primary function plays a key role in memory, awareness, thoughts
language or emotions... The human brain has a more developed
**cerebral cortex** than any other **mammals** and that is what makes
us, in a sense, so special.

The neocortex is entirely about memorizing patterns and this is an
important advantage that categorizes us as humans. It is the feedback
system that allows us to constantly make predictions. The human
experience is full of them. Language, for example, could be thought as
very familiar patterns of signals firing between neurons inside your
neocortex, ready to predict the next word of this... sentence.

One main misconception in neuroscience was that the brain works like a
black box processing and manipulating incoming information and
returning responses, however, it is a bit more complex and elegant
than that. Indeed, our brains continually create patterns in the
communication between their neurons. Let's say you always leave your
computer turned on when you leave your room. Days after days, a model
gets formed in the behavior of your neurons. But if at some point, you
get back into your room and find that your computer is down, those
neurons will stop firing the same way they used to do each time you
were getting inside your room, this uncommon behavior can be seen as
the awareness that something went wrong with your computer.

I like to think of brains, not as storing devices, but as unceasingly
behaving systems.

Nervous systems are active structures composed of neural cells, or
neurons, that can communicate through different channels and perform a
large variety of functions.

Neurons receive signals via **the dentrites** and produce a response
transmitted by **the axon**. The dendrites receive the signals at the
contact region with other cells, **the synapses**. *Synapses* allow a
neuron to pass electrical chemical signals to another cell.

Nerve cells self organize themselves and fire signals all the time.
You might think that you can force yourself to stop thinking, but you
persistently do, and most of the time, we're not even aware of those
thoughts. Our brains behave like monkeys and it can be proven that
most of our lives are about "what am I going to have for lunch?"...

# Artificial Neural Networks

We'll see that artificial neural networks are not that different from
our magnificent biological system in their most basic definitions.
They are composed of input channels, units and output channels. I will
introduce you here to the very basics.

An artificial network defines the interaction of several units. A
single unit (also called neuron, or cell) has one or more **real
valued edges as input**, an **integration function** that process the
inputs and produce a value passed to an **activation function** which
basically computes the output of the unit. The input edges are usually
weighted.

<center><img width="400"
src="http://i.imgur.com/Y3yBw1F.png"></center>

The *Perceptrons* are known to be a good introduction to neural
networks. They constitute a more general computational model than the
simple *McCulloch-Pitts* units introduced for the first time in 1945.
Here is how they work:

- They take as input $n$ real values $x\_1, x\_2, ..., x\_n$
- The integration function computes the sum $\sum x\_iw\_i$ where
$w_i$ is the input's associated edge weight $w\_1, w\_2, ..., w\_n$
- The activation function is a boolean function which tests the
  inequality $\sum x\_iw\_i \geq \theta$, where $\theta$ is the unit's
  threshold

To make equations easier to manipulate we usually include a _bias_ as
input ($x\_{n+1}$) which is defined as an edge with the constant value
1 and weights $-\theta$ ($w\_{n+1}$). This makes the inequality easier
to handle: $\sum x\_iw\_i \geq 0$

<center><img width="400"
src="http://i.imgur.com/DBOJzLG.png"></center>

Let's describe the unit's outputs:

<center>
$w \cdot x \geq \theta \Longleftrightarrow 1$

$w \cdot x < \theta \Longleftrightarrow 0$
</center><br/>

Please bear in mind though that there is plenty of ways to represent
neural network cells and that perceptrons are just one of them. We'll
see for example in other posts the variety of activation functions and
for what purpose they are used in the field.

Now that we have a decent representation of a unit, an obvious
question that should arise in your mind is, how do we compute
functions through a connected network of cells?

Artificial neural networks mainly work as classifiers. They literally
are meant to classify patterns of *features* (features, in our case,
are the inputs of the units). That said, they can also be used to
solve other problems: **classification** (or pattern recognition) and
**regression** problems. The former class of networks is trained to
output, at some point, discrete values (or labels). Handwriting
recognition, face detection, spam filtering can be categorized as
classification problems. The later variant is when the output is
real-valued for example financial time series forecast, in which case
we say that it is a regression problem.

# Learning algorithms

Machine learning algorithms are used to train neural networks in order
to specialize them in performing specific tasks from data.

There is this interesting paper titled
[“A Few Useful Things to Know about Machine Learning”](http://homes.cs.washington.edu/~pedrod/papers/cacm12.pdf),
which basically defines machine learning programs in three distinct
steps. **Representation**, **evaluation**, and **optimization**. Where
the representation determines the picture of the data used so that
they can make sense to computers. A good imaging and selection of the
data is often required to avoid misguided teaching. The evaluation
defines a cost function that scores the performance of the systems in
his associated task over classified data. The optimization is the
algorithm used to alleviate the evaluation score.

As I previously stated, there exists in **machine learning** several
classes of learning algorithms; The first one is known as **supervised
learning** which learn from given labeled sets of data (i.e.
$\\{(x\_1, y\_1),..., (x\_n, y\_n)\\}$). A good example could be a set
of data coupling numbers to their parity so that we have: $\\{(2, 0),
(10, 0), (3, 1)\\}$ where the class is a boolean value which
associates 0 to even numbers and 1 to odd numbers.

Another alternative of learning is, **unsupervised learning** which
goal is to classify unlabeled sets of data, an option used in biology
by data scientists when attempting to make sense of data. It is
considered as the Holy Grail by many, said to be the ability at which
the brain excel. Google has several
[projects and publications](http://static.googleusercontent.com/media/research.google.com/it/us/archive/unsupervised_icml2012.pdf)
involving the investigation of such problems which I believe will
constitute a primordial step in the next big tech revolution, _the
internet of things_, in a world where technologies will anticipate all
our needs.

To summarize, in our case, we could try to figure out an algorithm
that minimizes a loss function (our scoring function) while
calibrating the weights of the perceptron units contained in our
network. For example, a XOR function using three fully connected
units. You should now guess how the representation of the data should
look like in the matter of supervised learning.

I’m currently working on a concrete network implementation and will
publish a few more information about the learning algorithms.

# To conclude

The human brain is a biological, learning neural network. Today
researches on brains are getting better than few years ago. A primary
issue we have to deal with is that the diversity of data available is
incredibly huge and their computational representation can be tricky
to figure out. Think about that, on what metrics should you base your
algorithm to learn your classifier in the task of recognizing forms of
objects? Obviously, our human visuospatial abilities allow us to solve
such problems by ourselves without much trouble but computers are
still struggling to do so.

Keep in mind that ANNs aren't about duplicating human brains and that
a lot of aspects already don't correlate with our current, very short,
understanding of them (i.e. learning algorithms, backpropagation,...).
We are instead working on something bigger, which can match our
current needs and will certainly project us further.

Can you imagine by how much artificial neural networks and the
studying of nervous systems will help us in our evolution? So much
more is to come in the next few decades. I’m very optimistic about the
future of artificial intelligence and glad of being part of this
generation.

--------
<sub><a name="ab">1</a>: Free Will by Sam Harris - 2012<br/>
<a name="cd">2</a>: The Doors of Perception: Heaven and Hell by Aldous
Huxley - 1954</sub>
