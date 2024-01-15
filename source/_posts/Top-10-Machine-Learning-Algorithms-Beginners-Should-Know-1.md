---
title: Top 10 Machine Learning Algorithms Beginners Should Know-1
categories:
  - machine learning
tags:
  - machine learning
cover: >-
  https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042107189.png
abbrlink: 362
date: 2023-10-04 21:04:31
---

```
origins：https://builtin.com/data-science/tour-top-10-algorithms-machine-learning-newbies
```

A machine learning algorithm is described as learning an objective function (f) that best maps an input variable (X) to an output variable (Y): Y = f(X)

The most common type of machine learning is learning the mapping Y = f(X) to predict Y for a new X. This is called predictive modeling or predictive analytics, and the goal is to make the most accurate predictions.

![Snipaste_2023-10-04_21-06-35](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042107189.png)

### Linear regression

Linear regression is one of the easiest algorithms to understand in statistics and machine algorithms.

Linear regression is represented as an equation that **describes a straight line that best fits the relationship between an input variable (x) and an output variable (y) by finding specific weights for the input variables called coefficients (B). **

![Snipaste_2023-10-04_21-10-41](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042112294.png)

*For example: y = B0 + B1 \* x*
 We will predict y given the input x. ** The goal of the linear regression learning algorithm is to find the values of the coefficients B0 and B1. **

Different techniques can be used to learn linear regression models from data, such as linear algebra solutions for ordinary least squares and gradient descent optimization.

## Logistic regression

Logistic regression is another technique borrowed by machine learning from the field of statistics. It is the method of choice for binary classification problems (problems with two class values).

Logistic regression is similar to linear regression in that the goal is to find coefficient values that weight each input variable. Unlike linear regression, the predictions of the output are transformed using a nonlinear function called a logistic function.

The logistic function looks like a big S and will convert any value to a range of 0 to 1. This is useful because we can apply rules to the output of the logistic function to capture values to 0 and 1 (e.g., output 1 if less than 0.5) and predict a class value.

![Snipaste_2023-10-04_21-14-51](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310042115487.png)

Due to the way the model learns, the predictions made by logistic regression can also be used as the probability that a given data instance belongs to class 0 or 1. This is a useful prediction for problems that require more reason to be given.

As with linear regression, logistic regression works better when you remove attributes that are not related to the output variable and attributes that are very similar (related) to each other. This is a fast learning model and works for binary classification problems.

