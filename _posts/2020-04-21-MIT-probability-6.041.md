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
	- \\(P_X (x) = P(X = x) = P({\omega \in \Omega    s.t. X(\omega) = x})\\)
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
		
## Week 6: Discrete Random Variables II

#### Conditional PMF and expectation

* \\(P_{X \vert A}(X) = P(X = x \vert A)\\)
* \\(E[X \vert A] = \sum_x x P_{X \vert A} (x)\\)
* \\(p_{X \vert A}(x) = P((X=x) \vert A)\\)
* \\(E[g(X) \vert A] = \sum_x g(x)P_{X\vert A} (x)\\)
* \\(P(B) = P(A_1)P(B \vert A_1) + ... + P(A_n)P(B \vert A_n)\\)
* \\(P_X (x) = P(A_1)P_{X \vert A_1}(x) + ... + P(A_n)P_{X \vert A_n}(x)\\)
* \\(E[X] = P(A_1)E[X \vert A_1] + ... + P(A_n)E[X \vert A_n]\\)
- Geometric example:
	- \\(A_1: (X=1), A_2: (X>1)\\)
		- \\(E[X] = P(X=1)E[X\vert X=1] + P(X>1)E[X \vert X>1] = p(1-p)(E[x]+1)\\)
		- Solve to get E[X] = 1/p

#### Joint PMFs

* \\(P_{X, Y}(x, y) = P(X=x and Y=y)\\)
* \\(\sum_x\sum_y P_{X, Y}(x, y) = 1\\)
* \\(P_x(x) = \sum_yP_{X, Y} (x, y)\\)
* \\(P_{X \vert Y}(x \vert y) = P(X=x \vert Y=y) = \frac{P_{X, Y}(x, y)}{P_Y (y)}\\)
* \\(\sum_xP_{X \vert Y}(x \vert y) = 1\\)


### Week 7: Discrete Random Variables III

Random variables X, Y, Z are independent if: 

\\(P_{X, Y, Z} (x, y, z) = P_X(x) * P_Y(y) * P_Z(z) for all x, y, z\\)

Expectations: 
* In general: \\(E[g(X, Y)] = \sum_x \sum_y g(x, y) P_{X, Y}(x, y)\\)
* \\(E[\alpha X + \beta] = \alpha E[X] + \beta\\)
* \\(E[X+Y+Z] = E[X] + E[Y] + E[Z]\\)
* if X, Y are independent: 
	* \\(E[XY] = E[X] * E[Y]\\)
	* \\(E[g(X)h(Y)] = E[g(X)] * E[h(Y)]\\): If X is independent to Y, then h(Y) and g(X) are also independent.  

* \\(Var(\alpha X) = \alpha^2 Var(X)\\)
* \\(Var(X+\alpha) = Var(X)\\)
* Let \\(Z = X+Y\\)
	* if X, Y are independent:
		* \\(Var(X+Y) = Var(X) + Var(Y)\\)
* Example: 
	* If \\(X = Y, Var(X+Y) = Var(2X) = 4Var(X)\\)
	* If \\(X = -Y, Var(X+Y) = Var(0) = 0\\)
	* If X, Y indep and \\(Z = X-3Y\\)
	   \\(Var(Z) = Var(X)+Var(-3Y) = Var(X) + 9Var(Y)\\)
	   
## Week 8: Continuous Random Variables
* A continuous r.v. is described by a probability density function. 

\\[P(a \leq X \leq b) = \int_{a}^{b}f(x)dx\\]

\\(\int_{-\infty}^{\infty} f(x)dx = 1\\)
\\(P(x \leq X \leq x + \delta) = \int_{x}^{x+\delta} f_{X}dx * = f_{X}(x) * \delta\\)

#### Means and Variance
* \\(E[X] = \int_{-\infty}^{\infty} x f_X(x) dx\\)
* \\(E[g(X)] = \int_{-\infty}^{\infty}g(x)f_X(x)dx\\)
* \\(var(X) = \delta ^2 = \int_{-\infty}^{\infty}(x-E[X])^2f_X(x)dx = E[X^2]-(E[X])^2\\)
#### Continuous Uniform r.v.

