---
layout: page
title: logistic regression from scratch
permalink: /log_reg_scratch/
show_in_menu: true
weight: 1
---

Check the full project [here]()

Implementing algorithms from scratch is one of the best ways to understand what's going on when we use them. Just plug in the scikit-learn implementation shouldn't be enough.

### Theory

We implemented a very simple version, without including regularizations or other parameters. The convergence method used was gradient descent, although stochastic gradient descent should be very easy to generalize.

The model is defined as

$$
p(x) = \sigma(\theta x + b)
$$

where

$$
\sigma(z) = \frac{1}{1 + \exp{(- z)}}
$$.

For each epoch, we refresh the coefficients by $\partial$

$$
\theta_j \leftarrow \theta_j - \eta \frac{\partial}{\partial \theta_j} C(\theta, b, X)
$$


$$
b \leftarrow b - \eta \frac{\partial}{\partial b} C(\theta, b, X)
$$

Where $C(\theta, b, .)$ is the usual cost function and $X$ is the training set.

### Tests

We run a test with the iris dataset and compare the results to the `scikit-learn` implementation.