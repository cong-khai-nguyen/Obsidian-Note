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

**Sol:**
(a) MAP (Maximum a-priori) estimation. The priors are P(c), the likelihood is P(X|c), and the posterior is P(c|X).

(b) Under MLE, the final decision function would be P(X|c) = argmax P(X|c). This is because having no class prior or uniform class prior adds no additional knowledge if we multiply P(c) inside the argmax. It also follows directly from the definition of MLE - chose the class c that maximizes the likelihood of the given test instance, P(X|c).

(c) Words in a document instance, X = w1 ... wn, are conditionally independent of each other given the class of the document, i.e., P X = w1 ... wn | c = ∏i=1^n P(wi|c).

### Q: What is meant by the margin in a linear separable SVM? What is its expression in terms of the weight vector, w? How is it related to the final decision boundary/hyperplane that SVM constructs? [2+2+2=6 points]

Sol: Margin refers to the portion of the Euclidean space of ℝⁿ for an n-dimensional data which separates the positive and negative instances. Its expression is (w·w)/2. The final hyperplane of an SVM is the hyperplane which maximizes the margin.

### Q: What is feature selection? Why do we need it? Name 3 popular methods of feature selection. [2+2+2=6 points]
Sol: Feature selection is a technique to select a subset of relevant features having high discriminative strength. We need it to filter
non-relevant features/reduce feature space, dimensionality of the problem. Chi-squared, Information gain, and Mutual information
are some of the popular methods.

### Q: Can we directly use continuous attributes (e.g., height in inches, h € [50, 84]) in the classifiers Naïve Bayes, SVM, decision trees? Answer yes/no for each and provide a reason for your answer. How to deal with continuous attributes/features when we cannot use them directly? [3+2 = 5 points]

**Sol:**
Only SVM can directly use continuous attributes/features. NB and DT need feature discretization into multiple categories.
Continuous features need to be discretized (e.g., using equal width binning).

### Q: How does SVM deal with classification problems where the positive and negative classes are not linearly separable? In soft-margin SVM, what is minimized? [2+2 = 4 points]

**Sol:** It relaxes the constraints by adding slack variables so that the new hyperplane still finds the maximal separating margin allowing
but with minimum errors. This is a called soft-margin SVM.

In soft margin SVMs, the margin, (w . w)/2 + the penalized slack error CEE, is minimized.

### Q: The decision function for an SVM classifier is linear. Why do we say it is linear? Can we say the same for Naïve Bayes or Decision trees? [2+2 = 4 points]
