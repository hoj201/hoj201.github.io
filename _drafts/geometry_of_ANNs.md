---
layout: post
title: A geometers take on Artificial Neural Networks
tags: [math,AI]
---

## Summary
Each layer of the network is a map from a polytope to another polytope (possibly of lower dimension). This can be visualized when the X's are in $R3$.  Say the Weight matrix is 2x3, so that the first map $y={\rm relu}(Wx+b)$ divides $R3$ into 4 quadrants.  In one region both $y_1$ and $y_2$ are non-zero.  In another only $y_1$ varies.
In another, only $y_2$ varies, and in the last region, both $y_1$ and $y_2$ do not vary.
The space being described is isomorphic to the positive quadrant of $R^2$.
There are two coordinates, and a boundary where each coordinate vanishes respectively.
Geometrically speaking, the first layer divides space into 4 parts, sends one part to the strictly positive quadrant of $R^2$, sends to other regions to the positive axis in $R^2$, and the sends the remainder of the space to the origin of $R^2$.

The final layer, then sends the positive quadrant to $\mathbb{R}^+$ in a similar manner.
Just write this up with pictures now.

## Sigmoid activation function
These were long thought dead, until LSTM revived them and then batch-normalization made them somewhat trainable.  Sigmoids are similar to Relu.  They send spaces to compact strips.

## Convolutional neural networks and max-pooling
Same idea, just he weight matrices have been constrained, and relu is replaced with max-pooling.
Max-pooling sends regions of space to orbifolds rather than polytopes.
The intuition behind this is that many times, you only care about the strength of a feature in a given region.
So you take the max over that region.  This creates a discrete symmetry (i.e. swapping pixels), badda boom, badda bing, you got yourself an orbifold.
