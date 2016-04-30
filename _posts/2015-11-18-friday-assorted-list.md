---
layout: post
title: Friday Assorted List
---

<center><img src="http://i.imgur.com/IVOsc16.jpg" height="400" /></center>

I read and learn about a lot of things on the internet. I share with
you some of my findings from this week:

- The engineers at Sift recently published
  [an interesting article with a great insights](http://blog.siftscience.com/blog/2015/large-scale-decision-forests-lessons-learned)
  about their experience with decision forests trees and a few past
  models for their fraud detection engine. They ended up with an
  in-house customized solution. Here some of the resulting statistics:
  - Hundred of trees
  - Over 10s of million of samples
  - A few hours of training
  - Significant infrastructure cost saving

- [Science Isn’t Broken](http://fivethirtyeight.com/features/science-isnt-broken/):
  Would you like to hack some p-values? This great article go in depth
  into why p-values, which is defined as the probability under the
  null hypothesis, can in a lot of cases be harmful and damage your
  conclusions. P-values tend to overstate the evidence against the
  null, and are thus very "trigger happy".

- Streaming data processing is attracting a lot of attention these
  days. This is a big deal. But a lot of streaming systems are either
  immature or lack in essential abilities. Their complexity lies
  behind the very wide range of applicability. I recommend you to take
  a look at [Spark Streaming](http://spark.apache.org/streaming/)
  which is a well maintained and promising data processing project.
  [Some engineers at Google wrote a paper about Dataflow and provide us with a lot more details on the subject](http://www.vldb.org/pvldb/vol8/p1792-Akidau.pdf).

- [The Person I Call Most for Startup Advice](http://fourhourworkweek.com/2015/08/18/the-evolutionary-angel-naval-ravikant/).
  Insightful wide-ranging conversation between Tim Ferriss
  ([@tferriss](https://twitter.com/tferriss)) and Naval Ravikant
  ([@naval](https://twitter.com/naval)) on startups, ethics,
  mindfulness, self-improvement, evolution and more. There is plenty
  of references you might want to take some notes.

- LSTM Recurrent Neural Networks predominantly occupied of lot of my
  time last year at Google. They look quite complex but are very
  fascinating. Traditional recurrent neural networks naturally
  incorporate memory and time-based dependencies which allow them to
  learn and predict from sequences. (Speech recognition, text
  processing,...) However, they struggle to learn long term
  dependencies as the error signal vanishes rapidly when getting
  backpropagated in the past. This is where LSTM RNNs come in action:
  [Understanding LSTM Networks](http://colah.github.io/posts/2015-08-Understanding-LSTMs/index.html).

- [Ten scariest theories known to man](http://imgur.com/a/TDsYx).

- [A/B Testing with Hierarchical Models in Python](http://blog.dominodatalab.com/ab-testing-with-hierarchical-models-in-python/):
  There were a lot of hype in the industry lately about A/B testing
  methods. As useful as they can be to your business, a few practices
  will tend to increase the likelihood of false positives and mislead
  your decisions.

- Eigenvalues and Eigenvectors were one of the most counter-intuitive
  and weird notion I've learned in linear algebra. And yet, they
  represent the underlying foundation of so many concepts in machine
  learning.
  [Here is good introduction by deeplearning4j](http://deeplearning4j.org/eigenvector).

- Very complete post about [How does a relational database work](http://coding-geek.com/how-databases-work/).
