---
title: III. Collocations, Hypothesis testing, N-gram Language Model
date: 2024-11-18
---
### Q14: What is a collocation (of consecutive words)? How are they discovered? Are all collocations informative? What tends to make a collocation interesting/informative as opposed to merely being a frequently occurring (and often containing stop words) pattern? [2+2+2+2]

Sol: Juxtaposing of words corresponding to a convention in language usage is collocation. They can be discovered by frequency counts of the  ngrams of the words. Usually no. Collocations with associated POS tag pattern/ngram containing a N/NP tend to be informative.

### Q15: Which of Chi-squared (χ²) test or t-test is mostly used for determining word collocation? Why? [3+3]

Sol: For collocation discovery Chi-squared (χ²) is usually preferred because the Chi-squared (χ²) can better deal with small counts/probabilities of words than t-test. Chi-squared (χ²) test also does not assume that the means of the sample is normally distributed (as in t-test) and thus reflects a more natural setting to model words as they are usually not normally distributed.

### Q16: What is the main drawback of t-test? How does Chi-squared (x2) get around it? [2+2]

Sol: t-test assumes the samples are normally distributed. Chi-squared (χ²) directly measures the difference between observe and expected frequencies without assuming the samples are normally distributed.

### Q17: Answer the following based on the main idea of t-test [2+4] (Incomplete).

(a) Does higher t value in the t-test indicate lower confidence in rejecting the null hypothesis?

(b) Arrange the p-values in the increasing order for three experiments A, B, C whose *t* values (obtained using)

t-test value, for experiment A, t<sub>A</sub> = 2.156

t-test value, for experiment B, t<sub>B</sub> = 1.656

t-test value, for experiment C, t<sub>c</sub> =3.556

i.e., Arrange the p-values of the experiments, P<sub>A</sub> , P<sub>B</sub>, and p<sub>c</sub> in the increasing order assuming
(more specifically, they and the associated t-tests have the same degrees of freedom). [3+3]

Sol:
(a) No. Higher values of t using a t-test indicate lower p-values and hence higher confidence in rejecting the null hypothesis.

(b) Higher values of t using a t-test indicate lower p-values. Hence we have P<sub>C</sub> < P<sub>A</sub> < P<sub>B</sub>.
### Q18: Recall that the Chi-squared (χ²) test measures the difference between two random variables using the expected observed counts to compute whether a bigram is a collocation or not. The Chi-squared (χ²) value for a given contingency table for bigram ***w***₁ ***w***₂ with observed counts as:

|         | **w₁** | **¬w₁** |
| ------- | ------ | ------- |
| **w₂**  | W      | X       |
| **¬w₂** | Y      | Z       |

The Chi-squared statistic is computed using the formula:

**χ² = [(N * W * Z) - (X * Y)]² / [(W + Y) * (X + Z) * (W + X) * (Y + Z)]**

---
#### Questions:

**(a)** Which out of these two bigrams tends to be more likely to form a collocation?

**(b)** Which bigram has a lower p-value?

**(c)** Can we say the words "swiss" and "bar" appear independently?  
   i.e., Can we accept the null hypothesis if our confidence level is set to 99.9%?

**(d)** Can we say the words "mercedes" and "benz" form a collocation and are correlated? i.e, Can we accept the alternate hypothesis?

#### Table 1: "swiss" and "bar"

|              | **w₁ = swiss** | **w₁ ≠ swiss** |
|--------------|----------------|----------------|
| **w₂ = bar** | 2              | 5              |
| **w₂ ≠ bar** | 10             | 20             |

#### Table 2: "mercedes" and "benz"

|              | **w₁ = mercedes** | **w₁ ≠ mercedes** |
|--------------|--------------------|--------------------|
| **w₂ = benz** | 10                 | 12                 |
| **w₂ ≠ benz** | 11                 | 50                 |
For your convenience, you are provided with the χ² value for each as follows:

- **χ² (swiss, bar) = 0.059**
- **χ² (mercedes, benz) = 6.433**

Also, the following excerpt of the χ² table is provided.
![[Pasted image 20241118190622.png]]

| **df** | **χ²<sub>0.995</sub>** | **χ²<sub>0.990</sub>** | **χ²<sub>0.975</sub>** | **χ²<sub>0.950</sub>** | **χ²<sub>0.900</sub>** | **χ²<sub>0.100</sub>** | **χ²<sub>0.050</sub>** | **χ²<sub>0.025</sub>** | **χ²<sub>0.010</sub>** | **χ²<sub>0.005</sub>** |
|--------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|
| 1      | 0.000                   | 0.000                   | 0.001                   | 0.004                   | 0.016                   | 2.706                   | 3.841                   | 5.024                   | 6.635                   | 7.879                   |


**Professor's Sol:**
(a) Clearly Mercedes benz as it has a much larger χ² value implying stronger correlation of the terms.

(b) "mercedes benz". This is because higher χ² values indicate, stronger correlation, higher confidence of rejecting the null hypothesis, and subsequently lower p-values.

(c) Yes.

(d) Yes
### Q18: Solution
#### (a) 

To determine if a bigram forms a collocation, compare their **χ² values** with the critical values in the Chi-squared table. Higher χ² values indicate a stronger likelihood of a collocation.

- **χ² (swiss, bar) = 0.059**
- **χ² (mercedes, benz) = 6.433**

From the Chi-squared table:
- For **df = 1** and **confidence level = 99.9%**, the critical value is **6.635**.

- **χ² (swiss, bar) = 0.059**: This is much smaller than 6.635, so "swiss" and "bar" do not form a strong collocation.
- **χ² (mercedes, benz) = 6.433**: This is closer to 6.635 but still below the threshold, so "mercedes" and "benz" are more likely to form a collocation compared to "swiss" and "bar."

