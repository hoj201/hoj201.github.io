---
layout: default
title: And another thing
---

I ended an [earlier post](blah) by suggesting a new definition of a probability distribution.  After some more digging, it seems that other people have thought along similar lines.
Just as a refresher, I'd like to think of probabilities as measures modulo scaling. Geometrically, this entails defining a probability as a ray in a vector space.

## Previous work
It seems like this idea has popped up a few times.  I noticed it pop up on [This blog](link) which cites, [this recent pre-print](https://arxiv.org/abs/1710.08933), which then cites both Renyi and Kolmogorov as thinking upon similar lines.  So maybe I'm crazy, but there something her that people besides me seem to like about this line of thought.  In particular, the above citations were motivated by a desire to incorporate "improper" priors  into probability theory by redefining things.

## Uh "improper"?
  In a nutshell, an improper probability distribution is something like the Lebesgue
measure on the reals.  This is not a probability distribution because the
total mass is not 1. It's "improper" because the total mass is infinite, and so we
can't even normalize $$\lambda$$.  There's no way to get a traditional probability
distribution out of $$\lambda$$.  However, the notion of an equitable distribution
over the reals makes intuitive sense, and [comes up a lot in statistics](https://en.wikipedia.org/wiki/Prior_probability#Improper_priors)

## Rays to the rescue
While we may not be able to normalize $$\lambda$$, the ray of $$\lambda$$ is still
well defined.  In fact, for any $$\sigma$$-algebra $(\Omega,X)$
the Ray is well defined for all $$\sigma$$-finite measures [wikipedia](https://en.wikipedia.org/wiki/%CE%A3-finite_measure).
For a topological spaces, where we invoke the Borel $$\sigma$$-algebra,
this means any distribution which has finite mass on compact sets has a well defined ray.