* \\(f_X(x) = \frac{1}{b-a}, a \leq x \leq b, 0 otherwize\\)
* \\(E[X] = \int_{a}^{b} x * \frac{1}{b-a}dx = \frac{a+b}{2}\\)
* \\(\delta_{X}^{2} = \int_{a}^{b} (x - \frac{a+b}{2}) \frac{1}{b-a} dx = \frac{(b-a)^2}{12}\\)
* \\(\delta_x = \frac{b-a}{\sqrt 12}\\)

#### Gaussian (normal) PDF
* Standard normal N(0, 1): \\(f_X(x) = \frac{1}{\sqrt {2 \pi}}e^{-x^2/2}\\)
* \\(E[X] = 0\\)
* \\(Var(X) = 1\\)
* General normal function \\(f_X(x) = \frac{1}{\sigma\sqrt {2 \pi}}e^{-(x-\mu)^2/2\sigma^2}\\)
* Let \\(Y = aX + b\\)
	* Then: \\(E[Y] = a*\mu + b\\)
	* \\(Var(Y) = a^2\sigma^2\\)
	* Fact: \\(Y \sim N(a\mu+b, a^2\sigma^2)\\)
	
## Week 9: Multiple Continuous Random Variables
* \\(P((X, Y)) \in S) = \int\int_{S}f_{X, Y}(x, y)dxdy\\)
* Interpretation: 
	* \\(P(x \leq X\leq x+\delta, y \leq Y \leq y+\delta) \approx f_{X, Y}(x, y) * \delta^2\\)
	* Expectations: \\(E[g(X, Y)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x, y)f_{X, Y}(x, y)dxdy\\)
	* From the joint to the marginal: \\[f_X(x) * \delta \approx P(x \leq X \leq x + \delta) = \delta * \int_{-\infty} ^ {\infty} f_{X, Y} (x, y)dy\\]
	\\[f_X(x)  = \int_{-\infty}^{\infty}f_{X, Y}(x, y)dy\\]
	* X and Y are called independent if 
		\\[f_{X, Y}(x, y) = f_X(x)f_Y(y) for all x, y\\]

* Conditional probability
	* \\(P(x \leq X \leq x + \delta \vert Y \approx y) \approx f_{X \vert Y}(x \vert y) * \delta\\)
	* \\(f_{X \vert Y}(x \vert y) = \frac{f_{X, Y}(x, y)}{f_Y(y)} if f_Y(y) > 0\\)
	* If independent \\(f_{X, Y} = f_Xf_Y\\), we obtain
	\\[f_{X \vert Y}(x \vert y) = f_X (x)\\]
	
1. Set up sample space
2. Describe the probablity law for defined sample space
3. Identify the event of intersect
4. Calculate


## Week 10: Multiple Continuous Random Variables

\\[f_{X|Y}(x\vert y) = \frac{f_{X,Y}(x, y)}{f_Y(y)} = \frac{f_X(x)f_{Y\vert X}(y\vert x)}{f_Y(y)}\\]
\\[f_Y(y) = \int_x f_X(x)f_{Y\vert X}(y\vert x)dx\\]


\\[P_X(x)f_{Y\vert X}(y \vert x) * \theta = f_Y(y) P_{X\vert Y}(x \vert y) *\theta\\]

\\[f_{X\vert Y} = \frac{f_X(x) P_{Y\vert X}(y\vert x)}{P_Y(y)}\\]
\\[P_Y(y)=\int_x f_X(x)P_{Y\vert X}(y\vert x)dx\\]

- Obtain probablity mass for each possible value of \\(Y=g(X)\\)
\\[P_Y(y) = P(g(X) = y) = \sum_{x:g(x)=y}P_X(x)\\]

The continuous case: 

- Get CDF of Y: \\(F_Y(y) = P(Y \leq y)\\)
- Differentiate to get
\\[f_Y(y) = \frac{dF_Y}{dy}(y)\\]

$Example\\)

- \\(Y = aX+b\\) => to get \\(f_Y(y)\\) from \\(f_X(x)\\)
- \\(X: F_Y(y) = P(Y \leq y) = P(aX+b \leq y) = P(X \leq \frac{y-b}{a}) = F_x(\frac{y-b}{a}) = F_x(\frac{y-b}{a})\\) when \\(a > 0\\), similar apply to \\(a < 0\\)
\\[f_Y(y) = f_x(\frac{y-b}{a}) \frac{1}{\vert a\vert}\\]