**Answer:** "mercedes" and "benz" are more likely to form a collocation than "swiss" and "bar."

---

#### (b) Which bigram has a lower p-value?

- A higher χ² value corresponds to a smaller p-value.
- **χ² (swiss, bar) = 0.059** has a much smaller χ² value, indicating a higher p-value.
- **χ² (mercedes, benz) = 6.433** has a higher χ² value, indicating a smaller p-value.

**Answer:** The bigram **"mercedes" and "benz"** has a lower p-value.

---
#### (c) Can we say the words "swiss" and "bar" appear independently?

To test independence:
- **Null hypothesis (H₀):** "swiss" and "bar" are independent.
- **Alternate hypothesis (H₁):** "swiss" and "bar" are not independent.

From the Chi-squared table:
- For **df = 1** and **confidence level = 99.9%**, the critical value is **6.635**.

- **χ² (swiss, bar) = 0.059**: This value is much smaller than 6.635, meaning we fail to reject the null hypothesis.

**Answer:** Yes, "swiss" and "bar" appear independently. The null hypothesis is accepted at the 99.9% confidence level.

### Q19: (a) What is maximum likelihood estimate of a trigram? (b) Provide an MLE expression for computing p(x<sub>n</sub>|x<sub>n-1</sub>,x<sub>n-2</sub>) in terms of the count variables c(x<sub>n-2</sub>,x<sub>n-1</sub>,x<sub>n</sub>) and c(x<sub>n-1</sub>,x<sub>n-2</sub>). [2+2]

Sol:

(a) Maximum Likelihood Estimates (MLEs) refer to the probabilities of n-grams computed using corpus frequency counts of their components. For a trigram, the MLE is the conditional probability of the current word given the previous two words.

(b) p(x<sub>n</sub>|x<sub>n-1</sub>,x<sub>n-2</sub>) = c(x<sub>n-2</sub>,x<sub>n-1</sub>,x<sub>n</sub>)/c(x<sub>n-1</sub>,x<sub>n-2</sub>).

### Q20: (a) What is smoothing? (b) Why do we need it? [2+2]
**Prof's Sol:** Smoothing is a technique for interpolating/assigning non-zero probabilities to unseen ngrams in training. It is required because we don't obtain 0 probabilities when computing the probability of an unseen ngram (as owing to chain rule it can result in probability of entire sentence or even corpus to be 0).

**Chat's Sol:** **(a) Smoothing** is a statistical technique to adjust the probabilities of n-grams (sequences of words) in a language model. In simpler terms, it ensures that even the n-grams we didn’t observe in our training data are given a small, non-zero probability.

For example, if your training data doesn’t contain the phrase "blue unicorn," without smoothing, the probability of "blue unicorn" would be 0. This is problematic, as many valid sequences may not appear in the training set but still occur in real-world use. **(b)** Smoothing is important because **if an unseen n-gram has a probability of 0, it can "break" the probability calculations for a larger sequence or even the entire sentence or document**.

Example:
- Say you want to compute the probability of the sentence: "I saw a blue unicorn."
- If "blue unicorn" is an unseen n-gram, its probability is 0.
- This makes the probability of the entire sentence 0.

### Q21:  What is Markov assumption? Assuming a trigram model (which follows a 2<sup>nd</sup> order Markov assumption), what is the probability of p(_dog_|_The quick brown fox jumped over the lazy_) in the sentence:
Sol.

(a) The Markov assumption states that the prediction of the next word only depends on some fixed number of previous words rather than the entire history.

(b) p(_dog_|_The quick brown fox jumped over the lazy_) ≈ p(_dog_|_the lazy_)

### Q22: Where can language models be used? Explain with an example. [4]

Sol: In disambiguation of optical character recognition where some words could not be parsed. Using a language model trained on a large corpus and figuring out the nearby words, one can use higher likelihood of ngrams to determine the missing word. Another application is detecting ambiguity.

### Q23. Compute these unigram and bigram probabilities based on the text snippet below. Each word has been assigned a part-of-speech tag, which is indicated after the slash. You should not solve the fraction in decimal but retain the fraction with the counts in numerator and denominator(e.g., 5/10). Show the numerator and denominator rather than just the resulting probability (e.g., 0.5) This will ensure you go the counts correct! Provide your final answer in the blanks.
```
I/PRO am/VERB a/ART nobody/NOUN.
Nobody/NOUN is/VERB perfect/ADJ.
Therefore/ADV I/PRO am/VERB perfect/ADJ.
```
(a) P(perfect)

(b) P(VERB)

(c) P(am | I)

(d) P(ADJ | VERB)

(e) P(VERB | ART)

**Sol:** 

(a) P(perfect)= 2/11

(b) P(VERB) = 3/11

(c) P(am | I)=2/2

(d) P(ADJ | VERB)=2/3

(e) P(VERB | ART)= 0/1

### Q24. Four different language models A, B, C, D were trained using different smoothing techniques on the same training techniques yielded a perplexity of 110, 120, 100, 90 respectively on a particular held out test set. Answer the following as true or false.

(a) Language model A is better than D.

(b) As perplexity of a language model on a test set increases, the probabilities estimate of the test corpus using the language model also decreases.

(c) The probability of the test corpus (held out data) using the language model A is higher than using the language model B.

(d) The next word predictive strengths or simply predictive power/effective of the language models follows the following order,
B<A<C<D.

**Sol: (a) F (b) T (c) F (d) T**

### Q25: Higher order n-gram suffer with: (choose all that apply) [3 points]

(a) Smoothing

(b) Data sparsity

(c) Usually have lower probability than lower order n-grams

(d) OOV words

(e) All the above

**Sol:** (b) and (c)