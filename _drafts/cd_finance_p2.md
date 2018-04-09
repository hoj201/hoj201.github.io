---
layout: post
title: Finance for mathematicians (part II)
tags: math, economics
---

This post is something of a sequel to [a post from two years ago]({{ site.baseurl }}{% post_url 2016-04-04-finance-explained-in-commutative-diagrams %}) where I used commutative diagrams to understand finance.
A few people wanted me to write a follow-up and I dragged my feet for a long time.
Then it randomly appeared on Reddit, and then my ego kicked in, and I always listen to my ego now days because I'm tired of being controlled by the Buddha!

No commutative diagrams in this one, but the level is a bit elevated mathematically.
This time I'll use discrete exterior calculus.  A pre-requisite to understanding this post is knowledge of [differential forms](https://en.wikipedia.org/wiki/Differential_form).

## backstory

<figure>
  <img src="https://upload.wikimedia.org/wikipedia/commons/8/80/Sadi_Carnot.jpeg" alt="carnot image"/>
  <figcaption>A portrait of Carnot circa 1813</figcaption>
</figure>

Three hundred years ago, Thomas Newcomen invented an early version of the steam engine using the Rankine cycle. This notion of exploiting something while returning to where you started to exploit again was generalized by Carnot
who jotted down his ideas for exploiting the relationship between pressure, volume, temperature, and entropy to literally move mountains.  The carnot cycle is representing in psuedo-code as:

```
Light a furnace
while True:
  trade pressure for volume
  Extract work during a cooling phase
  Trade volume for pressure (at constant temperature)
  Heat things up again from your furnace
```

This loop is diagramed on wikipedia like this

![carnot cycle picture](https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Carnot_cycle_p-V_diagram.svg/600px-Carnot_cycle_p-V_diagram.svg.png)

