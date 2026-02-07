# LEARN.md — Technical Notes & Concepts

This document explains the theory and reasoning behind the spam classification project.

---

## 1. Why Split Before Vectorization?

If we build vocabulary using the entire dataset before splitting, the model indirectly sees information from the test set.

This causes **data leakage**, leading to artificially inflated performance.

Correct order:

1. Split data
2. Fit vectorizer on training data
3. Transform training and test sets separately

---

## 2. How Bag-of-Words Works

Each email is converted into a fixed-length vector.

Steps:

* Build vocabulary from training set
* Assign each unique word an index
* Represent each email as a vector of word counts (or presence)

Example:

Vocabulary:
["hello", "how", "are", "you"]

Email:
"hello you hello"

Vector:
[2, 0, 0, 1]

---

## 3. Sparse Matrix Representation

Most vocabulary words do not appear in a single email.

Instead of storing thousands of zeros, sparse matrices store only:

* Non-zero values
* Their column indices
* Row boundaries

Scikit-learn uses CSR (Compressed Sparse Row) format.

This makes computation memory-efficient and fast.

---

## 4. Why Class Imbalance Matters

Dataset:

* 2500 Ham
* 500 Spam

Accuracy can be misleading.

If a model predicts only ham:
Accuracy = 83%

But it completely fails at detecting spam.

Therefore:

* Use `class_weight='balanced'`
* Focus on precision, recall, F1-score

---

## 5. Why Logistic Regression Works Well for Text

Text vector space is:

* High-dimensional
* Sparse

Logistic Regression:

* Handles high-dimensional data efficiently
* Produces interpretable coefficients
* Learns linear decision boundaries in vector space

---

## 6. Interpreting Model Coefficients

Each word has a weight.

Positive weight → pushes prediction toward spam
Negative weight → pushes prediction toward ham

This makes the model transparent.

---

## 7. Structural Feature Engineering

Additional features explored:

* URL count
* Exclamation mark count
* Uppercase ratio
* Character length

These capture behavioral spam signals.

---

## 8. Limitations of Bag-of-Words

* Ignores word order
* Cannot understand semantics
* Treats all words independently

Future improvement:

* TF-IDF
* N-grams
* Embeddings

---

## 9. Core Insight

Spam detection is not about understanding language.

It is about detecting statistical asymmetry in word usage patterns.

Language → Vector Space → Linear Separation

That is the core of classical NLP.
