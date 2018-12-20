---
layout: post
title: Derivation of the forward-algorithm for Hidden Markov Models
---

Let's say you have a [hidden Markov model](https://en.wikipedia.org/wiki/Hidden_Markov_model) (HMM) with transition probabilities $$M(x_t,x_{t-1}) = \Pr(X_t = x_t | X_{t-1} = x_{t-1})$$ and observation probabilities $$C(y,x) = \Pr(Y_t = y | X_t = x)$$. We'd like to know $$\Pr(X_t=x_t | Y_0 = y_0, \dots, Y_t = y_t)$$.  So here we go
\begin{align}
  \Pr(X_t=x_t | Y_0 = y_0 , \dots, Y_t = y_t) \propto \Pr(X_t = x_t, Y_t = y_t, \dots, Y_0 = y_0)
\end{align}
where "$$\propto$$" means "modulo a function of $$y_0, \dots, y_t$$".  To reduce clutter let $$Y_{:t} := (Y_0,\dots,Y_t)$$. Similarly, $$y_{:t} = (y_0, \dots, y_t)$$. Finally define $$f_t(x_t,y_{:t}) := \Pr(X_t=x_t, Y_{:t}=y_{:t})$$. Then the above equation is
$$
\begin{align}
\Pr(X_t=x_t | Y_{:t} = y_{:t}) = \frac{1}{Z_t(y_{:t})} f_t(x_t, y_{:t}) \\
\end{align}
$$
where $$Z_t(y_{:t}) := \sum_{x_t} f_t(x_t, y_{:t})$$.
So we've reduce the problem to creating an algorithm for deriving $$f_t(x_t, y_{:t})$$ for a fixed sequence, $$y_0, y_1, \dots$$.

## Recursively solving for $$f_t$$.
Computing $$f_t$$ naively is not advisable.  However, we can compute $$f_t$$ recursively as a function of the transition and measurement probabilities and $$f_{t-1}$$.

$$
\begin{align}
  f_t(x_t, y_{:t}) &= \sum_{x_{t-1}} \Pr(X_t = x_t, X_{t-1}=x_{t-1}, Y_{:t} = y_{:t}) \\
  &= \sum_{x_{t-1}} \Pr(Y_t=y_t| X_{t-1:t}=x_{t-1:t}, Y_{:t-1}=y_{:t-1}) \Pr(X_{t-1:t}=x_{t-1:t}, Y_{:t-1}=y_{:t-1}) \\
  &= \sum_{x_{t-1}} \Pr(Y_t=y_t| X_t=x_t) \Pr(X_{t-1:t}=x_{t-1:t}, Y_{:t-1}=y_{:t-1}) \\
  &= \sum_{x_{t-1}} C(y_t,x_t) \Pr(X_{t}=x_{t}| X_{t-1} = x_{t-1}, Y_{:t-1}=y_{:t-1}) \Pr(X_{t-1} = x_{t-1}, Y_{:t-1}=y_{:t-1}) \\
  &= \sum_{x_{t-1}} C(y_t,x_t) \Pr(X_{t}=x_{t}| X_{t-1} = x_{t-1}) \Pr(X_{t-1} = x_{t-1}, Y_{:t-1}=y_{:t-1}) \\
  &= \sum_{x_{t-1}} C(y_t,x_t) M(x_{t}, x_{t-1}) \Pr(X_{t-1} = x_{t-1}, Y_{:t-1}=y_{:t-1}) \\
  &= \sum_{x_{t-1}} C(y_t,x_t) M(x_{t}, x_{t-1}) f_{t-1}(x_{t-1}, y_{:t-1})
\end{align}
$$

So in summary, our recursion formula is

$$
\begin{align}
 f_t(x_t, y_{:t-1}) = C(y_t,x_t) \sum_{x_{t-1}} M(x_{t}, x_{t-1}) f_{t-1}(x_{t-1}, y_{:t-1})
\end{align}
$$

If the state space is continuous, then we'd get

$$
\begin{align}
  f_t(x_t, y_{:t}) = C(y_t, x_t) \int M(x_t, x_{t-1}) f_{t-1}(x_{t-1}, y_{:t-1}) dx_{t-1}
\end{align}
$$

## Matrix Form
If the state space is finite, then we can identify the states with the integers $$1,\dots, N_s$$. Let $$\vec{f}_t := (f_t(1,y_{:t}), \dots, f_t(N_s)$$ and for each $$y$$ in the observation space (which can be any set) we define the diagonal matrix

$$
\begin{align}
  \Lambda(y) := {\rm diag}(C(y_t,1), \dots, C(y_t,N_s))
\end{align}
$$

and we can re-write our our recursive equation as

$$
\begin{align}
  \vec{f}_t = \Lambda(y_t) \cdot M \cdot \vec{f}_{t-1}
\end{align}
$$

and $$\Pr(X_t = i \mid y_{:t}) = \frac{1}{Z_t} \vec{f}_t[i]$$ where $$Z_t = \sum_{i} \vec{f}_t[i]$$.

## Algorithmic complexity
For a fixed sequence of observations, $$y_0, \dots, y_t$$, the computation of $$\Pr(X_t = i \mid y_{:t})$$ is $$\mathcal{O}(t)$$ in time and $$\mathcal{O}(1)$$ in space.  Updating after a new measurement arrives is $$\mathcal{O}(1)$$ in time and space.
