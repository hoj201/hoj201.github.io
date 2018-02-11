---
layout: post
title: Probabilistic notation is the worst: Part III
subtitle: (now with Machine Learning)
---

In the last post [link]() I discussed how probability theory deserves its own category, in the same way that other sub fields of mathematics have their own category.  In particular, measure theory is one such field.  This will be a short post which accomplishes one thing, we will make a category for probability theory and tie it to the classical notions.

# The category of measurable spaces
A measurable space consists of a pair, $(X,\Sigma)$, where $\Sigma \subset 2^X$ is a $\sigma$-algebra.
We think of the elements of $\Sigma$ as events when we talk about probability.
Informally, a $\sigma$-algebra is just the algebraic entity which encodes the notion of a space of events.
For the formal definition see the wikipedia [link](https://en.wikipedia.org/wiki/Sigma-algebra).
The collection of all measurable spaces forms a category where the arrows are given by measurable maps.

# The category of measures
A measure on a measure space, $(X,\Sigma)$, is just a map $\mu: \Sigma \to \mathbb{R}^+ \cup \{ \infty\}$ such that
  - $\mu(\nullset) = 0$
  - $\mu \left( E_1 \uplus E_2 ) = \mu(E_1) + \mu(E_2)$
where $\uplus$ denotes disjoint union.
We denote the space of measures over a $(X,\Sigma)$ by $\mathcal{M}(X,\Sigma)$.

Note that given two measures $\mu_1,\mu_2 \in \mathcal{M}(X,\Sigma)$ we can sum them to get a measure $\mu_1 + \mu_2 \in \mathcal{M}(X,\Sigma)$ so that $\mathcal{M}(X,\Sigma)$ forms a [convex cone](https://en.wikipedia.org/wiki/Convex_cone).

In the map $(X,\Sigma) \mapsto \mathcal{M}(X,\Sigma)$ is actually a functor, but to clarify that I need to describe the arrows.

## Arrows between measure cones
Not that for each event $E \in \Sigma$, we can describe a new $\sigma$-algebra $(E, E \cap \Sigma)$
where
$$E \cap \Sigma := \{ E \cap \bar{E} \mid \bar{E} \in \Sigma \}$$.
In fact this characterizes all the sub-algebras of $\Sigma$.
So we see each $\sigma$-algebra is equipped with a set of map to it's sub-algebras.

A posterior measure is a map, $m: \mathcal{M}(\Sigma_1) \to \mathcal{M}(\Sigma_2)$ such that for any $E \in \Sigma_1$
there exists a unique map $m_E : \mathcal{M}(E \cap \Sigma_1) \to \mathcal{M}(\Sigma_2)$ such that the diagram

      m
S_1 ----- > S_2
^           /
| i        / m_E
|         /
E \cap S_1

commutes.

The correspondence with the classical notion of a posterior measure might not be obvious.
Given a classical posterior measure, $m(B \mid A)$ where $A \in \Sigma_1$ and $B \in \Sigma_2$
we also have a map which sends a measure $\mu_1 \in \mathcal{M}(X,\Sigma_1)$ to a measures $\mu_2 \in \mathcal{M}(Y,\Sigma_2)$
by
$$\mu_2(B) := m(B \mid X) \mu_1(X) \forall B \in \Sigma_2$$.
This mapping from $\mathcal{M}(X,\Sigma_1)$ to $\mathcal{M}(Y,\Sigma_2)$ completely characterizes the posterior $\mu(B\mid A)$.

(Sidetrack: this conversation closely resembles an introduction to sheaves.)

Having defined posterior measures in this way, we see that the posterior measures are good candidates for the arrows of the category of measures. We need only define the composition operation.

## The composition
The composition operation is (perhaps unsurprisingly) the chain rule of measure theory.
Given posteriors $m_1 :\mathcal{M}(X,\Sigma_1) \to \mathcal{M}(Y,\Sigma_2)$,
and a posterior $m_2:\mathcal{M}(Y,\Sigma_2) \to \mathcal{M}(Z,\Sigma_3)$, we can compose
them to get the posterior $m_3 = m_2 \circ m_1:\mathcal{M}(X,\Sigma_1) \to \mathcal{M}(Z,\Sigma_3)$.
If we write this composition down using classical notation we find
$$m_3(C \mid A) =  m_2(C \mid Y) m_1(Y \mid A)$.

## Our first functor
This gives us our first functor, which sends the category of $\sigma$-algebras to the category of measures cones.
For each $(X,\Sigma)$ there is a measure cone $\mathcal{M}(X,\Sigma)$,
and for each measureable map $f:X \to Y$ there is a posterior measure $m_f:$\mathcal{M}(X,\Sigma) \to \mathcal{M}(Y,\Sigma)$ given by $m_f(\mu)(B) = \mu(f^{-1}(B))$, basically sending a measure to its push-forward.
Note, this functor is not epic because not all posteriors are given by pushing forward measures.
In fact, the only posteriors that do this have a very Dirac-delta feel to them.  Hardly a typical posterior.

# From measures to probabilities
Getting from measures to probabilities is fairly trivial now.
We just apply the ray functor...  Wait, what's that?

We've already established that $\mathcal{M}(X,\Sigma_1)$ is a cone.
Therefore, the notion of a ray makes formal sense, and we can send each non-zero measure $\mu \in \mathcal{M}(X,\Sigma_1)$ to a ray $R[\mu] \in \mathcal{P}(X,\Sigma_1)$.
These rays are (very modest generalization of) probability densities on $(X,\Sigma_1)$.
This was the content of the last few posts.

I'd like to promote the assignment of "$\mu \mapsto R[\mu]$"" to a functor. To do so, I must figure out how $R$ should handle the arrows in the category of measure cones, the posterior measures.
The set of posterior measures between $\mathcal{M}(X,\Sigma_1)$ and $\mathcal{M}(Y,\Sigma_2)$ is itself a convex cone.
So again, the notion of a ray is well defined there.
The ray of a posterior measure is just what it sounds like, and applying $R$ to the posterior measures in this way gives us a functor to a new category, which we will call the category of probability.

## The category of probability theory
By fiat, lets just say that the functor $R$ is epic, so its image is the entire category.
In this new category, the objects are the spaces $\Pr(X,\Sigma)$ which consist of the ray space of $\mathcal{M}(X,\Sigma)$.  The rays themselves correspond with probability densities (see the first post).
The arrows correspond with our classical notion of posterior probabilities.
The composition operation corresponds with the the chain rule of probability theory.

## Baye's Theorem
Baye's theorem in this context simply states that the category of probability theory is actually a groupoid.
... wait what?

**Explanation**: Baye's theorem tells us how to swap the arguments of a posterior probability, effectively swapping the direction of an arrow in our category.  A category where are the arrows are reversible is called a groupoid.  So Baye's theorem is simply that the category of probability theory is a groupoid.
Anybody who's talked to me back in my geometric-mechanics days knows that I think groupoids are the best thing since sliced bread.

# Bayesian nets
This section is somewhat of a downer, but I thought I should include it just for clarification.  With all these diagrams and arrows being drawn, it's tempting to wonder "What does this have to do with probabilistic graphical models and Bayesian networks". Sorry to put a damper on the party, but not as much as one might imagine.

The arrows of a Bayesian network are not posteriors.  The arrows of a Bayesian network represent the flow of information in a computation graph.
This is probably a good time to clear up another misconception.
Bayesian networks are **not** generalizations of computation graphs.
Actually the reverse is the case.
Bayesian networks are **special cases** of computation graphs.
They correspond to the scenario where all the nodes are ray-spaces of probability distributions.

In fact the only thing I can see that category theory has to offer to the world of computation graphs is the notion of composition. Given two computation graphs with a single source node and a single target node, we can compose them to get another computation graph with a single source node and a single target node.
More generally, we can consider graphs with multiple source nodes, and multiple target nodes, and there is a notion of higher order composition from higher-order category theory which applies in this scenario.
Not sure if this clarifies anything.
Not sure if anything I wrote in this post clarified anything.

[Picture of Raul Duke Buy the Ticket Take the Ride]
