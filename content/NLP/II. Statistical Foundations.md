---
title: II. Statistical Foundations
date: 2024-11-17
---
### Q6: Express the probabilities of the following events in terms of P(A), P(B) and P(A ∩ B)

a) either A or B or both

b) either A or B but not both

c) at least one of A or B

**Sol**:

**a**. "A or B or both" is A ∪ B.  P(A ∪ B) = P(A) + P(B) - P(A ∩ B)

**b**. "A or B but not both" is (A ∩ B<sup>c</sup>) ∪ (B ∩ A<sup>c</sup>). Thus we have:
				P((A ∩ B<sup>c</sup>) ∪ (B ∩ A<sup>c</sup>)) 
				= P(A ∩ B<sup>c</sup>) + P(B ∩ A<sup>c</sup>)
				= [P(A) - P(A ∩ B)] + [P(B) - P(A ∩ B)]
				= P(A) + P(B) - 2P(A ∩ B)

**c.** "At least one of A or B" is A ∪ B. So we get the same answer as A

### Q7: For some events A and B in a given sample space, we have, P(A) = 1/3 and P(B<sup>c</sup>) = 1/4, where B<sup>c</sup> denotes the complement of B, i.e, non-occurrence of B. Can the events A and B be disjoint? Justify your answer.
Hint: Recall that for *A* and *B* to be disjoint, we must have P *A* ∩ *B* = 0.

**Sol:**

If A and B are disjoint, P(A ∪ B) = P(A) + P(B) = 1/3 + 3/4 = 13/12, which is impossible. More generally, if A and B are disjoint, then A ⊂ B<sup>c</sup> and P(A) ≤ P(B<sup>c</sup>). But here P(A) > P(B<sup>c</sup>), so A and B cannot be disjoint.
### Q8: A fair dice is cast continuously until a 6 appears. What is the probability is not required. A numerical expression is sufficient.
**Sol:**

Let W and L denote the events a win (a 6 appears) and a loss (no 6 appears) = P(L) = 5/6

