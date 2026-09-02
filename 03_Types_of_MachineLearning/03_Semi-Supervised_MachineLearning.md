# Semi-Supervised Machine Learning

**Semi-Supervised Machine Learning** is a machine learning approach that combines **labeled** and **unlabeled data** during the training process.

It typically uses:

* A small amount of **labeled data** — data paired with the correct answers.
* A much larger amount of **unlabeled data** — data without predefined answers.

Semi-supervised learning combines ideas from **supervised learning** and **unsupervised learning**. It is especially useful when manually labeling data is expensive, difficult, or time-consuming, while collecting large amounts of raw data is relatively easy.

---

## What is Semi-Supervised Learning?

In traditional supervised learning, the model requires a large amount of labeled data.

For example:

```text
Image 1 → Cat
Image 2 → Dog
Image 3 → Cat
Image 4 → Dog
```

However, creating labels for thousands or millions of examples can require significant human effort.

Semi-supervised learning addresses this problem by combining a small labeled dataset with a much larger unlabeled dataset.

```text
Small Labeled Dataset
        +
Large Unlabeled Dataset
        ↓
Semi-Supervised Learning
        ↓
Improved Model
```

---

# How Semi-Supervised Learning Works

Suppose we want to classify images of **cats and dogs**.

We have:

* **1,000 labeled images**
* **100,000 unlabeled images**

A typical process can be:

### Step 1 — Collect Data

Collect both labeled and unlabeled images.

```text
Labeled Images       → 1,000
Unlabeled Images     → 100,000
```

### Step 2 — Train an Initial Model

Train a machine learning model using the available labeled images.

```text
1,000 Labeled Images
        ↓
Initial Model
```

### Step 3 — Predict Unlabeled Data

Use the initial model to make predictions on the unlabeled images.

```text
100,000 Unlabeled Images
          ↓
     Initial Model
          ↓
Predicted Labels
```

For example:

```text
Image A → Cat (98% confidence)
Image B → Dog (96% confidence)
Image C → Cat (51% confidence)
```

### Step 4 — Select Confident Predictions

Predictions with high confidence can be treated as temporary labels.

For example, if we set a confidence threshold of `90%`:

```text
Cat → 98%  ✓ Use as pseudo-label
Dog → 96%  ✓ Use as pseudo-label
Cat → 51%  ✗ Ignore
```

### Step 5 — Retrain the Model

The original labeled data and confidently pseudo-labeled data are combined.

```text
Original Labeled Data
          +
Pseudo-Labeled Data
          ↓
      Retraining
          ↓
    Improved Model
```

This process can be repeated to improve the model's performance.

---

# Self-Training and Pseudo-Labeling

One of the most common approaches in semi-supervised learning is **self-training**, also known as **pseudo-labeling**.

The basic idea is:

```text
Labeled Data
     ↓
Train Model
     ↓
Predict Unlabeled Data
     ↓
Select High-Confidence Predictions
     ↓
Create Pseudo-Labels
     ↓
Add to Training Dataset
     ↓
Retrain Model
```

The generated labels are called **pseudo-labels** because they are predicted by the model rather than manually assigned by a human.

---

# Common Techniques

Semi-supervised learning can be implemented using several techniques.

## 1. Self-Training

In self-training, a model is first trained using labeled data.

The model then predicts labels for the unlabeled data.

Only highly confident predictions are added to the training dataset.

```text
Labeled Data
     ↓
Train Model
     ↓
Predict Unlabeled Data
     ↓
High-Confidence Predictions
     ↓
Pseudo-Labels
     ↓
Retrain Model
```

### Example

```text
Prediction          Confidence
──────────────────────────────
Cat                 97%   ✓
Dog                 95%   ✓
Cat                 52%   ✗
Dog                 48%   ✗
```

Only predictions above the selected confidence threshold are used.

---

# 2. Consistency Regularization

**Consistency regularization** encourages a model to produce similar predictions when the same input is slightly modified.

For example, an image might be:

* Rotated slightly
* Cropped
* Flipped
* Made brighter or darker
* Given small amounts of noise

The model should ideally produce the same prediction.

```text
Original Image
      ↓
   Model
      ↓
     Cat


Modified Image
      ↓
   Model
      ↓
     Cat
```

The goal is to make the model's predictions **consistent** despite small changes to the input.

---

# 3. Graph-Based Learning

Graph-based methods represent data points as nodes in a graph.

Similar data points are connected by edges.

Some nodes have known labels while others do not.

```text
          Cat
           ●
          / \
         /   \
        ●-----●
        |     |
        |     |
        ●-----●
       /       \
      ●         ●
   Unlabeled   Dog
```

Labels can then be propagated from labeled nodes to nearby unlabeled nodes based on their relationships or similarities.

This approach is useful when similar data points tend to have similar labels.

---

# 4. Generative Methods

Generative approaches attempt to learn the underlying structure or distribution of the data.

The model can first learn useful representations from both labeled and unlabeled data and then use the labeled examples to perform the final prediction task.

Conceptually:

