---
layout: default
title: Probabilistic notation is the worst II (Even worser)
---

I ended an [earlier post](blah) by suggesting a new definition of a probability distribution.


Just as a refresher, I'd like to think of probabilities as measures modulo scaling.
Geometrically, this entails defining a probability as a ray in a vector space.

## Reasons why this definition is better (if you like diagrams)
 - Conditional probability appears naturally as pull-backs
 - Independence appears as a co-product
 - Marginals are push-forwards
 - Baye's theorem arises from intersection being a sigma algebra morphism
 - It does not prohibit improper priors.

## Previous work
After a little digging, it seems that other people have thought along similar lines.
I noticed it pop up on [This blog](link) which cites, [this recent pre-print](https://arxiv.org/abs/1710.08933), which then cites both Renyi and Kolmogorov.
So maybe I'm crazy, but there something valuable here that other people besides me seem to like about this line of thought.  In particular, the above citations were motivated by a desire to incorporate "improper" priors  into probability theory by redefining things.

## Uh "improper"?
  In a nutshell, an improper probability distribution is something like the Lebesgue
measure on the reals, $$\lambda$$.  This is not a probability distribution because the
total mass is not 1.  In fact, the mass is infinite, and so we
can't even normalize $$\lambda$$.  There's no way to get a traditional probability
distribution out of $$\lambda$$.  However, the notion of an equitable distribution
over the reals makes intuitive sense, and [comes up a lot in statistics](https://en.wikipedia.org/wiki/Prior_probability#Improper_priors)

## Rays to the rescue
While we may not be able to normalize $$\lambda$$, the ray of $$\lambda$$ is still
well defined.  In fact, for any $$\sigma$$-algebra $(\Omega,X)$
the Ray is well defined for all $$\sigma$$-finite measures [wikipedia](https://en.wikipedia.org/wiki/%CE%A3-finite_measure).
For a topological spaces, where we invoke the Borel $$\sigma$$-algebra,
this means any distribution which has finite mass on compact sets has a well defined ray.

## Frechet Sigma algebras
We define a Frechet sigma algebra as one where there are a countable family $$F$$ of
algebra elements which cover $$X$$.
I call it a Frechet sigma algebra because this family equips the space $$\bar{\mathbb{R}}^\Sigma$$
with a Frechet topology via the semi-norms $$\| f \|_{x}_{} = | f(x) |$$.
We then can consider all the measure for which are finite on individual elements of this family.
For example, $$X = \mathbb{R}$$ and we consider the family of compact sets.
With respect to this topology, $$\lambda$$ is bounded.
In contrast, $$\lambda$$ is infinitely distant from $0$ with respect to the traditional
toplogy induced by the 1-norm.
We then consider the ray-space of the Frechet-space induced by a Frechet sigma-algebra.
