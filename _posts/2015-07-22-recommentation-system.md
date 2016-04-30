---
layout: post
title: Recommendation systems
---

This is a blog post about recommender systems. This month, I've been
working on several projects involving sophisticated recommendation
algorithms. So It might be good to summarize some of my knowledge and
thoughts on the subject.

As machine learning is getting more and more popular in the industry,
recommender systems are particularly doing well. Netflix, the popular
streaming service, is the host of a contest (i.e. The Netflix Prize)
where scientists and engineers participate to improve the accuracy of
predictions about how much an individual will enjoy a movie. In 2009,
the best team came to be awarded a prize of 1 million dollars for a
10% improvement against their previous systems. Recommender systems
take gradually an important part in the business model of various
companies.

The recommendation problem can intuitively be represented as a matrix
containing ratings where the columns define the users and the rows,
the items.

<center><img width="500" src="http://i.imgur.com/q4zVp5z.png">
</center>


Let $C$ be the set of all users and let $S$ be the set of all possible
items that can be recommended. The central problem of recommender
systems lies in that the utility function $u$ which maps a user and an
item to a rating, i.e. $C \times S \rightarrow R$ where $R$ is often a
nonnegative integer with a certain range, is often not defined on the
whole $C \times S$ space. The goal of recommenders might then be to
extrapolate the missing ratings.

In the literature, recommender systems are usually divided in three
categories:

- **Content-based recommendations**: The users are recommended items
similar to the ones they preferred in the past.
- **Collaborative recommendations**: The users are recommended items
based on people with similar tastes.
- **Hybrid approaches**: These techniques combine collaborative and
content-based methods.

They all show pros and cons but the hybrid versions often show more
attractiveness in several problems as they try to solve issues such as
the new user problem, the new item problem, nonintrusiveness and
more... We'll talk more about it later on.

# Content-Based Recommendations

As previously stated, content-based methods predict user's missing
ratings based on his past actions. In order to do so, the items need
features such as keywords, dates or authors to evaluate level of
similarities between items. In the case of movies this could simply be
the genre. (i.e. horror, action, comedy...)

Information retrieval and information filtering has a long history
with problems of such nature.

We can easily see that content-based recommendations mainly favor text
based applications. So, how do we weight similarities between items
and predict ratings? Various machine learning techniques have been
used in the past to answer this question. Methods such as Bayesian
classifiers, clustering, decision trees and artificial neural networks
can score very well in those tasks. We might for example, use a Naive
Bayes classifier to classify items as "relevant" or "irrelevant" by
the user given a set of keywords:

<p><center> $P(C\_i|k\_{1j},...,k\_{nj})$ </center></p>

We can then make the assumption that keywords are independent and,
therefore, the above probability is proportional to

<p><center>$P(C\_i)\prod\limits\_{x}P(k\_{xj}|C\_i)$</center></p>

Both factors $P(C\_i)$ and $\prod\_{x}P(k\_{xj}|C\_i)$ can be
estimated from the underlying training data. Therefore, for each page
$p\_j$, the probability $P(C\_i|k\_{1j},...,k\_{nj})$ is computed for
each class $C\_i$ and page $p_j$ is assigned to class $C\_i$ having
the highest probability.

Content-based recommendations present some limitation such as:

- **Limited content analysis**: The techniques are limited by the
  features that are explicitly associated with the objects that the
  systems recommend. The features might, for example, need to be
  extracted from text documents.
- **Overspecialization**: The recommendations are limited in being
    similar to those already rated by the users. Introducing some
    randomness could be necessary.
- **New user problem**: The user often has to rate a sufficient
      number of items before content based recommender systems can
      understand the user's preferences.


# Collaborative Recommendations

Collaborative recommendation systems make the assumption that the
missing ratings of an individual can be predicted through the users'
ratings who share similar tastes.

One commonly used technique is known as the nearest neighbor.

**TODO(rzagabe):** More is yet to come

Collaborative recommendations present some limitation such as:

- New user problem:
- New item problem:

# Hybrid Approaches

Most popular recommendation systems are hybrid approaches where
content based and collaborative recommendation techniques are combined
in order to overcome their individual limitations.

**TODO(rzagabe):** More is yet to come