```text
Labeled + Unlabeled Data
          ↓
 Learn Data Distribution
          ↓
Learn Useful Representation
          ↓
 Classification / Prediction
```

Generative approaches can be implemented using probabilistic models and neural-network-based techniques.

---

# Example: Spam Detection

Consider an email spam detection system.

Suppose we have:

```text
Labeled Emails      → 5,000
Unlabeled Emails    → Millions
```

The 5,000 labeled emails might contain:

```text
Email 1 → Spam
Email 2 → Legitimate
Email 3 → Spam
Email 4 → Legitimate
```

The remaining millions of emails do not have labels.

A semi-supervised model can use both datasets.

```text
5,000 Labeled Emails
          +
Millions of Unlabeled Emails
          ↓
Semi-Supervised Model
          ↓
Improved Spam Detection
```

The model can learn patterns such as:

* Words and phrases
* Sender behavior
* Message structure
* Email frequency
* Links and URLs
* Other characteristics

The unlabeled data provides additional information about the overall distribution of emails.

---

# Advantages and Limitations

| Advantages                               | Limitations                                                 |
| ---------------------------------------- | ----------------------------------------------------------- |
| Requires fewer manually labeled examples | Incorrect pseudo-labels can reinforce mistakes              |
| Reduces labeling cost and effort         | Performance depends on the quality of labeled data          |
| Can utilize large real-world datasets    | Incorrect assumptions about the data can reduce performance |
| Can improve generalization               | More complex to design than standard supervised learning    |
| Useful when labeled data is limited      | Evaluating performance can be more challenging              |

---

# When Should You Use Semi-Supervised Learning?

Semi-supervised learning is particularly useful when:

```text
Labeled Data        → Small
Unlabeled Data      → Large
Labeling Cost       → High
Raw Data Collection → Easy
```

For example, imagine you have:

```text
1,000 labeled images
+
500,000 unlabeled images
```

Manually labeling all 500,000 images could be expensive and time-consuming.

Semi-supervised learning allows the model to take advantage of the large amount of unlabeled data.

---

# Applications

Semi-supervised learning is used in many real-world applications.

### Medical Image Analysis

A small number of medical images may be labeled by medical experts while thousands of additional images remain unlabeled.

### Speech Recognition

Large quantities of speech recordings can be collected, but manually transcribing every recording is expensive.

### Text Classification

Semi-supervised learning can improve tasks such as:

* Sentiment analysis
* Spam detection
* Document classification
* Topic classification

### Face and Object Recognition

A small labeled image dataset can be combined with a much larger collection of unlabeled images.

### Fraud Detection

Labeled fraudulent transactions may be limited, while large amounts of unlabeled transaction data are available.

### Handwriting Recognition

A small set of manually labeled handwriting samples can be combined with a large collection of unlabeled samples.

---

# Supervised vs Unsupervised vs Semi-Supervised

| Aspect             | Supervised Learning                        | Unsupervised Learning                | Semi-Supervised Learning                                                  |
| ------------------ | ------------------------------------------ | ------------------------------------ | ------------------------------------------------------------------------- |
| **Labeled Data**   | Required                                   | Not required                         | Small amount                                                              |
| **Unlabeled Data** | Usually not required                       | Required                             | Large amount                                                              |
| **Main Goal**      | Predict known targets                      | Discover hidden patterns             | Learn using both labeled and unlabeled data                               |
| **Common Tasks**   | Classification, Regression                 | Clustering, Dimensionality Reduction | Classification, Recognition, Prediction                                   |
| **Human Labeling** | Usually high                               | Not required                         | Reduced                                                                   |
| **Example**        | Cat/Dog classification with labeled images | Group similar images                 | Cat/Dog classification using few labeled images and many unlabeled images |

---

# Simple Comparison

The difference can be remembered using the following diagram:

```text
                 Machine Learning
                       │
        ┌──────────────┼──────────────┐
        │              │              │
   Supervised     Unsupervised   Semi-Supervised
        │              │              │
 Labeled Data     Unlabeled Data   Labeled +
                                  Unlabeled Data
        │              │              │
        ↓              ↓              ↓
   Prediction       Pattern       Prediction using
                    Discovery     limited labels
```

---

# Key Idea

The easiest way to remember semi-supervised learning is:

> **Semi-supervised learning uses a small amount of labeled data to help a model learn from a much larger amount of unlabeled data.**

```text
Small Labeled Data
        +
Large Unlabeled Data
        ↓
Semi-Supervised Learning
        ↓
Better Learned Representation
        ↓
Improved Prediction
```

---

# Summary

**Semi-Supervised Machine Learning** combines **supervised learning** and **unsupervised learning**.

It is especially useful when:

* Labeled data is limited.
* Unlabeled data is abundant.
* Manual labeling is expensive or time-consuming.
* The unlabeled data is relevant to the prediction task.

The major techniques include:

* **Self-Training / Pseudo-Labeling**
* **Consistency Regularization**
* **Graph-Based Learning**
* **Generative Methods**

In short:

> **Supervised learning learns from labeled data, unsupervised learning discovers patterns from unlabeled data, and semi-supervised learning uses both to make better use of limited labeled information.**
