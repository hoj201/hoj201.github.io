---
layout: post
title: Racism, Justice, and Bayesian Networks
tags: math, society
comments: true
---

## Bail
Interesting stat $$\Pr(case dsmissed | can pay bail) = 0.9$$.  However,
$$\Pr( case dismissed | can not pay bail) = 0.10$$, in fact, you are a lot more likely to enter a guilty plea
during this time, just so you can get out of the system quicker and avoid a harsher sentence.




Explain the iic HERE

A bayesian network of a racist looks like This
time to react
Race of person -> I should shoot this person
 ->person appears threatening

The world is simple here.  If you see a black guy, then you shoot him half the time.
Hey may or may not appear threatening, don't know don't care. So the next time you see this guy, put your hand on his shoulder, and tell him "It's okay. I understand you".
Then take out your pad of paper and draw this diagram.
I'm sure he'll be giddy.


## A bayesian network for a "non-racist"
Notice the quotes.  These people are, in my mind, technically still racist.
The only reason that we ever call them non-racist is becuase 99% of people, including myself, will fall under this category.  This is the Bayes net.

time to react -> person appears threatening -> I should shoot this person
race of person -^


## A bayesian network for a true non racist (these ppl don't exist)
A truly non-racist person is one where $$shoot \perp race$$ which make for a diagram more like this.

time to react -> person appears threatening -> I should shoot this person

race of person (island)

The race of the person is just in some island with no interaction with other factors.


## What is observed in the field
Most people are not "racist" in the sense that they can not possibly have the first diagram.
For most people it might be the case that $$\Pr(I should shoot | black ) \approx \Pr( I should shoot | white)$$.
However, the story is more nuanced in the "non-racist" case since we must integrate over time.
$$\Pr(shoot | black) =  \sum_{t} \Pr(shoot , t | black) = \sum_{t} \Pr(shoot | t , black) \Pr(t)$$
and it might be the case that the marginals are non-racist, but $\Pr(shoot, 0.001 | black) > \Pr(shoot, 0.001 | white)$
which is to say simply, the unconciousness comes into play.

When we think of ourselves, we usually think of our conscious selves.  Not the selves who poor beer on our dates after too many drinks.  Or the idiot who ate the marijuana cookie and freaked out about his heart rate before calling 911, wasting thousands of dollars, and precious bed space at an over crowded hospital.  That guys was not me.  That never happened.  Whatever Jake told you is a total lie (... Jake...).

I think this is why the conversation seems so heated.
The inequality $$\Pr(shoot | black, t << 1 ) > \Pr(shoot | white, t << 1)$$ is directly observable in the field.
However, calling the cops or the shooter racist immediately provokes a back-lash because the accused has a disconnect between what his unconsciousness Bayes-net and his conscious one, and the consciouss Bayesian net is more of an average over all scenarios.
