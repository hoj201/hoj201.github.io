---
title: finite state POMDPs are infinite state MDPs
layout: post
---

## Overview of MDPs
A Markov decision process is a tuple $$(S, A, P_a, R_a)$$ where
  - $$S$$ is a set of states (typically finite).
  - $$A$$ is a set of actions
  - $$P_a(s,s') = \Pr(s_{t+1} = s' \mid a_t = a , s_t = s)$$ encodes the transition probabilities.
  - $$R_a(s,s') \in \mathbb{R}$$ is the reward from transitioning from $$s$$ to $$s'$$ via $$a$$.

We'd like to maximize the expected value of the discounted total reward
$$
  \sum_{t=0} \gamma^t R_{a_t}(s_t, s_{t+1})
$$
for a discount rate $$\gamma \in (0,1)$$.

Due to the Markov property we know there must exist a stochastic map (i.e. a posterior distribution) $$\pi(a \mid s)$$ that chooses the optimal action for each state.  Given a policy $$\pi$$ we can define the quality function

## Overview of POMDPs


## POMDPs as MDPs
Given a POMDP over a state space $$S$$, there is an associated MDP over $$\mathcal{S} = \Omega(S)$$ and the actions are elements of $$\mathcal{A} = \Omega(A)$$. The evolution operator is a stochastic map $$\mathcal{T}: \Omega(S \times A) \to \Omega(S)$$ given by lifting $$T:S \times A \to S$$ viewed as a deterministic map.


## The category of probability theory

## MDPs for cat people
Let's consider the category of probability distributions, where the arrows are posterior distributions. In this framework an MDP is a triple $$(\tau, T, r)$$ where $$\tau: \mathcal{A} \to S$$ is a measureable surjection, and $$T:\mathcal{A} \to S$$ and $$r:\mathcal{A} \to \mathbb{R}$$ are stochastic maps. A policy $$\pi: S \to \mathcal{A}$$ is defined as a $$\tau$$-section. Given a policy, there is an arrow $$\Phi: \mathcal{A} \to \mathcal{A}$$ given by the composition $$\Phi = \pi \circ T$$. We can define the quality function $$Q^\pi: \mathcal{A} \to \mathbb{R}$$ as a measureable map defined via the recursion


$$
\begin{align}
  Q^{\pi}(s,a) = \mathcal{R}(s,a) + \gamma \mathbb{E}( Q^\pi \circ \Phi | s,a )
\end{align}
$$

Since we know that the solution is deterministic, we can do policy iteration in the normal way, setting $$\pi_{n+1}(s) = \arg \max_{s = \tau(a)} Q^{\pi_n}(s,a)$$.

## POMDPs for cat people
A POMDP is a tuple $$(\tau, T, r, Y)$$ where $$Y:S \to \mathcal{O}$$ (generally stochastic).  Given a sequence of observations and actions $$(y_0, a_0), (y_1,a_1), \dots$$ and an initial distribution $$\sigma_0 \in {\rm Prob}(S)$$ we can derive a sequence of distributions $$\sigma_1, \sigma_2,\dots$$ using the forward algorithm. Therefore, at any given time we only can expect to have a distribution $$\sigma \in {\rm Prob}(S)$$, and so we should only make decisions based upon a probabilistic description of the state. Thus a policy should be something that eats $${\rm Prob}(S)$$.  In particular, we define a policy to be a $$\tau_\ast$$-section, where $$\tau_{\ast}: {\rm Prob}(\mathcal{A}) \to {\rm Prob}(S)$$ is the push-forward map associated to $$\tau$$. Given a policy $$\pi: {\rm Prob}(S) \to {\rm Prob}(\mathcal{A})$$ the posterior $$\Phi = \pi \circ T$$ serves as an evolution operator on $$\mathcal{A}$$. The quality function $$Q^{\pi} : {\rm Prob}(\mathcal{A}) \to \mathbb{R}$$ is defined by

$$
\begin{align}
  Q^{\pi}(\rho) := \sum_{k=0}^{\infty} \mathcal{R}(\Phi^k(\rho)).
\end{align}
$$

We see that $$Q^\pi$$ may also be defined by the recursion

$$
\begin{align}
  Q^{\pi}(\rho) = \mathcal{R}(\rho ) + \gamma Q^{\pi} (\Phi(\rho)).
\end{align}
$$

There is also an operator $$\Psi: {\rm Prob}(S) \to {\rm Prob}(S)$$ given by $$\Psi = \tau_{\ast} \Phi \circ \pi$$. We can then consider the value function $$V^\pi(\sigma) = Q^\pi(\pi(\sigma))$$
which must satisfy a similar recursion
$$
  V^{\pi}(\sigma) = \mathcal{R}(\pi(\sigma)) + \gamma V^\pi(\Psi(\sigma)).
$$

This recursive identity theoretically allows us to do value-iteration to solve for $$V^\pi$$ and then define $$Q^{\pi}$$ as $$Q^{\pi}(\rho) = \mathcal{R}(\rho) + \gamma V^{\pi}( \Psi(\tau_{\ast}(\rho)))$$.

Similarly, we can do policy iteration via defining

$$
\begin{align}
  \pi_{n+1}( \sigma ) = \arg \max_{ \sigma = \tau_*(\rho)} Q^{\pi_n}(\rho)
\end{align}
$$

Once a stochastic policy is found such that
$$
\begin{align}
  \pi( \sigma ) = \arg \max_{ \sigma = \tau_*(\rho)} Q^{\pi}(\rho)
\end{align}
$$
we will know that a sequence of rewards produced from $$\pi$$ will optimize the quantity $$\mathbb{E}\left(\sum_{k} \gamma^k r_k\right)$$.
