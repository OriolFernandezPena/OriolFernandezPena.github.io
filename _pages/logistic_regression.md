---
layout: page
title: logistic regression from scratch
permalink: /log_reg_scratch/
show_in_menu: true
weight: 1
---

Check the full project and the code [here](https://github.com/OriolFernandezPena/LogisticRegressionFromScratch)

Implementing algorithms from scratch is one of the best ways to understand what's going on when we use them. Just plug in the scikit-learn implementation shouldn't be enough.

### Theory

We implemented a very simple version, without including regularizations or other parameters. The convergence method used was gradient descent, although stochastic gradient descent should be very easy to generalize.

The model is defined as

$$
p(x) = \sigma(\theta x + b)
$$

where

$$
\sigma(z) = \frac{1}{1 + \exp{(- z)}}.
$$

For each epoch, we refresh the coefficients by $\partial$

$$
\theta_j \leftarrow \theta_j - \eta \frac{\partial}{\partial \theta_j} C(\theta, b, X),
$$


$$
b \leftarrow b - \eta \frac{\partial}{\partial b} C(\theta, b, X),
$$

where $C(\theta, b, .)$ is the usual cost function, $\eta$ is the learning rate and $X$ is the training set.

### Tests

We run a test with the iris dataset and compare the results to the `scikit-learn` implementation. Measuring with the AUC score we get very similar results.

|Classifier    | AUC Score |
| ------------ | --------- |
| From scratch | 0.992600  |
| Scikit Learn | 0.997600  |

Let's look at both ROC curves:

<img src="/images/logistic/CustomLogReg_ROC.jpg" alt="From scratch ROC Curve" width="500"/>
<img src="/images/logistic/SKLearnLogReg_ROC.jpg" alt="Scikit Learn ROC Curve" width="500"/>


#### Notes

We didn't use a test or validation dataset, contrary to standard, because we weren't trying to build a robust model. In this case, the robustness of the actual model is of no importance, we wanted to check that the model to which we converge is similar to what we would've had if we had used a standard scikit-learn logistic regression.