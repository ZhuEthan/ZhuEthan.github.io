---
layout: post
title: MIT probability 6.041
tags: [MIT, ML]
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"
---

Probability notes from MIT 6.041

## Week1: Probability models and Axioms

Sample Space: \\(\Omega\\)
- List (Set) of possible outcomes
	- Mutually exclusive
	- Collectively exhaustive (At least one of the events must occur)
- To be at the "right graularity"

Axioms:
- Nonnegativity: \\(P(A) \geq 0\\)
- Normalization: \\(P(\Omega) = 1\\)
- Additivity: if \\(A \cap B = \emptyset \\), then \\(P(A\cup B) = P(A) + P(B) \\)



## Week2: Conditioning and Beyes' rule

Beye's Rule is ```a foundation of a lot of inference based on partial observation```

\\(P(A|B)=\\) Probability of A, given that B occurred
- B is our new universe
Definition: Assuming \\(P(B) \not = 0\\)
\\[P(A|B) = \frac{P(A\cap B)}{P(B)}\\]
\\[P(A \cap B) = P(B) * P(A | B) \\]

* Conditional probablity still obey Axioms, e.g.
\\(A \cap B = \emptyset\\)
\\(P(A \cup B | C) = P(A|C) + P(B|C)\\)


## Week3: Independence

- Multiplication rule: 
\\(P(A \cap B) = P(B) * P(A|B) = P(A) * P(B|A)\\)

- Total probability theorem: 
\\(P(B) = P(A)\*P(B|A) + P(A^c)\*P(B|A^c)\\) 

- Beyes rule: 
\\[P(A_i|B) = \frac{P(A_i)P(B|A_i)}{P(B)}\\]

**"Defn:"** \\(P(B|A) = P(B)\\)
- Occurrence of A provides no info about B's occurrence. __Will A's occurrence change your belief of B's occurrence?__
- Defn: \\(P(A \cap B) = P(A) * P(B)\\) in addition to \\(P(A \cap B)\\) = \\(P(B)\\) * \\(P(A \| B)\\)
- Symmetric with respect to A and B
	- applies even if \\(P(A) = 0\\)
	- implies \\( P(A \| B) = P(A) \\)

**Def of conditional independence:**
\\(P((A \cap B) | C) = P(A|C) * P(B|C)\\)

**Independence of a collection of events**
- Information on some of the events tells us nothing about probabilities related to the remaining events. 
- \\(P(A \cap B \cap C) = P(A) * P(B) * P(C)\\)
- Pairwise independence does not imply independence

Note: Two events are independent doesn't mean they are still independent on some extra conditions. 

## Week 4: Counting

Discrete uniform law
- Let all sample points be equally likely. 
- binominal coeffs\\(\dbinom{n}{k} = \frac{n!}{k! (n-k)!}\\) 
- \\(\sum_{k=0}^n \dbinom{n}{k} =\\)  total number of subsets = \\(2^n\\)
- \\(\sum_{k=0}^n \dbinom{n}{k} p^{k} (1-p)^{n-k} =\\)  total probability = \\(1\\) (exploit all possible permutations of coin tosses)

## Week 5: Discrete Random Variables I

- Random Variables
	-	An assignment of a value (number) to every possible outcome
	-	Mathematically: A function from the sample space \\(\Omega\\)  to the **real numbers**. 
		-	discrete or continuous values
	- Can have several random variables defined on the same sample space
	- Notation: 
		- Random variable X
		- Numerical value x
- Probablity mass function (PMF)
	- \\(P_X (x) = P(X = x) = P({\omega \isin \Omega    s.t. X(\omega) = x})\\)
	- \\(P_X (x) \geq 0, \sum_x P_X (x) = 1\\)
	- How to compute PMF \\(P_X (x)\\)
		- collect all possible outcomes for which X is equal to x
		- add their probabilities. 
- Expectation
	- \\(E[X] = \sum_{x} xp_X (x)\\)
-	Interpretations: 
	-	Center of gravity of PMF
	-	Average in large number of repetitions of the experiment (to be substantiated later in this course)
	-	Let X be a r.v and let \\(Y = g(X)\\)
		-	hard \\(E[Y] = \sum_y yP_Y(y)\\)
		-	easy: \\(E[Y] = \sum_{x} g(x) P_X (x)\\)
	-	Caution: In general, \\(E[g(X)] \neq g(E[X])\\)
	\\(E[g(X)] = g(E[X])\\) if g is linear
- Properties:  if \\(\alpha, \beta\\) are constants, then: 
	- \\(E[\alpha] = \alpha\\)
	- \\(E[\alpha X] = \alpha E[X]\\)
	- \\(E[\alpha X + \beta] = \alpha E[X] + \beta\\)
- Variance: How spread the distribution is
	- Recall: \\(E[g(X)] = \sum_x g(x) p_X(x)\\)
	- Second moment: \\(E[X^2] = \sum_x x^2 p_X(x)\\)
	- Variance
		- \\(var(X) = E[(X-E[X])] ^ 2 = \sum_x (x-E[X])^2 P_X (x) = E[X^2] - (E[X])^2\\)
		
	-	Properties
		-	\\(var(X) \geq 0\\)
		-	\\(var(\alpha X + \beta) = \alpha ^ 2 var(X)\\)
		
## Week 6

**Conditional PMF and expectation**

\\(P_{X|A} (X) = P(X = x | A)\\)
\\(E[X|A] = \sum_x x P_{X|A} (x)\\)


\\(p_{X|A}(x) = P((X=x) | A)\\)
\\(E[g(X) | A] = \sum_x g(x)P_{X|A}(x)\\)

\\(P(B) = P(A_1)P(B|A_1) + ... + P(A_n)P(B|A_n)\\)
\\(P_X (x) = P(A_1)P_{X|A_1}(x) + ... + P(A_n)P_{X|A_n}(x)\\)
\\(E[X] = P(A_1)E[X|A_1] + ... + P(A_n)E[X|A_n]\\)

- Geometric example:
	- \\(A_1: (X=1), A_2: (X>1)\\)
		- \\(E[X] = P(X=1)E[X|X=1] + P(X>1)E[X|X>1] = p*(1-p)*(E[x]+1)\\)
		- Solve to get E[X] = 1/p

**Joint PMFs**
\\(P_{X, Y}(x, y) = P(X=x and  Y=y)\\)
- \\(\sum_x\sum_y P_{X, Y}(x, y) = 1\\)
- \\(P_x(x) = \sum_yP_{X, Y} (x, y)\\)
- \\(P_{X|Y}(x|y) = P(X=x | Y=y) = \frac{P_{X, Y}(x, y)}{P_Y(y)}\\)
- \\(\sum_xP_{X|Y}(x|y) = 1\\)

