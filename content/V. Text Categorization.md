---
title: V. Text Categorization
date: 2024-11-19
---
### Q: Given the classification results in the following confusion matrix, compute the classification accuracy, precision, recall, and F-score of the positive data. It is sufficient to provide the expressions. [2 + 2 + 2 + 2 = 8 points]

#### Confusion Matrix:

| Classified as | Positive | Negative |
|---------------|----------|----------|
| **Positive**  | 50       | 10       |
| **Negative**  | 5        | 200      |

---

### Expressions:

1. **Accuracy:**  
   <code>Accuracy = (TP + TN) / Total Samples</code>  
   Substitute values:  
   <code>Accuracy = (50 + 200) / (50 + 10 + 5 + 200)</code>

2. **Precision (Positive Class):**  
   <code>Precision = TP / (TP + FP)</code>  
   Substitute values:  
   <code>Precision = 50 / (50 + 5)</code>

3. **Recall (Positive Class):**  
   <code>Recall = TP / (TP + FN)</code>  
   Substitute values:  
   <code>Recall = 50 / (50 + 10)</code>

4. **F-score (Positive Class):**  
   <code>F<sub>1</sub> = 2 * (Precision * Recall) / (Precision + Recall)</code>  
   Substitute values:  
F<sub>1</sub> = 2 * ((50 / (50 + 5)) * (50 / (50 + 10))) / ((50 / (50 + 5)) + (50 / (50 + 10)))

### Q: We know that Naive Bayes' final decision is based using the probability function P(c|X) = P(c)P(X|c)/P(X) where c denotes the class variable and X the instance which needs to be classified. Answer the following: 

(a) Is the decision function obtained using MAP (Maximum a-priori) estimation or MLE (Maximum Likelihood Estimation)? Justify the priors, likelihood and posterior.

(b) How would the Naive Bayes classifier's final decision function differ if we were to use maximum likelihood estimation(MLE)? ie., Assuming no class prior or uniform class prior (each class is equally likely).

(c) What makes Naive Bayes "naive"? Explain briefly