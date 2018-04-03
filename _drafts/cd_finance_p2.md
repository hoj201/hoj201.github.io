---
layout: post
title: Finance for mathematicians part II: Exterior calculus
tags: math, economics
---

This post is a sequel to [link to previous post here](;il)
Actually, this post is on another topic I never wrote any papers on, but thoroughly enjoyed nonetheless.
Discrete exterior calculus. (links to Topological data analysis, Topological combinatorics, discrete morse theory, discrete differential geometry)

## The olden days
A long time ago there was no motors, no combustion engines.... Carnot loops... this was the engine of the industrial revolution... engineers... me at Caltech... studied this loop in a biomech class... then a few years ago drew this diagram... If you're a mathematician you know there are no coincences, *the whole field is a conspiracy.*
They are all in on it. The industrialists, Carnot, those weird beetles, and now wall street.
I was not shocked to find my advisors, Mathieu Desbrun and Jerry Marsden were in on it too.
This goes deep. (PICTURE OF ILLUMNIATI)

## DDG
If all the contracts in the economy are represented by a discrete one form $\alpha$,
then the no-arbitrage principle says $d \alpha = 0$.
By a discrete analog of the poincare lemma this mean $\alpha = d f$ for some function $f$.
Which is just a cooky way of deriving the notion of intrinsic value.
Everything has a price.[^poincare lemma]  So the no-arbitrage principle now looks
super self-evident.  It appears to just claim that everything has a price.


How about when there is arbitrage? ... introduce work loops.
This principle was the engine of the industrial revolution (pun intended).
Once all the arbitrages are exploited you end up with an arbitrage free economy
and all diagrams commute.  However, this is rarely the case.  So what can be said in such cases.
We'll firstly, if $d \alpha \neq 0$, then there is no function $f$ such that $df = \alpha$.
Thus, there is no collective agreed price for the commodities in the economy.

That's not quite the end.  We know that $d(d\alpha) = 0$, does this translate to anything familiar?
Well if you draw the picture, it's not so crazy.  $\omega := d\alpha$ is a two-form an is cartooned using oriented triangles.
That $d\omega = 0$ means that whenever you fit these triangles into a simplex, they will sum to zero.
Imagine a world of four currencies: the US dollars, the Euro, and the Yuan, and bit coin.
Also imagine three currency traders: this guy (Pollock), this guy (Dali), this guy (Ai Wei Wei), and this guy (douchy kid).
Each person might consider traversing a loop in this diagram so as to return to their home currency.

[picture of tetra hedron with oriented sides, put an eye on one of them]

If the douchy kid issues the contracts on the edge of the blue face, then somebody else had to agree to the other side of each of those contracts. In this case, three people did, and in aggregate those three people have lost money to the douchy kid, and  traditional currency has transferred value to bitcoin.
Therefore, the statement $d \omega = 0$ here is just the manifestation of investment as a zero-sum game.
The conspiracy deepens.

## Non-zero sum?
What about when the economy is not zero sum.  This is when people are being productive (or destructive).
Then two

## Don't be so certain.
In fact, I should be more random.  Prices are not fixed, and most quantitative theories view them as random variables.  I just complete a three part post where probability theory was given a category, and the morphisms were posteriors.  Can that machinery be imported here?... Sort of.  Baye's theorem actually manifests as $d\alpha = 0$.  Thus, we end up in a no-arbitrage economy if we force our posteriors to follow Baye's theorem (which we should if we want to be self-consistent). Making money off this entails watching price fluctuations, and noting discrepencies between the contracts issued and the contracts you'd expect issued from your posteriors.  My guess is that this is roughly what electronic trading at medium length time-scales involves.

[^poincare lemma] Cite something
