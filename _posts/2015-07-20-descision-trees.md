---
layout: post
title: Decision Trees and Random Forests
---
_Draft version. Last update: 20 July 2015_

**Adaptive basis function models** are useful models as they allow us
  to represent non-linear relationship between input and output
  spaces.

They include models such as neural networks, decision trees, bagging,
random forests, boosting or generalized additive models.

We're going to talk here about a few classification and regression
trees which quickly became the state of the art method in many
domains.

**CART** (Classification and Regression Trees) have a great history in
  various sub-fields of science such as medicine, physics or
  mechanical engineering. Random forests are responsible for the
  discovery of the Higgs Boson at CERN in 2012. Trees attractiveness
  lies mainly in their flexibility and their easy interpretation.

# Decision Trees

Decision trees are simple and useful for interpretation. They can be
applied to both regression and classification problems. Even though
their accuracy can be quite poor, they are the foundation of more
effective and sophisticated algorithms such as bagging, random forests
or boosting.

Decision trees work by recursively partitioning the input space. Each
one of the resulting input spaces represent a local model. The local
models can be expressed in diverse ways (e.g. point estimates such as
means or densities distributions). At each step, the algorithm selects
a feature and a threshold (i.e. regression setting) that best
minimizes a cost function. In the classification setting, we generally
store the distribution over class labels in each leaf.

As we go down in the tree, the splits contribute less and less
significantly to the minimization of the cost function.

We can conclude that the complexity of the models is expressed via the
amount elements contained in each one of the leafs in the tree. (i.e.
input space regions) The depth of the tree can be approximated via
cross-validation.

Let's say we want to predict the salary of new graduate students given
inputs such as their **grades**, **ages** and **sex**. The steps will
go as follow:

1. Divide the predictor space into two distinct regions by selecting a
   feature -that is, ages, grades or sex- that minimize at best our
   cost function.
   <center> $(j,t) = \arg\min\_{j \in {1,...,D}}\min\_{t \in T\_j}
   cost({x\_i,y\_i : x\_{ij} \leq t}) + cost({x\_i,y\_i : x\_{ij} >
   t})$ </center>
   where $j$ is the best feature and $t$ is the best threshold value.

2. Check the stopping criterion and repeat the split step in the
resulting regions.

The recursion stopping criterion can take many forms:

- The reduction in loss function becomes too small.
- The depth of the tree is too large.
- The resulting regions are homogeneous enough.
- The number of examples in each one of the regions are small enough.

<center><img height="400" src="http://i.imgur.com/sfeFob4.jpg">
_A simple regression tree._
</center>

The model can be expressed in the following form:
<center> $f(x) = \mathbb{E}[y|x] = \sum\_{m = 1}^{M}w\_m\mathbb{I}(x
\in R\_m) = \sum\_{m=1}^{M}w\_m\phi(x;v\_m)$ </center>
where $R\_m$ is the $m$'th region, $w\_m$ is the mean of the region.
(i.e. regression setting)

<center><img height="400" src="http://i.imgur.com/HxnvlFJ.png">
</center>

Decision trees shows several non-negligible advantages:

- They are non-parametric. They can model arbitrarely complex
relations between input and output without prior assumptions.
- They handle heterogenous data. The input space can be easily
represented as a mix of quantitative and qualitative values.
- They are easy to interpret and naturally implement feature
selection.

# Random Forests

Random forests answer several disadvantages of the decision trees. In
fact, decision trees accuracy can be poor. They are also quite
unstable. A little change in the input space generally implies
important change in the structure of the tree.

Random forests reduce the variance by constructing multitude of trees
over randomly generated subsets of data with replacement. They are
very similar to another technique known as **Bagging** but provide
improvements by operating over randomized and smaller subsets of input
variables in order to decorrelate the trees.

**TODO(rzagabe)**: ...

Random forests are widely used in the industry for broad range of
problems. The body pose recognition of the popular Microsoft's Kinect
sensor is a fine example. (i.e.
[Shotton et al. 2011](http://research.microsoft.com/pubs/145347/BodyPartRecognition.pdf))
