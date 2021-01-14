---
layout: post
title: Reinforcement Learning (2)
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"
---


## Week1

**Marte Carlo.** 

In RL Monte Carlo methods allow us to estimate values (Not to get best policy) directly from experience, from sequences of states, actions and rewards. Learning from experience is striking because the agent can accurately estimate a value function without prior knowledge of the environments dynamics 

* To evaluate state value, we need to know transition probabilities before DP. 

Monte Carlo methods estimate values by averaging over a large number of random samples. 

Use Monte-Carlo Prediction to estimate the value function for a given policy. 


Undiscounted MDP where each game of blackjack corresponds to an episode. [example is interesting.]

Implications of Monte Carlo learning. 
* We do not need to keep a large model of the environment
* We are estimating the value of an individual state independently of the values of other states. 
* The computation needed to update the value of each state does not depend on the size of the MDP. Instead, it depends on the length of the episodes. 

Off-policy learning VS On-policy learning? 

Using Monte Carlo for Action-Values
