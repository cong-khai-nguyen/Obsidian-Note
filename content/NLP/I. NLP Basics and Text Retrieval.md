---
title: I. NLP Basics and Text Retrieval
date: 2024-11-17
---
### Q1: Binary Term-Document Incidence Matrix

Consider the following mini corpus containing 4 documents:

- **Doc-1:** breakthrough drug for schizophrenia  
- **Doc-2:** new schizophrenia drug  
- **Doc-3:** new approach for treatment of schizophrenia  
- **Doc-4:** new hopes for schizophrenia patients  

**(a)** Compute the **binary term-document incidence matrix** for this collection based on the terms:  

| **Term**         | **d1** | **d2** | **d3** | **d4** |
|-------------------|--------|--------|--------|--------|
| approach          | 0      | 0      | 1      | 0      |
| breakthrough      | 1      | 0      | 0      | 0      |
| drug              | 1      | 1      | 0      | 0      |
| for               | 1      | 0      | 1      | 1      |
| hopes             | 0      | 0      | 0      | 1      |
| new               | 0      | 1      | 1      | 1      |
| of                | 0      | 0      | 1      | 0      |
| patients          | 0      | 0      | 0      | 1      |
| schizophrenia     | 1      | 1      | 1      | 1      |
| treatment         | 0      | 0      | 1      | 0      |
 **(b)** Compute the inverted index for this mini corpus.
 
- approach -> 3  
- breakthrough -> 1  
- drug -> 1 -> 2  
- for -> 1 -> 3 -> 4  
- hopes -> 4  
- new -> 2 -> 3 -> 4  
- of -> 3  
- patients -> 4  
- schizophrenia -> 1 -> 2 -> 3 -> 4  
- treatment -> 3

**(c)** What is the result of the query: schizophrenia AND drug?
* {Doc-1, Doc-2}

**(d)** What is the result of the query: ``for AND NOT (drug OR approach)``?
* {Doc-4}
### Q2: Briefly define the following [2 + 2 + 2 + 2]

**(a) Syntax:**  
Sol: Grammatical ordering/structure of the language

**(b) Semantics:**
Sol: Meaning of words/language

**(c) Stopwords:**
Sol: Frequently appearing words (e.g., a, to, of, the, etc.) which are filtered out because they do not convey enough content/semantics.

**(d) Content/Function words:**
Sol: Non-stop words

### Q3: What is Query Optimization? How would you optimize nested AND queries? [1+1 = 2 points]
Sol: Query optimization refers processing queries at a particular sequence to ensure faster queries are usually optimized by processing queries in the increasing order of size of posting list

### Q4: What is Zipf's law? Mandelbrots's law? Provide formulae for them [2 + 2]
![[Pasted image 20241116180857.png]]
the term. 
#### Zipf's Law
Zipf's Law describes the relationship between the rank of a word and its frequency in a natural language text. It states that the frequency f of a word is inversely proportional to its rank r.
###### Formula:
f ∝ 1/r(r^-1)

or equivalently:

f = C/r
where:

- f = frequency of the word
- r = rank of the word (1 for the most frequent word, 2 for the second, etc.)
- C = a constant (depends on the corpus)

---
#### Mandelbrot's Law
Mandelbrot's Law is a generalization of Zipf's Law. It introduces two additional parameters to account for deviations observed in real-world text data. It states that the frequency f of a word is inversely proportional to a shifted power of its rank r.
###### Formula:

f = P/(r + ρ)^B

where:
- f = frequency of the word
- r = rank of the word
- P = a constant (scaling factor)
- ρ (rho) = a constant (shift factor)
- B = a power-law exponent (typically B ≥ 1)

### Q5:  If *f* and *r* denote the frequency and rank of the terms/words in a corpus, and we plot log(*f*) on y-axis and log(*r*) on x-axis, then[2 + 2]
a) The relationship of y and x is roughly (choose one): (1) quadratic, (2) inverse, (3) linear, (4) None

Sol: (3)

b) The slop is roughly: (1) positive (2) negative (3) undefined (4) constant
Sol: (2) and (4)

### Q6:  What is an inverted index, and what is it used for? What is its key advantage?
Sol: Inverted index builds the posting lists of all terms (sorted list of all documents in which it appears). It is used to retrieve results
of search queries and also many other IR applications. The key advantage lies in hashing of the terms with mapping to posting lists
in the inverted index as it can facilitate constant time retrieval of terms