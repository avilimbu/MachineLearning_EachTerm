# Supervised Machine Learning

Supervised Machine Learning is a type of machine learning where an algorithm learns from **labeled data**. This means each training example contains both the **input features** and the **correct output (target)**.

The main goal is for the model to learn the relationship between inputs and outputs so that it can make accurate predictions on **new, unseen data**.

---

## Core Idea of Supervised Learning

In supervised learning, we provide the algorithm with a dataset containing input-output pairs:

```text
(x₁, y₁), (x₂, y₂), ..., (xₙ, yₙ)
```

Where:

* `xᵢ` represents the **input features**.
* `yᵢ` represents the **known output or target**.
* `n` represents the total number of training examples.

For example, if we want to predict the price of a house:

* **Input:** Size, location, number of rooms, age of house
* **Output:** House price

The algorithm learns the relationship between these inputs and the known outputs during the **training process**.

After training, we provide new, unseen input data:

```text
x_new
```

The trained model then produces a prediction:

```text
ŷ_new
```

The objective is to make the predicted output as close as possible to the actual output.

---

## How Supervised Learning Works

The general process can be summarized as follows:

```text
Labeled Data
     ↓
Data Preprocessing
     ↓
Training Data
     ↓
Machine Learning Algorithm
     ↓
Model Training
     ↓
Trained Model
     ↓
New / Unseen Data
     ↓
Prediction
```

During training, the model adjusts its internal parameters to reduce the difference between its predictions and the actual target values.

---

## Common Supervised Learning Algorithms

Some commonly used supervised machine learning algorithms include:

* Linear Regression
* Logistic Regression
* Decision Trees
* Random Forest
* Support Vector Machines (SVM)
* K-Nearest Neighbors (KNN)
* Naive Bayes
* Polynomial Regression
* Ridge Regression
* Lasso Regression

---

# Two Main Types of Supervised Learning

Supervised learning problems are mainly divided into two categories based on the type of output being predicted:

1. **Regression**
2. **Classification**

---

## 1. Regression

### Definition

**Regression** is a supervised learning technique used to predict a **continuous numerical value**.

The output can be any value within a numerical range.

### Examples of Regression Outputs

* House price → `$250,000`
* Temperature → `28.5°C`
* Salary → `$45,000`
* GDP → `$35.7 billion`
* Sales revenue → `$120,500`

### Goal

The goal of regression is to learn the relationship between the input variables and a continuous numerical target.

### Common Regression Algorithms

* Linear Regression
* Polynomial Regression
* Ridge Regression
* Lasso Regression
* Decision Tree Regression
* Random Forest Regression
* Support Vector Regression (SVR)

### Examples

**House Price Prediction**

Predicting the price of a house based on:

* House size
* Location
* Number of rooms
* Age of the house

**GDP Prediction**

Predicting a country's future GDP based on factors such as:

* Population
* Inflation
* Exports
* Imports
* Agriculture
* Investment
* Employment
* Other economic indicators

Since GDP is a continuous numerical value, this is a **regression problem**.

---

# 2. Classification

### Definition

**Classification** is a supervised learning technique used to predict a **category or class label**.

Unlike regression, the output belongs to one or more predefined categories.

### Examples of Classification Outputs

* Spam / Not Spam
* Disease / No Disease
* Cat / Dog / Bird
* Male / Female
* Digit 0–9
* Positive / Negative

### Goal

The goal of classification is to learn how to assign an input to the correct class.

### Common Classification Algorithms

* Logistic Regression
* Decision Trees
* Random Forest
* Support Vector Machines (SVM)
* K-Nearest Neighbors (KNN)
* Naive Bayes

---

## Types of Classification

### Binary Classification

Binary classification involves **two possible classes**.

Examples:

```text
Spam       → 1
Not Spam   → 0
```

Other examples include:

* Yes / No
* Pass / Fail
* Disease / No Disease
* Fraud / Not Fraud

---

### Multi-Class Classification

Multi-class classification involves **more than two classes**, where each input belongs to one class.

For example, handwritten digit recognition:

```text
0
1
2
3
4
5
6
7
8
9
```

Another example is classifying animals:

```text
Cat
Dog
Bird
Horse
```

---

### Multi-Label Classification

In multi-label classification, a single input can belong to **multiple classes simultaneously**.

For example, a movie could have multiple genres:

```text
Action
Comedy
Adventure
```

Unlike multi-class classification, the model can assign more than one label to the same input.

---

# Regression vs Classification

| Aspect                 | Regression                                             | Classification                                             |
| ---------------------- | ------------------------------------------------------ | ---------------------------------------------------------- |
| **Output Type**        | Continuous numerical value                             | Discrete category or label                                 |
| **Main Goal**          | Predict a numerical value                              | Predict a class                                            |
| **Example Output**     | Price, temperature, GDP, salary                        | Spam/Not Spam, Cat/Dog, 0–9                                |
| **Typical Algorithms** | Linear Regression, Polynomial Regression, Ridge, Lasso | Logistic Regression, SVM, Decision Trees, KNN, Naive Bayes |
| **Common Metrics**     | MSE, RMSE, MAE, R²                                     | Accuracy, Precision, Recall, F1-Score, ROC-AUC             |

---

## Simple Example

Suppose we have information about students.

### Regression

We want to predict a student's **final exam score**:

```text
Study Hours → 5
Attendance  → 85%
Assignments → 90%

Prediction → 82.5 marks
```

Because the output is a numerical value, this is **Regression**.

### Classification

Now suppose we want to predict whether the student will **Pass or Fail**:

```text
Study Hours → 5
Attendance  → 85%
Assignments → 90%

Prediction → Pass
```

Because the output is a category, this is **Classification**.

---

## Key Difference

The easiest way to remember the difference is:

> **Regression predicts "how much" or "how many".**

> **Classification predicts "which category".**

For example:

```text
House Price = $250,000
             ↓
          Regression


House Type = Apartment
             ↓
        Classification
```

---

## Summary

Supervised Machine Learning uses **labeled data** to train a model to make predictions on new data.

The two major types are:

* **Regression** → Predicts continuous numerical values.
* **Classification** → Predicts categories or class labels.

```text
                 Supervised Learning
                        │
             ┌──────────┴──────────┐
             │                     │
        Regression            Classification
             │                     │
      Numerical Output       Categorical Output
             │                     │
        GDP, Price,          Spam, Animal,
        Temperature          Pass/Fail, etc.
```
