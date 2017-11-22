---
layout: default
title: Difficulties with the wealth distribution
---

This is a plot of the wealth distribution of the US.

![plot](url)


## Is this Pareto?
It is *not* [Pareto](url).  A Pareto distribution looks like a straight line, when shown in a log-log plot.  This is the log-log plot for the US wealth distribution.

![plot](path)

There is much more inequality here, than a MLE derived Pareto distribution could produce.

## Is this bad?

The total wealth is roughly x.  Evenly distributing this wealth would be a joke, but just for shits and giggles, if this were divided evenly, we'd each have y.  The current (uneven) state of things leaves z people literally starving.  So, yeah, probably bad.

## Experiment 1: Polya's urn
Let's initially distribute all capital evenly.
At each time-step each dollar of capital has the potential to become two (through investment in things that actually add to the economy).  With 100 people, simulated 100 times for 10,000 time-steps I get the following curves:

![plot of curves](url)

F! This does not look all that different in shape.

## Experiment 2: Copy other counties

... List of plots for other countries


## Experiment 3: Give up and flip a coin.
Since this is all in our heads, let's try a terrible idea.  Given each person a random share of the wealth.
Doing this 100 times, I get the following curves

F!  Looks exactly the same.


## Epilogue: What just happened?
Okay, here's the math.  For **Idea 1 (Polya's Urn)**, with people numbered $$1,\dots,p$$.
let $$\Pr(n_1,\dots, n_p)$$ denote the probability of wealth being distributed with $$n_1$$
dollars going to the first person, $$n_2$$ dollars to the second, and so on, at any time in history[^1].
We know that at $$t=0$$ the distribution is one-dollar a person, so
$$
  \Pr( 1, \dots, 1 ) = 1
$$
At time $$t > 0$$, the model is defined by the Markov process
$$
  \Pr(n_1, \dots, n_p ) = \sum_{k=1}^{p} \frac{n_k-1}{t+p}\Pr( n_1, \dots, n_{k-1}, n_k -1 , n_{k+1}, \dots, n_p).
$$

> Proposition:  $$\Pr(n_1,\dots,n_p)$$ is purely a function of the sum, $$N = \sum_{k=1}^{p}{n_k}$$.

> *proof*: We can prove it by induction. The hypothesis trivially holds at time $$t=1$$ because every
person has an equal change of getting a dollar.
That is to say $$\Pr(2,1,\dots,1) = \Pr(1,2,1,\dots,1) = \cdots = \Pr(1,\dots, 1,2)$$.
> At time $$t>1$$ we can use the induction hypothesis, and the above equation to find
> $$
  \Pr(n_1, \dots, n_p ) = \sum_{k=1}^{p} \frac{n_k-1}{t+p}\Pr( n_1, \dots, n_{k-1}, n_k -1 , n_{k+1}, \dots, n_p) \\
    &= blah.
$$


### Footnotes
[^1] Actually, a given wealth distribution, $$(n_1, \dots, n_p)$$, can only occur once, if at all, and it would be at time $$t = \left(\sum_{k=1}^p n_k \right) - p$$.
