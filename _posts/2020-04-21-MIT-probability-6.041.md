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
- Defn: \\(P(A \cap B)=P(A) * P(B)\\) in addition to \\(P(A \cap B) = P(B) \* P(A|B)\\)
- Symmetric with respect to A and B
	- applies even if \\(P(A) = 0\\)
	- implies \\( P(A \| B) = P(A) \\)

**Def of conditional independence:**
\\(P((A \cap B) | C) = P(A|C) * P(B|C)\\)

**Independence of a collection of events**
- Information on some of the events tells us nothing about probabilities related to the remaining events. 
- \\(P(A \cap B \cap C) = P(A) * P(B) * P(C)\\)
- Pairwise independence does not imply independence
