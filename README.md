# Spam Email Classification using Machine Learning

## Overview

This project builds a spam detection system using classical Natural Language Processing (NLP) techniques and Logistic Regression.

The goal is to classify emails as:

* **Ham (0)** – Legitimate email
* **Spam (1)** – Unwanted or malicious email

The model converts raw email text into numerical feature vectors and learns statistical patterns that distinguish spam from normal communication.

---

## Dataset

* 2500 Ham emails
* 500 Spam emails

The dataset is imbalanced and handled using stratified splitting and balanced class weights.

---

## Pipeline

1. **Train-Test Split (Stratified)**
2. **Text Vectorization using Bag-of-Words**
3. **Sparse Matrix Representation**
4. **Logistic Regression Model**
5. **Evaluation using Precision, Recall, F1-score**
6. **Model Interpretation via Word Coefficients**

---

## Key Techniques Used

* `CountVectorizer` for tokenization and vocabulary building
* Sparse matrix representation (CSR format)
* Logistic Regression with `class_weight='balanced'`
* Proper evaluation beyond accuracy

---

## Why Logistic Regression?

* Performs well in high-dimensional sparse spaces
* Efficient and interpretable
* Strong baseline for text classification

---

## Model Evaluation

Since the dataset is imbalanced, the following metrics were used:

* Precision
* Recall
* F1-score
* Confusion Matrix

Precision is especially important in spam detection to avoid marking legitimate emails as spam.

---

## What This Project Demonstrates

* End-to-end NLP pipeline construction
* Proper handling of class imbalance
* Sparse vector mathematics in text classification
* Interpretable machine learning

---

## Future Improvements

* TF-IDF vectorization
* N-grams (bigrams, trigrams)
* Naive Bayes comparison
* Hyperparameter tuning
* Web deployment

---

## Author

Yash
B.Tech Computer Science & AI
