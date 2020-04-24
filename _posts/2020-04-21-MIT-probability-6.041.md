---
layout: post
title: MIT probability 6.041
tags: [MIT, ML]
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"
---

Probability notes from MIT 6.041

## Week1

Sample Space: \\(\Omega\\)
- List (Set) of possible outcomes
	- Mutually exclusive
	- Collectively exhaustive (At least one of the events must occur)
- To be at the "right graularity"

Axioms:
- Nonnegativity: \\(P(A) \geq 0\\)
- Normalization: \\(P(\Omega) = 1\\)
- Additivity: if \\(A \cap B = \empty \\), then \\(P(A\cup B) = P(A) + P(B) \\)



## Week2

Beye's Rule is ```a foundation of a lot of inference based on partial observation```

\\(P(A|B)=\\) Probability of A, given that B occurred
- B is our new universe
Definition: Assuming \\(P(B) \not = 0\\)
\\[P(A|B) = \frac{P(A\cap B)}{P(B)}\\]
\\[P(A \cap B) = P(B) * P(A | B) \\]

* Conditional probablity still obey Axioms, e.g.
\\(A \cap B = \empty\\)
\\(P(A \cup B | C) = P(A|C) + P(B|C)\\)
