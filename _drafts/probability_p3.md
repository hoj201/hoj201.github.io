---
layout: post
title: Probabilistic notation is the worst: Part III
subtitle: (now with Machine Learning)
---

<!-- Summary:  measure theory works pretty well with category theory.  We can extend the projection map into a functor to create the category of probability theory.  So first review measure theory.  The objects are cones of measures (define measure), and the arrows are conditional distributions.  Composition is the chain rule.

Baye's Theorem just says that the conditional measures form a groupoid.

PGMs:  It's tempting to relate PGMs because they are directed networks, but this does not quite work. PGMs are the probabilistic analog of computation graphs.  A computation graph is just a graphical representation of a way of computing a function.  So any function has a family of computation graphs. We can embed the space of computation graphs into the space of PGMs by embedding into Dirac measures.
-->

In the last post [link]() I discussed how probability theory deserves its own category, in the same way that other sub fields of mathematics do.  In particular, measure theory is one such field.  This will be a short post which accomplishes one thing.  We define the category of measure spaces, and then a functor which maps the measure category to the category of probabilities.

# What's category
Before giving a raw definition, let me just flip through some examples of categories:
  - Linear algebra is a category, consisting of vector spaces and linear transformations.
  - Group theory is a category, consisting of groups and group homomorphisms.
  - Topology is a category, consisting of topological spaces and continuous maps.
  - Differential geometry is a category, consisting of smooth manifolds and smooth maps.

Now for a (semi-formal) definition

## Functors


# The category of measures

## The objects

## The arrows

## The composition

# From measures to probabilities

## The objects

## The arrows

## The composition