Then steam powered locomotives, sewing machines, children working in factories, machine guns, the internal combustion engine, World War I, assembly lines, World War II, Bikini Atoll, Hiroshima, USSR, the transistor, soda fountains, television, betamax, the Apple II, and then I was sitting in a class on biomechanics and the teacher ([Michael Dickenson](https://dickinsonlab.caltech.edu/)), drew this diagram like this on the white-board

![diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/Work_Loop.svg/330px-Work_Loop.svg.png)

The diagram explains the extraction of work from a muscle.
This could not be a coincidence, *it was a conspiracy.*

## They control everything and they can be anywhere
The airlines are also involved. Lift in irrotational flows is derived by integrating over a loop[^Kutta].
At this point it was no surprise that my advisors at Caltech, Mathieu Desbrun and Jerry Marsden were in on it too. The evidence of this can be seen in their (seemingly innocuous) work on computer graphics. That's just a cover, this goes deep.

[^Kutta]: See the [Kutta-Joukowski theorem](https://en.wikipedia.org/wiki/Kutta%E2%80%93Joukowski_theorem).

They are all in on it. The industrialists, the Russian, and even the suits on wall street.
Years later, I jotted down this commutative diagram to understand stock trading.

![middle](https://hoj201.files.wordpress.com/2016/03/middle.png)

The top arrow represents the interest rate on a loan.  The p's refer to trading dollars for shares of stock, and so $$p^{-1}$$ refers to the process of selling a share of stock.
If there is an arbitrage opportunity, then this diagram does not commute.
You can take out a loan, buy a stock, wait, and then sell the stock.  This the map $$p_{\operatorname{future}^{-1}} \circ \operatorname{wait} \circ p$$.
It's an arbitrage in your favor if the return on investment is greater than the interest rate of the loan, $$r$$.

Diagramatically, capturing arbitrage involves traversing this triangle

 ![arbitrage triangle]({{"assets/finance/arbitrage.png" | absolute_url }})

 The ubiquity of this phenomena is eerie until you go down the rabbit hole and find the common culprit.

## The puppet master
![Elie Cartan picture](https://upload.wikimedia.org/wikipedia/en/e/e8/Elie_Cartan.jpg)

It's unclear who to target, but [Elie Cartan](https://en.wikipedia.org/wiki/%C3%89lie_Cartan) certainly had the final word.
All these phenomena involve the calculation of the area on the interior of a bounded region to a line integral over a boundary, which can be seen as a special case of the Stokes theorem. Elie Cartan is credited with inventing exterior calculus, and discovering the modern characterization of Stokes theorem.

### Stokes theorem and the exterior derivative
Recall, given any differential form $$\omega$$, the integral of $$\omega$$ over the boundary of some region $$\partial \Omega$$ is given by
\begin{align}
  \int_{\partial \Omega} \omega = \int_\Omega d\omega.
\end{align}
In fact this theorem can be used as an alternative definition of the exterior derivative.
That is, we can define $$d \omega$$ as the unique $${k+1}$$-form, such that Stokes theorem hold for arbitrary $$k$$-submanifolds with boundary.  Such a definition would be consistent with defining $$k$$-forms as

> **Alternative Definition of $$k$$-form:** A $$k$$-form, $$\alpha$$, is a map from oriented[^oriented] $$k$$-submanifolds of $$M$$ to the reals, such that $$\alpha(N_1 \uplus N_2) = \alpha(N_1) + \alpha(N_2)$$, where $$\uplus$$ denotes disjoint union. The vector space of $$k$$-forms on $$M$$ is denoted by $$\Omega^k(M)$$.[^analysis]

[^oriented]: Sometimes, one learns that a manifold is oriented if there exists a non-vanishing volume form on it (this is how I learned of it).  However, you can define orientation prior to defining differential forms.  A manifold is oriented if there exists an atlas where the transition maps are all orientation preserving (i.e the determinant of the Jacobian is positive).

[^analysis]: What's missing in this definition is analysis. I'm not exactly sure how best to address this. My gut tells me that Peter Michor and his students know best.  It's somewhere in [this book](http://www.mat.univie.ac.at/~michor/apbookh-ams.pdf), either explicitly or implicitly.  Perhaps it's as simple as looking at the space of smooth embeddings, $$\operatorname{Emb}(S,M)$$ as an infinite.  We'd say $$\alpha \in \Omega^k(M)$$ is $$C^s$$ if $$\alpha \circ f$$ is a $$C^s$$ endomorphism on $$\mathbb{R}$$ for any $$f: \mathbb{R} \to \operatorname{Emb}(S,M)$$ of class $$C^s$$ and any $$k$$-manifold $$S$$.

Typically, people denote $$\alpha(N)$$ by $$\int_N \alpha$$, and I will do that here.
This is an alternative to the definition in most textbooks where we:
 1. describe dual-vectors
 2. tensors on vector spaces
 3. linear k-forms as anti-symmetrized tensors
 4. bundle it all on $$TM$$
 5. define $$k$$-forms as sections.
 6. attempt to define the integral of a $$k$$-form
 7. fail
8.  Refer to an appendix on partitions of unity (and pray nobody reads it)

You're free to pick your poison, since these definitions are roughly equivalent.[^not_equal]

[^not_equal]: Actually these definitions are not equivalent.  The traditional definition is a special case of the more general definition given here, analogous to the relationship between measures on a manifold, and volume forms. However, when I learned differential forms, I found it really difficult to discern the motivation (which was integration, but that's not until Chapter 10 or somthing crazy).  Why not just introduce integration off the bat?

In any case, using our definition, we can define $$d \alpha := \alpha \circ \partial$$. In other words

> **Definition:** The *exterior derivative* is the pre-composition operation on $$\Omega^k$$ by the boundary operator.

Stoke's theorem is now a tautology.

It's also intuitively clear that the boundary of the boundary is an empty set.[^boundary].Thus we see that $$d^2 \alpha = d(d\alpha) = d\alpha \circ \partial = \alpha \circ \partial^2 = 0$$.

[^boundary]: Rigorously proving $$\partial^2 = \emptyset$$ took me a bit of effort actually.  I proved it in a brute force way.  Let $$\mathbb{H}^n$$ denote the half space of dimension $$n$$.  Consider an arbitrary chart on you manifold with boundary $$\{ \varphi_\alpha: M \to U_\alpha \cap \mathbb{H}^n \}$$.  Note that the sets $$\varphi_\alpha^{-1}( U_\alpha \cap \partial \mathbb{H})$$ form an open cover of $$\partial M$$, and $$\partial \mathbb{H}^n = \mathbb{R}^{n-1}$$.  Therefore $$V_\alpha := U_\alpha \cap \partial \mathbb{H}^n$$ is just an open subset of $$\mathbb{R}^{n-1}$$ for all $$\alpha$$ and the maps $$\varphi_\alpha$$ restricted to $$\varphi_\alpha^{-1}(V_\alpha)$$ form a chart for $$\partial M$$.  This chart is apparently a chart for a manifold *without boundary*.  QED.

### Poincare Lemma
Realizing that $$d^2 \alpha = 0$$ for all $$\alpha$$ raises the question, if $$d\omega = 0$$, then does there exist an $$\alpha$$ such that $$\omega = d \alpha$$?  The definitive and unambiguous answer is "sort of".  At each point in the manifold there exists a neighborhood, $$U$$ and a differential form $$\alpha$$ over $$U$$ such that $$\omega|_{U_{}} = d\alpha$$.[^poincareLemma]

[^poincareLemma]: We generally can't paste all these neighborhoods together to form a global $$\alpha$$ over all of $$M$$. The reason for this is typically an entry point to algebraic topology.

## Discrete exterior calculus (DEC)
There is a discrete analog of this notion.  We can discretize a manifold as a [simplicial complex](https://en.wikipedia.org/wiki/Simplicial_complex) like this

![simplicial complex]({{"assets/finance/simplicial_complex.png" | absolute_url}})

Then discretized functions are maps from the vertices to the reals.  The discrete notion of a submanifold is a sub-complex, which looks like the high-lighted red part in this picture.

![subcomplex]({{"assets/finance/subcomplex.png" | absolute_url}})

The definition of a *discrete* $$k$$-form (and a perhaps all of discrete exterior calculus) can be a obtained by using your favorite text editor (mine is VIM) and doing a find/replace to substitute the word "manifold" with "simplicial complex" and the word "sub manifold" with "sub complex".  By drawing arrows on edges we get oriented simplicies, and thus oriented simplicial complexes.  We then obtain

> **Definition of discrete differential forms:** A discrete $$k$$-form, $$\alpha$$, over $$K$$ is a map from oriented $$k$$-subcomplexes of $$K$$ to the reals, such that $$\alpha(N_1 \uplus N_2) = \alpha(N_1) + \alpha(N_2)$$, where $$\uplus$$ denotes disjoint union.

Again, we will use the notation $$\int_N \alpha$$ to denote $$\alpha(N)$$. We denote the set of discrete $$k$$-forms on $$K$$ by $$\Omega_d^k(K)$$

### Discrete Stokes Theorem
In the discrete case, the Stokes theorem is not really a theorem but a definition.
Let $$\partial K$$ denote the boundary of a simplicial complex, $$K$$.
For a given $$\alpha \in \Omega^k_d(K)$$, we say $$d\alpha$$ is the unique $$k+1$$-form such that
\begin{align}
  \int_{K} d\alpha = \int_{\partial K} \alpha
\end{align}
for arbitrary sub-complexes $$N$$.

### Discrete Poincare Lemma
Just as in the smooth case, $$\partial^2 = 0$$ and therefore, we have that $$d^2 \alpha = 0$$.  We can again ask, if $$d \omega = 0$$ for some $$\omega \in \Omega^k_d(K)$$, then does there exists an $$\alpha$$ such that $$d\alpha = \omega$$?  Again, the answer is sort-of. At each vertex, $$x$$, there exists a sub-complex $$U \subset K$$ which contains $$x$$, and a form $$\alpha$$ on $$K$$ such that $$\omega|_{U_{}} = d\alpha$$.[^discretePoincareLemma]

[^discretePoincareLemma]:[Mathieu Desbrun, Melvin Leok, Jerrold Marsden, "Discrete Poincare Lemma", Volume 53, Issues 2--4, (2205)](https://doi.org/10.1016/j.apnum.2004.09.035)

## DEC for finance
We can represent the trade-network of the economy as a massive simplicial complex.  The vertices represent commodities, and the edges represent trades.

At any given moment, apples might be trade for oranges at a rate of 1:2.  Bitcoin might trade with respect to US dollars at a rate of 1:6,599.0.  There are a lot of trades, and the most natural way to represent them all is using a one-form, $$\alpha$$.

Recall, the no arbitrage principle says that if we execute a circular sequence of trades, $$\gamma$$, then the total result is no gain or loss.  So $$\int_\gamma \alpha = 0$$.
Since the trade network is fully connected, $$\gamma$$ can be seen as the boundary of a disk-shaped subcomplex $$D$$, and we can use stokes theorem to write $$\int_D d\alpha = \int_\gamma \alpha = 0$$. Now note that $$D$$ is arbitrary (or arbitrary enough), so that we conclude $$d\alpha = 0$$.  This gives us yet another description of the no-arbitrage principle

> **The DEC no-arbitrage principle:**
  Let $$\alpha \in \Omega^1(K)$$ represent the contracts in an economy. In a no-arbitrage economy, $$d \alpha = 0$$.

By a discrete analog of the poincare lemma this mean $$\alpha = d V$$ for some function $$V$$.
What is this $$V$$?  Is it even worth knowing?

### $$V$$ is for Value!
![big mac](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Big_Mac_hamburger_-_Croatia.jpg/330px-Big_Mac_hamburger_-_Croatia.jpg)

Specifically, I think, $$V$$, is $$\log$$-value. If $$dV = \alpha$$, and $$\alpha(\bar{xy}) > 0$$, then intuitively, $$y$$ is more valuable than $$x$$, and we find $$V(y) > V(x)$$[^signErrors].
However, $$V$$ is only well defined up to a constant function!  $$\tilde{V} = V+c$$ also satisfies $$d\tilde{V} = \alpha$$.
This is because $$V$$ is really the logarithm of value, and value itself is not an absolute quantity.
I don't believe that intrinsic value makes a lot of sense, because there is no such thing as a "value util".  People speak about value in concrete units like big macs[^bigmac], or dollars (which are only valuable because you can exchange them for things like big macs). Because we really only define the relative value of things we should view value as a probability distribution over all the commodities.  [Probability distributions need only be defined up to a normalization constant]({{ site.baseurl }}{% post_url 2018-01-21-probability %}), and so the log of a probability distribution need only be specified up to a constant.
The function $$V$$ has this very property, and thus my suspicion that the value of a commodity is given by $$P = \exp(V)$$ (defined modulo an immaterial multiplier).  

[^bigmac]: See [the big mac index](https://en.wikipedia.org/wiki/Big_Mac_Index)
[^signErrors]:possible sign errors here, but the idea holds.

## Arbitrage economy
How about when there is arbitrage?  What can be said in such cases?
We'll firstly, if $$d \alpha \neq 0$$, then there is no $$f$$ such that $$df = \alpha$$.
In other words,
*there is no collectively agreed upon value for the commodities in an economy that has arbitrage opportunities.*

That's not quite the end.  We know that $$d(d\alpha) = 0$$, does this translate to anything familiar?
Well if you draw the picture, it's not so crazy.  $$\omega := d\alpha$$ is a two-form an is cartooned using oriented triangles.
That $$d\omega = 0$$ means that whenever you fit these triangles into a simplex, they will sum to zero.
Imagine a world of four currencies: the US dollars, the Euro, and the Yuan, and bit coin.
Also imagine three currency traders: this guy (Pollock), this guy (Dali), this guy (Ai Wei Wei), and this guy (douchy kid).
Each person might consider traversing a loop in this diagram so as to return to their home currency.

[picture of tetra hedron with oriented sides, put an eye on one of them]

If the douchy kid issues the contracts on the edge of the blue face, then somebody else had to agree to the other side of each of those contracts. In this case, three people did, and in aggregate those three people have lost money to the douchy kid, and  traditional currency has transferred value to bitcoin.
Therefore, the statement $$d \omega = 0$$ here is just the manifestation of investment as a zero-sum game.
The conspiracy deepens.

## Gripes and under-developed musings
I'm like this formalism, but there are major issues
 - Typically the economy is growing or shrinking.  It's not really zero-sum.
 - Typically there are multiple contracts floating around for some trades, and zero contracts floating around for others.

### Non-zero sum?
By construction, $$d^2 \alpha = 0$$.  However, this would suggest a zero-growth economy.  However, the economy is always growing or shrinking. No idea how to fix this. If you've got an idea, I'd love to hear it.  Jot it in the comments section, please!

### Weighted networks and electronic trading
 I think the links in the network should not be one-forms, but more like a distribution of one-forms. Prices are not fixed, and many quantitative theories of finance view them as random variables.  I just complete a three part post where probability theory was given a category, and the morphisms were posteriors.  Can that machinery be imported here?... Sort of... I think.  I jotted some stuff down and found that Bayes theorem actually manifests as $$d\alpha = 0$$.  Thus, we end up in a no-arbitrage economy if we force our posteriors to follow Bayes theorem (which we should if we want to be self-consistent). Making money off this entails watching price fluctuations, and noting discrepancies between the contracts issued and the contracts you'd expect issued from your posteriors.  My guess is that this is roughly what electronic trading at medium length time-scales involves.

### Monopoles, trade barriers, and the shape of the market
In this formalism I have been assuming the economy is fully connected.  Geometrically speaking, this means the economy is a an $$n$$-dimensional simplex for some large $$n$$.  This is the simplest possible shape we could expect.  However, trade barriers will remove some of the links in the network, and the resulting trade network might take on a more interesting shape, perhaps one with holes.  Once you have a hole, the poincare lemma is only local.  It is then possible to have an economy where $$d\alpha = 0$$, but where there exists a loop $$\gamma$$ that posses an arbitrage opportunity.  Getting rid of such an arbitrage might be impossible due to topological obstructions (the trade barriers).

An analogous question arose in the physics community back in 1931, when Dirac wrote a quantum theory of magnetic charge.  There is a geometric way of writing down Maxwell's equations using (modest generalizations of) differential forms and one of the equations takes the form $$d\alpha = 0$$.  Dirac found that if there exists a magnetic monopole in the universe, then the charge of all particles would become quantized.  Such a magnetic monopole would correspond to a hole of sorts, and the charge would manifest by integration of a differential form around this hold.  To date, magnetic monopoles have eluded us, but the theory is consistent with reality (charge is quantized). To the best of our knowledge, they are out there.

Finding an arbitrage is analogous (and mathematically identical) to finding a magnetic monopole somewhere in the universe.
Such a loop would make one person massively wealthy until the trade barriers are removed, and the market is able to clamp down on this exploit.  Nonetheless, I've never heard of such a tactic.
I don't imagine a *Ready Player One* type of global quest to search for such a thing.
However, virtually all transaction are of the form "`[SOMETHING]` in exchange for `[A CURRENCY]`", and typically the currency is US dollars.  You can't form a loop if you only do trades of this form.
So perhaps there are holes in the network, fortunes just sitting under our noses, but we are blinded by our trust in the dollar.

![dollar]({{"assets/finance/great_seal.jpg" | absolute_url }})



# Footnotes
