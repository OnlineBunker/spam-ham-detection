# Spam Email Classification Using Bag-of-Words and Logistic Regression

## 1. Introduction

This project implements a complete spam email classification pipeline using classical Natural Language Processing (NLP) techniques and Logistic Regression.

The objective is to convert raw email text into numerical feature vectors and train a machine learning model capable of distinguishing between:

* **Ham (0)** – Legitimate emails
* **Spam (1)** – Unwanted or malicious emails

This project demonstrates the full workflow of a real-world text classification system, including data preparation, feature engineering, vectorization, model training, evaluation, and interpretation.

---

## 2. Problem Statement

Given a dataset of emails labeled as spam or ham, build a machine learning model that:

1. Converts each email into a sparse feature vector.
2. Trains a classifier on the training dataset.
3. Evaluates performance using appropriate metrics.
4. Identifies the most important words influencing predictions.

---

## 3. Dataset Overview

The dataset contains two columns:

* `text` – Raw email content
* `label` – Target variable (0 = ham, 1 = spam)

Dataset distribution:

* 2500 Ham emails
* 500 Spam emails

This class imbalance requires careful evaluation and handling.

---

## 4. Project Pipeline

The project follows a structured machine learning workflow:

1. Data Splitting
2. Text Vectorization
3. Model Training
4. Model Evaluation
5. Model Interpretation

Each step is explained below.

---

## 5. Step 1: Train-Test Split

Before any preprocessing or vectorization, the dataset is split into training and testing sets.

Stratified splitting is used to preserve the class ratio in both sets.

Why?

If the dataset is not shuffled properly, the model may see only ham emails in training and only spam in testing, leading to incorrect results.

Stratification ensures statistical validity.

---

## 6. Step 2: Text Vectorization (Bag-of-Words)

Machine learning models cannot understand raw text. Therefore, each email must be converted into a numeric representation.

### 6.1 Vocabulary Construction

The training dataset is scanned to build a vocabulary of all unique words.

Example:

If the vocabulary is:

["hello", "how", "are", "you"]

Then the email:

"hello you hello"

Can be represented as:

Count representation:
[2, 0, 0, 1]

Binary representation:
[1, 0, 0, 1]

Each position corresponds to a word in the vocabulary.

---

### 6.2 Sparse Matrix Representation

Most emails contain only a small subset of all possible vocabulary words.

Instead of storing thousands of zeros, sparse matrices store only:

* Non-zero values
* Their positions

This makes computation efficient and memory-friendly.

The project uses `CountVectorizer` to:

* Tokenize text
* Remove stopwords
* Build vocabulary
* Generate sparse matrices

---

## 7. Step 3: Model Training

The project uses Logistic Regression for classification.

Why Logistic Regression?

* Performs well in high-dimensional spaces
* Efficient for sparse text data
* Produces interpretable coefficients

Class imbalance is handled using:

```
class_weight='balanced'
```

This adjusts decision boundaries to account for fewer spam samples.

---

## 8. Step 4: Model Evaluation

Accuracy alone is not sufficient due to class imbalance.

The following metrics are used:

* Precision
* Recall
* F1-score
* Confusion Matrix

### Why Precision Matters

In spam detection:

* False Positive = Legitimate email marked as spam
* False Negative = Spam email marked as legitimate

False positives are particularly harmful in real systems.

Therefore, precision is critically analyzed.

---

## 9. Step 5: Model Interpretation

Logistic Regression assigns a coefficient to each word.

* Positive coefficient → pushes prediction toward spam
* Negative coefficient → pushes prediction toward ham

By sorting coefficients, we can identify:

* Top spam-indicative words
* Top ham-indicative words

This makes the model transparent and interpretable.

---

## 10. Optional Feature Engineering

Additional structural features can be included:

* URL count
* Exclamation mark count
* Uppercase ratio
* Character length

These features capture behavioral patterns commonly seen in spam emails.

Combining lexical (word-based) and structural features improves performance.

---

## 11. Key Concepts Learned

This project demonstrates:

* Text preprocessing
* Tokenization
* Vocabulary construction
* Sparse matrix representation
* Handling class imbalance
* Model evaluation beyond accuracy
* Interpretable machine learning

---

## 12. Future Improvements

Potential enhancements:

* Use TF-IDF instead of raw counts
* Try Naive Bayes classifier
* Use n-grams (bigrams, trigrams)
* Perform hyperparameter tuning
* Deploy model using a web interface

---

## 13. Conclusion

This project transforms raw language into structured numerical space and trains a classifier to detect spam emails effectively.

It illustrates how:

Text → Tokenization → Vector Space → Classification → Evaluation

forms the foundation of classical NLP pipelines.

By understanding both the statistical foundation and practical implementation, this project bridges theory and applied machine learning.

---

## Author

Yash
