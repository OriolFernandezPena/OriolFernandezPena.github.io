---
layout: page
title: higher dimension knn
permalink: /higher_dim_knn/
show_in_menu: true
weight: 2
---

Hello
Check the full project and the code [here](https://github.com/OriolFernandezPena/HigherDimKNN)

Implementing algorithms from scratch is one of the best ways to understand what's going on when we use them. Just plug in the scikit-learn implementation shouldn't be enough.

### Theory

When performing Time Series Forecasting, sometimes the data we want to forecast needs to be of higher dimension than usual.

For example, when forecasting the price of electricity, it can be useful to predict the hourly price of a whole day instead of forecasting each hourly price recursively.

The `scikit-learn` implementation only lets us predict `float` numbers, this implementation will let us predict arrays.

The algorithm is simple.

- Fit is saving the training data and providing a value for `n`.
- Predict is finding the closest `n` points on the training data (with respect to the chosen distance) and returning an average (or weighted average) of the corresponding training dependent variables.



### Example: hourly stock GOOG value

Firstly we need to get the stock price every hour. We use `yfinance` library to get the last 2 years with hourly data for `GOOG`.

<img src="/images/higher_dim_knn/GOOG_close.jpg" alt="From scratch ROC Curve" width="500"/>

Then we define our training dataset as three consecutive days, and the forth will be our dependent variable.

<img src="/images/higher_dim_knn/training_example.jpg" alt="From scratch ROC Curve" width="500"/>

We split randomly the data, using 30% for test and the rest for training. Training is straightforward, as we don't really need to find any parameter, we just need to save the training data.

Let's see how predicting works:

Take a point from the test dataset and get the 2 closest neighbors (from the training dataset).

<img src="/images/higher_dim_knn/predicting_step1.jpg" alt="From scratch ROC Curve" width="500"/>

We look for the dependent variables of the nearest neighbours.

<img src="/images/higher_dim_knn/predicting_step2.jpg" alt="From scratch ROC Curve" width="500"/>

And make the weighted average to predict:

<img src="/images/higher_dim_knn/predicting_step3.jpg" alt="From scratch ROC Curve" width="500"/>

#### Notes

This is just an example to illustrate how the KNN algorithm can be adapted to higher dimensions, but does not compare the performance to other algorithms. 
