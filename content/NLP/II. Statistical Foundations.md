---
title: II. Statistical Foundations
date: 2024-11-17
---
### Q6: Express the probabilities of the following events in terms of P(A), P(B) and P(A ∩ B)

##### a) either A or B or both

##### b) either A or B but not both

##### c) at least one of A or B

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
### Q8: A fair dice is cast continuously until a 6 appears. What is the probability that it must be cast more than 3 times? An exact value is not required. A numerical expression is sufficient.

**Sol:**
Let W and L denote the events a win (a 6 appears) and a loss (no 6 appears) on a single throw of a dice. 

Clearly, P(W) = 1/6 and = P(L) = 5/6

Sample space, S = {W, LW, LLW, LLLW, LLLLW, ... }

The event **E**, that it must be cast more than 3 times, denotes that the first three throws must result in losses (**L**), and the win (**W**) must occur on or after the 4th throw. In other words: 

E = { LLLW, LLLLW, LLLLLW, ... }

1 - P(E<sup>c</sup>) = 1 - P({W, LW, LLW}) = 1- P[P(W) + P(LW) + P(LLW)] = 1 - [1/6 + 5/36 + 25/216]

### Q9: Suppose 5% of men and 0.25% of women in some African tribe are color blind. A random person is chosen from the tribe and was examined to be color blind. What is the probability that the person is male? Assume males and females are equal in numbers. An exact value is not required. A numerical expression is sufficient.
**Sol**: 2381/2500

Using Bayes rule:

`P(M|CB) = P(CB|M)P(M)/(P(CB|M)P(M) + P(CB|F)P(F))`

### Q10: For some events A and B in a given sample space, we have P(A) > 0 and P(B) > 0
**Justify your answer. Recall that if A and B are independent, then we have P(A ∩ B) = P(A) * P(B) and if A and B are disjoint / mutually exclusive, then P(A ∩ B) = 0**
###### a) If A and B are mutually exclusive, can they be independent?
**Answer:** No, A and B cannot be independent if they are mutually exclusive. 

**Justification:** If A and B are mutually exclusive, it means **P(A ∩ B) = 0**. For A and B to be independent, we require: **P(A ∩ B) = P(A) × P(B)**. Since **P(A) > 0** and **P(B) > 0**, the product **P(A) × P(B) > 0**, which contradicts **P(A ∩ B) = 0**. Thus, mutually exclusive events cannot be independent.
###### b) If A and B are independent, can they be disjoint (i.e., mutually exclusive)?
**Answer:** No, A and B cannot be disjoint if they are independent. **Justification:** If A and B are disjoint, it means **P(A ∩ B) = 0**. For A and B to be independent, we require: **P(A ∩ B) = P(A) × P(B)**. If **P(A) > 0** and **P(B) > 0**, then **P(A) × P(B) > 0**, which contradicts **P(A ∩ B) = 0**. Therefore, independent events cannot be disjoint.


### Q11: Seven balls are distributed randomly into 7 baskets, i.e., each basket can get anywhere between 0 to 7 balls and the sum of all balls in each basket should be 7. We define the random variable:
X<sub>i</sub> = The number of baskets containing exactly i balls

What are the possible values for X₃? [2]

**Professor's Sol**: The only possible values for X₃ = {0,1,2} as there cannot be 3 baskets containing 3 balls or in general i baskets each containing *i* balls for *i* >=3. This is because we only have 7 balls and 7 baskets.

**Chat's Sol:  X<sub>3</sub>** represents the number of baskets that contain exactly 3 balls. Since the total number of balls is 7, and each basket can have anywhere between 0 to 7 balls, the possible values of **X<sub>3</sub>** depend on whether it is feasible to have baskets containing exactly 3 balls. 
- If 1 basket contains exactly 3 balls (**X<sub>3</sub> = 1**), the remaining 4 balls must be distributed across the other baskets such that no other basket has 3 balls. 
- If 2 baskets each contain exactly 3 balls (**X<sub>3</sub> = 2**), the remaining ball must go into another basket, with no more baskets having 3 balls. 
- It is not possible for **X<sub>3</sub> > 2**, as 2 baskets with 3 balls already use 6 balls, leaving only 1 ball for the remaining baskets. Thus, the possible values for **X<sub>3</sub>** are: **X<sub>3</sub> ∈ {0, 1, 2}

### Q12:  Write a pseudocode to simulate the categorical distribution. You are given the method/function `Math.rand()` which returns you a uniformly distributed random variable in [0,1], i.e., X = Math.rand() and X ~ Uni(0,1). [4 + 2]

###### (a) Specifically, simulate a 3-way toss using Cat(3,<0.5,0,0.5>), i.e., write the method for `int SimulateCategorical(int n=3, double [] dist = {0.5, 0, 0.5})`.

###### (b) Is (a) equivalent to a fair coin toss? Why or why not? In what cases does the code in (a) return 2?

Sol:


