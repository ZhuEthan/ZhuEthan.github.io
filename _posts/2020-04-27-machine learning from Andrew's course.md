---
layout: post
title: Andrew Ng's Machine Learning on Coursera
tags: [ML]
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"
---

## Week1 & Week2:

* Gradient descent inference including cost function definition and derivative is on slices. 

* feature scaling and mean normalization is helping speed up gradient descent. 

\\[x_i = \frac{x_i-\mu_i}{max-min}\\]

* Normal Equation: Gradient descent gives one way of minimizing J. Let’s discuss a second way of doing so, this time performing the minimization explicitly and without resorting to an iterative algorithm. In the "Normal Equation" method, we will minimize J by explicitly taking its derivatives with respect to the θj ’s, and setting them to zero. This allows us to find the optimum theta without iteration. The normal equation formula is given below:

\\[\theta = (X^TX)^{-1}X^Ty\\]

Gradient descent has time complexity \\(O(kn^2)\\); Normal Equation is \\(O(n^3)\\), in which n is the number of features. In practice, when n exceeds 10,000 it might be a good time to go from a normal solution to an iterative process.

If \\(X^TX\\) is noninvertible, the common causes might be having :

* Redundant features, where two features are very closely related (i.e. they are linearly dependent)
* Too many features (e.g. m ≤ n). In this case, delete some features or use "regularization" (to be explained in a later lesson).

Solutions to the above problems include deleting a feature that is linearly dependent with another or deleting one or more features when there are too many features

* Gradient descent learning rate \\(\alpha\\)
  * If \\(alpha\\) is too small: slow convergence.
  * If \\(alpha\\) is too large: ￼may not decrease on every iteration and thus may not converge.


## Week 3

We cannot use the same cost function that we use for linear regression because the Logistic Function will cause the output to be wavy, causing many local optima. In other words, it will not be a convex function.

Instead, our cost function for logistic regression looks like:

\\(Cost(h_\theta, y) = -log(h_\theta(x)) if y = 1\\)
\\(Cost(h_\theta, y) = -log(1 - h_\theta(x)) if y = 0\\)

* Since this cost function leads to: 
  * \\(Cost(h_\theta, y) = 0\\) if \\(h_\theta(x) = y\\)
  * \\(Cost(h_\theta, y)\\) -> \\(\infty\\) if y = 0 and \\(h_\theta(x) -> 1\\)
  * \\(Cost(h_\theta, y)\\) -> \\(\infty\\) if y = 1 and \\(h_\theta(x) -> 0\\)
* This cost function is convex. 

Put together: 

\\(Cost(h_\theta, y) = -ylog(h_\theta(x)) - (1-y)log(1-h_\theta(x))\\)

There are other alternative to minimize \\(J(\theta)\\) other than gradient descent, no detailed introduction to them. 

Underfitting, or high bias, is when the form of our hypothesis function h maps poorly to the trend of the data. It is usually caused by a function that is too simple or uses too few features. At the other extreme, overfitting, or high variance, is caused by a hypothesis function that fits the available data but does not generalize well to predict new data

This terminology is applied to both linear and logistic regression. There are two main options to address the issue of overfitting:

1) Reduce the number of features:
* Manually select which features to keep.
* Use a model selection algorithm.

2) Regularization
* Keep all the features, but reduce the magnitude of parameters \\(\theta(j)\\)
* Regularization works well when we have a lot of slightly useful features.
 
