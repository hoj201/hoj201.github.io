---
layout: post
title: Finance for mathematicians part II: Exterior calculus
tags: math, economics
---

This post is a sequel to [link to previous post here](;il)
This time we use discrete exterior calculus to understand finance. (links to Topological data analysis, Topological combinatorics, discrete morse theory, discrete differential geometry).  A pre-requisite to understanding this post is knowledge of [differential forms](https://en.wikipedia.org/wiki/Differential_form).

## backstory
Three hundred years ago, Thomas Newcomen invented an early version of the steam engine using the Rankine cycle. This notion of exploiting something while returning to where you started to exploit again was generalized by Carnot ![carnot](https://en.wikipedia.org/wiki/File:Sadi_Carnot.jpeg)
who jotted down his ideas for exploiting the relationship between pressure, volume, temperature, and entropy to literally move mountains.
  0) Light a furnace
  1) trade pressure for volume
  2) Extract work during a cooling phase
  3) Trade volume for pressure (at constant temperature)
  4) Heat things up again from your furnace
  5) go to step (1)

Then steam powered locomotives, sewing machines, children working in factories, machine guns, the internal combustion engine, World War I, assembly lines, World War II, Bikini Atoll, Hiroshima, USSR, the transistor, soda fountains, television, betamax, the Apple II, and then I was sitting in a class on biomechanics and the teacher (Michael Dickenson, drew this diagram on the white-board
[diagram](link)

The diagram explains the extraction of work from a muscle.
This could not be a coincidence, *it was a conspiracy.*

## They control everything and they can be anywhere
The airlines are also involved. This diagram explains how lift is extracted from an aerofoil
[diagram2](lift)
At this point it was no surprise that my advisors at Caltech, Mathieu Desbrun and Jerry Marsden were in on it too. The evidence of this can be seen in their (seemingly innocuous) work on computer graphics. That's just a cover, this goes deep. They are all in on it. The industrialists, the Russian, and even the suits on wall street.

Years later, I jotted down this diagram to understand commodities trading.

[commodities trading diagram]

if you take the bottom route of the diagram you've made a profit (and some poor shmuck is now in debt).  Diagramatically, capturing arbitrage involves traversing this triangle ![arbitrage triangle](link to picture) The ubiquity of this phenomena is eerie until you go down the rabbit hole and find the common cuprit.

## The puppet master
It's unclear who to target, but [Elie Cartan](link)
![Elie Cartan picture](link) certainly had the final word.
All these phenomena involve the calculation of the area on the interior of a bounded region to a line integral over a boundary, which can be seen as a special case of the Stokes theorem.

### Stokes theorem and the exterior derivative
Recall, given any differential form $\omega$, the integral of $\omega$ over the boundary of some region $\partial$\Omega$ is given by
$$
  \int_{\partial \Omega} \omega = \int_\Omega d\omega.
$$
In fact this theorem can be used as an alternative definition of the exterior derivative.
That is, we can define $d \omega$ as the unique ${k+1}$-form, such that Stokes theorem hold for arbitrary $k$-submanifolds with boundary.  Such a definition would be consistent with defining $k$-forms as

> **Definition** A $k$-form, $\alpha$, is a map from $k$-submanifolds of $M$ to the reals, such that $\alpha(N_1 \uplus N_2) = \alpha(N_1) + \alpha(N_2)$, where $\uplus$ denotes disjoint union.[^analysis]

[^analysis]: What's missing in this definition is analysis. I'm not exactly sure how best to address this. My gut tells me that this can be addressed by asking Peter Michor or one of his students.  It's somewhere in [this book](http://www.mat.univie.ac.at/~michor/apbookh-ams.pdf) I'm sure.  There is probably some space of $C^s$ embeddings, and we can say that the $k$-form is $C^s$ if it is bounded on this hypothetical space.

Typically, people denote $\alpha(N)$ by $\int_N \alpha$, and I will do that here as well.[^forms]

[^forms]:This is an alternative to the definition in most textbooks where we:
 1) describe dual-vectors
 2) tensors on vector spaces
 3) linear k-forms as anti-symmetrized tensors
 4) bundle it all on $TM$
 5) define $k$-forms as sections.
 6) attempt to define the integral of a $k$-form
 7) give up and refer to an appendix on partitions of unity (and don't spend too much time on it, nobody reads appendices)

You're free to pick your poison, since these definitions are roughly equivalent[^not equivalent]

In any case, using our definition, we can define $d \alpha := \alpha \circ \partial$. In other words

> **Definition:** The *exterior derivative* is the pre-composition operation on $\Omega^k$ by the boundary operator.

Stoke's theorem is now a tautology.

It's also intuitively clear that the boundary of the boundary is an empty set.[^boundary squared]. Thus we see that $d^2 \alpha = d(d\alpha) = d\alpha \circ \partial = \alpha \circ \partial^2 = 0$.



### Poincare Lemma
Realizing that $d^2 \alpha = 0$ for all $\alpha$ raises the question, if $d\omega = 0$, then does there exist an $\alpha$ such that $\omega = d \alpha$?  The definitive and unambiguous answer is **sort of**.  At each point in the manifold there exists a neighborhood, $U$ and a differential form $\alpha$ over $U$ such that $\omega|_{U_} = d\alpha$.[^poincare lemma]

[^poincare lemma]: We generally can't paste all these neighborhoods together to form a global $\alpha$ over all of $M$. The reason for this is typically an entry point to algebraic topology.

## Discrete exterior calculus (DEC)
There is a discrete analog of this notion.  We can discretize a manifold as a simplicial complex like this

![simplicial complex](get pic from keenan crane)

Then discretized functions are maps from the vertices to the reals.  The discrete notion of a submanifold is a sub-complext

![picture of sub complex](get pic from Keenan Crane)

The definition of a *discrete* $k$-form (and a perhaps all of discrete exterior calculus) can be a obtained by using your favorite text editor (mine is VIM) and doing a find/replace to substitute the word "manifold" with "simplicial complex" and the word "sub manifold" with "sub complex".  We obtain

DEFINITION
 A discrete $k$-form, $\alpha$, is a map from $k$-subcomplexes of $K$ to the reals, such that $\alpha(N_1 \uplus N_2) = \alpha(N_1) + \alpha(N_2)$, where $\uplus$ denotes disjoint union.

Again, we will use the notation $\int_N \alpha$ to denote $\alpha(N)$. We denote the set of discrete $k$-forms on $K$ by $\Omega_d^k(K)$

### Discrete Stokes Theorem
Let $\partial K$ denote the boundary of a simplicial complex, $K$.  Then stokes theorem is just an alternative definition for the discrete exterior derivative.
For a given $\alpha \in \Omega^k(K)$, we say $d\alpha$ is the unique $k+1$-form such that
$$
  \int_{K} d\alpha = \int_{\partial K} \alpha
$$
for arbitrary sub-complexes $N$.

### Discrete Poincare Lemma
Just as in the smooth case, $\partial^2 = 0$ and therefore, we have that $d^2 \alpha = 0$.  We can again ask, if $d \omega = 0$ for some $\omega \in \Omega^k_d(K)$, then does there exists an $\alpha$ such that $d\alpha = \omega$?  Again, the answer is sort-of. At each vertex, $x$, there exists a sub-complex $U \subset K$ which contains $x$, and a form $\alpha$ on $K$ such that $\omega|_{U_} = d\alpha$.

## DEC for finance
We can represent the trade-network of the economy as a massive simplicial complex.  The vertices represent commodities, and the edges represent trades.

At any given moment, apples might be trade for oranges at a rate of 1:2.  Bitcoin might trade with respect to US dollars at a rate of 1:6,599.0.  There are a lot of trades, and the most natural way to represent them all is using a one-form, $\alpha$.

Recall, the no arbitrage principle says that if we execute a circular sequence of trades, $C$, then the total result is no gain or loss.  So $\int_C \alpha = 0$.
Since the trade network is fully connected, $C$ can be seen as the boundary of a subcomplex $N$, and we can use stokes theorem to write $\int_N d\alpha = \int_C \alpha = 0$. Now note that $N$ is arbitrary (or arbitrary enough), so that we conclude $d\alpha = 0$.  This gives us yet another description of the no-arbitrage principle

DEC no-arbitrage
  If all the contracts in the economy are represented by a discrete one form $\alpha$,
then the no-arbitrage principle says $d \alpha = 0$.

By a discrete analog of the poincare lemma this mean $\alpha = d f$ for some function $f$.
From what I can tell, $f$, is related to value.

### Value as a distribution
I think, $f$, is the $\log$ of value.
I don't believe that intrinsic value makes a lot of sense, because nobody every speaks about how valuable things are in terms of value utils.  They speak about value in terms of stable currencies, like US dollars, or big macs. Therefore, we really only define the relative value of things, so it makes sense to view value as a probability distribution over all the commodities in the economy.  Probability distributions need only be defined up to a normalization constant (link to rays article), and so the log of a probability distribution need only be defined up to a constant.
In fact, the $f$ such that $\alpha = df$, has this very property.
Thus my suspicion that $v = \log(f)$ (modulo an immaterial constant).

## The Homologic no-arbitrage principle.
Everything has a price.[^poincare lemma]  So the no-arbitrage principle now looks
almost self-evident.  It appears to just claim that everything has a price.

... What about weird shaped economies?

## Arbitrage economy
Once all the arbitrages are exploited you end up with an arbitrage free economy and all diagrams commute.
How about when there is arbitrage?  What can be said in such cases?
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
Then I'm not so sure where to go.  It feels like solving an un-determined problem.  However, this is a typical scenario. The economy was different before the transistor was invented.  Any ideas from readers would be greatly appreciated.

## Don't be so certain.
In fact, I should be more random.  Prices are not fixed, and most quantitative theories view them as random variables.  I just complete a three part post where probability theory was given a category, and the morphisms were posteriors.  Can that machinery be imported here?... Sort of.  Baye's theorem actually manifests as $d\alpha = 0$.  Thus, we end up in a no-arbitrage economy if we force our posteriors to follow Baye's theorem (which we should if we want to be self-consistent). Making money off this entails watching price fluctuations, and noting discrepencies between the contracts issued and the contracts you'd expect issued from your posteriors.  My guess is that this is roughly what electronic trading at medium length time-scales involves.

## THE END?
need to write an ending.

[^1boundary squared]:Rigorously proving $\partial^2 = \emptyset$ took me a bit of effort actually.  I proved it in a brute force way.  Let $\mathbb{H}^n$ denote the half space of dimension $n$.  Consider an arbitrary chart on you manifold with boundary $\{ \varphi_\alpha: M \to U_\alpha \cap \mathbb{H}^n \}$.  The boundary of $M = \cup_\alpha \varphi_\alpha^{-1}( U_\alpha \cap \partial \mathbb{H})$.  The boundary of $\mathbb{H}^n = \mathbb{R}^{n-1}$, and the open set $V_\alpha := U_\alpha \cap \partial \mathbb{H}^n$ are just open subsets of $\mathbb{R}^{n-1}$.  The maps $\left. \varphi_alpha \right|_{\varphi_\alpha^{-1}(V_\alpha)}$ form a chart for the boundary of $M$, and it is a chart for a manifold **without boundary**.  QED.

 [^not equivalent]: Actually these definitions are not equivalent.  The traditional definition is a special case of the more general definition given here, analogous to the relationship between measures on a manifold, and volume forms.
