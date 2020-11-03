---
layout: post
title: Andrew Ng's Machine Learning on Coursera
tags: [ML]
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"
---

## Week1 & Week2:

* feature scaling and mean normalization is helping speed up gradient descent. 

\\[x_i = \frac{x_i-\mu_i}{max-min}\\]

* Normal Equation: Gradient descent gives one way of minimizing J. Let’s discuss a second way of doing so, this time performing the minimization explicitly and without resorting to an iterative algorithm. In the "Normal Equation" method, we will minimize J by explicitly taking its derivatives with respect to the θj ’s, and setting them to zero. This allows us to find the optimum theta without iteration. The normal equation formula is given below:

\\[\theta = (X^TX)^{-1}X^Ty\\]

Gradient descent has time complexity \\(O(kn^2)\\); Normal Equation is \\(O(n^3)\\), in which n is the number of features. In practice, when n exceeds 10,000 it might be a good time to go from a normal solution to an iterative process.
