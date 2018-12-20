---
layout: post
title: Variational Auto-encoders in a nutshell
comments: true
tags: math, AI
---

The goal of this post is to describe variational auto-encoders (VAEs) as succinctly as possible.

## The model
We assume that whenever we receive a datapoint $$x$$ it is drawn from a distribution $$\Pr(x \mid z)$$ with respect to some latent variable, $$z$$. We also assume that $$z \sim \rho$$ for some simple prior, $$\rho$$, that we can easily draw samples from (e.g. Gaussians).  If you understand the last sentence, all the pieces follow.

## VAEs
Let's assume we can represent $$\Pr(z \mid x)$$ and $$\Pr(x \mid z)$$ can be approximated 
