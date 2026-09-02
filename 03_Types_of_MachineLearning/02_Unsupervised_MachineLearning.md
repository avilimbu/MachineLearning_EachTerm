# Unsupervised Machine Learning

Unsupervised Machine Learning is a type of machine learning where algorithms learn patterns directly from **unlabeled data**, without any predefined "correct answers" to guide them.

Instead of predicting a target variable, the algorithm attempts to **discover hidden structures and patterns** within the data. These may include groups of similar items, simplified representations, unusual observations, or relationships between variables.

---

## What is Unsupervised Machine Learning?

The main difference between supervised and unsupervised learning is the presence of **labels**.

### Supervised Learning

In supervised learning, the model is trained using both **input data and corresponding labels**.

For example:

```text
Input Data              Label
────────────────────────────────
Image of a cat    →     Cat
Image of a dog    →     Dog
```

The model learns the relationship between the input and the known output.

### Unsupervised Learning

In unsupervised learning, the model receives **only input data** without predefined labels.

For example:

```text
Customer Data
     ↓
Customer 1
Customer 2
Customer 3
Customer 4
Customer 5
     ↓
Algorithm discovers patterns
     ↓
Customer Groups
```

The algorithm determines the underlying patterns or structures by itself.

---

## Main Goals of Unsupervised Learning

Typical goals of unsupervised learning include:

* **Clustering** — Grouping similar data points together.
* **Dimensionality Reduction** — Reducing the number of features while preserving important information.
* **Anomaly Detection** — Identifying unusual or suspicious observations.
* **Association Rule Learning** — Discovering relationships between variables or items.

---

# 1. Clustering

**Clustering** is an unsupervised learning technique that groups similar data points together.

The objective is to make data points within the same cluster more similar to each other than to data points in other clusters.

### Example

Suppose we have customer information based on:

* Age
* Annual income
* Spending behavior

The algorithm might automatically discover groups such as:

```text
              Customer Data
                    ↓
              Clustering
                    ↓
       ┌────────────┼────────────┐
       ↓            ↓            ↓
   Cluster 1    Cluster 2    Cluster 3
       ↓            ↓            ↓
   Low Income   High Income   Medium Income
   Low Spending High Spending Medium Spending
```

No customer group labels are provided beforehand. The algorithm discovers the groups based on similarities in the data.

### Applications

Clustering is commonly used for:

* Customer segmentation
* Image segmentation
* Document grouping
* Market analysis
* Social network analysis
* Recommendation systems

### Common Clustering Algorithms

#### K-Means

**K-Means** divides the dataset into `K` clusters.

The algorithm attempts to minimize the distance between data points and their corresponding cluster centers, known as **centroids**.

```text
Data Points
     ↓
Choose K
     ↓
Initialize Centroids
     ↓
Assign Points to Nearest Centroid
     ↓
Update Centroids
     ↓
Repeat Until Convergence
```

#### Hierarchical Clustering

Hierarchical clustering creates a hierarchy of clusters.

It can be performed using:

* **Agglomerative clustering** — Starts with individual data points and merges them.
* **Divisive clustering** — Starts with one large cluster and repeatedly divides it.

The resulting hierarchy can be visualized using a **dendrogram**.

#### DBSCAN

**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** groups points based on their density.

It is particularly useful when:

* Clusters have irregular shapes.
* The number of clusters is unknown.
* The dataset contains noise or outliers.

### Types of Clustering

#### Hard Clustering

Each data point belongs to exactly **one cluster**.

```text
Point A → Cluster 1
Point B → Cluster 2
Point C → Cluster 1
```

#### Soft Clustering

A data point can have a probability of belonging to multiple clusters.

For example:

```text
Point A
   ↓
Cluster 1 → 70%
Cluster 2 → 30%
```

---

# 2. Dimensionality Reduction

**Dimensionality reduction** is the process of reducing the number of features in a dataset while preserving as much important information as possible.

For example, a dataset might contain:

```text
100 Features
     ↓
Dimensionality Reduction
     ↓
10 Important Features
```

### Why Use Dimensionality Reduction?

High-dimensional datasets can:

* Be difficult to visualize.
* Require more computational resources.
* Contain redundant information.
* Contain irrelevant or noisy features.
* Make machine learning models more complex.

Reducing dimensionality can make the data easier to analyze and visualize.

### Common Techniques

#### PCA — Principal Component Analysis

**PCA** transforms the original features into a smaller number of new features called **principal components**.

The principal components are selected to preserve as much variance in the data as possible.

For example:

```text
Original Dataset
      ↓
50 Features
      ↓
      PCA
      ↓
5 Principal Components
```

#### t-SNE

**t-SNE (t-distributed Stochastic Neighbor Embedding)** is a nonlinear dimensionality-reduction technique commonly used to visualize high-dimensional data in two or three dimensions.

```text
High-Dimensional Data
        ↓
       t-SNE
        ↓
      2D / 3D
 Visualization
```

#### UMAP

**UMAP (Uniform Manifold Approximation and Projection)** is another nonlinear dimensionality-reduction technique that is often used for visualization and exploratory data analysis.

#### Autoencoders

**Autoencoders** are neural networks that can learn compact representations of data.

They consist mainly of:

```text
Input
  ↓
Encoder
  ↓
Latent Representation
  ↓
Decoder
  ↓
Reconstructed Input
```

### Applications

Dimensionality reduction can be used for:

* Data visualization
* Image compression
* Signal processing
* Feature extraction
* Noise reduction
* Preprocessing before clustering
* Exploratory data analysis

---

# 3. Anomaly Detection

**Anomaly detection** is the process of identifying data points that are significantly different from the majority of observations.

An anomaly is also commonly called an:

* Outlier
* Abnormal observation
* Unusual point

### Basic Idea

The algorithm learns what **normal data** generally looks like and identifies observations that do not fit that pattern.

```text
Normal Data
 ● ● ● ● ●
 ● ● ● ● ●
  ● ● ● ●

             X
          Anomaly
```

### Common Approaches

#### Statistical Methods

Statistical techniques assume that the data follows a particular distribution.

Observations with extremely low probability may be considered anomalies.

#### Distance and Density-Based Methods

These methods identify points that are:

* Far away from other observations.
* Located in low-density regions.
* Isolated from their neighbors.

Common algorithms include:

* Isolation Forest
* Local Outlier Factor (LOF)

#### Reconstruction-Based Methods

Autoencoders can learn to reconstruct normal observations.

If an observation produces a high reconstruction error, it may be considered an anomaly.

```text
Normal Data
     ↓
Autoencoder
     ↓
Low Reconstruction Error
     ↓
Normal


Anomalous Data
     ↓
Autoencoder
     ↓
High Reconstruction Error
     ↓
Anomaly
```

### Applications

Anomaly detection is used for:

* Fraud detection
* Network intrusion detection
* Industrial fault detection
* System monitoring
* Sensor fault detection
* Detecting unusual transactions
* Identifying unusual medical cases

---

# 4. Association Rule Learning

**Association Rule Learning** is an unsupervised learning technique used to discover interesting relationships between items or variables in large datasets.

It is particularly common in **transactional datasets**.

### Example

Suppose a supermarket analyzes customer purchases and discovers:

```text
Customers who buy:
Bread + Butter

are often likely to buy:
Milk
```

This can be represented as an association rule:

```text
Bread + Butter → Milk
```

The algorithm discovers these relationships from the data rather than being given the rules beforehand.

---

## Important Metrics

### 1. Support

**Support** measures how frequently an itemset appears in the dataset.

```text
Support(X) =
Number of transactions containing X
────────────────────────────────────
Total number of transactions
```

A high support means the itemset appears frequently.

---

### 2. Confidence

**Confidence** measures how often `Y` occurs when `X` occurs.

```text
Confidence(X → Y) =
Support(X ∪ Y)
────────────────
Support(X)
```

For example:

```text
Bread → Milk
```

Confidence tells us how often customers who buy bread also buy milk.

---

### 3. Lift

**Lift** measures how much more frequently `X` and `Y` occur together compared with what would be expected if they were independent.

```text
Lift(X → Y) =
Confidence(X → Y)
────────────────
Support(Y)
```

A lift greater than `1` can indicate a positive association between the items.

---

## Common Association Rule Algorithms

### Apriori

**Apriori** is a popular algorithm for finding frequent itemsets and generating association rules.

The general process is:

```text
Transaction Dataset
        ↓
Find Frequent Itemsets
        ↓
Generate Candidate Itemsets
        ↓
Calculate Support
        ↓
Generate Association Rules
        ↓
Calculate Confidence & Lift
```

### FP-Growth

**FP-Growth (Frequent Pattern Growth)** is another algorithm for discovering frequent itemsets.

It uses an **FP-tree** structure to efficiently find frequent patterns without generating as many candidate itemsets as Apriori.

---

## Applications of Association Rule Learning

Association rule learning is commonly used for:

* Market basket analysis
* Product recommendation
* Retail analysis
* Recommender systems
* Customer behavior analysis
* Healthcare pattern discovery
* Log and event analysis

---

# Unsupervised Learning vs Supervised Learning

| Aspect              | Supervised Learning        | Unsupervised Learning                                                      |
| ------------------- | -------------------------- | -------------------------------------------------------------------------- |
| **Training Data**   | Labeled data               | Unlabeled data                                                             |
| **Target Variable** | Present                    | Usually absent                                                             |
| **Main Goal**       | Predict an output          | Discover hidden patterns                                                   |
| **Common Tasks**    | Regression, Classification | Clustering, Dimensionality Reduction, Anomaly Detection, Association Rules |
| **Example**         | Predict house price        | Group similar customers                                                    |
| **Output**          | Known target type          | Discovered structure or pattern                                            |

---

# Simple Example

Consider a customer dataset containing:

```text
Customer | Age | Income | Spending Score
-----------------------------------------
A        | 22  | 25K    | 80
B        | 25  | 28K    | 75
C        | 45  | 80K    | 20
D        | 48  | 85K    | 15
```

There are no predefined customer categories.

Using **K-Means clustering**, the algorithm may discover:

```text
Customer Data
      ↓
    K-Means
      ↓
 ┌────┴─────┐
 ↓          ↓
Cluster 1   Cluster 2
 ↓          ↓
A, B        C, D
```

The algorithm has discovered groups based on similarities in age, income, and spending behavior.

---

# Key Difference

The easiest way to remember unsupervised learning is:

> **Supervised Learning:** Learn from labeled examples to make predictions.

> **Unsupervised Learning:** Learn from unlabeled data to discover patterns and structure.

```text
                 Machine Learning
                       │
             ┌─────────┴─────────┐
             │                   │
        Supervised          Unsupervised
             │                   │
       Labeled Data         Unlabeled Data
             │                   │
      ┌──────┴──────┐     ┌──────┼──────────────┐
      │             │     │      │       │       │
 Regression   Classification  Clustering  PCA  Anomaly  Association
```

---

# Summary

Unsupervised Machine Learning works with **unlabeled data** and attempts to discover meaningful patterns or structures without predefined target values.

The major areas of unsupervised learning are:

* **Clustering** → Groups similar data points.
* **Dimensionality Reduction** → Reduces the number of features while preserving important information.
* **Anomaly Detection** → Identifies unusual or abnormal observations.
* **Association Rule Learning** → Discovers relationships between items or variables.

These techniques are widely used in **customer segmentation, recommendation systems, fraud detection, data visualization, market basket analysis, image processing, and exploratory data analysis**.
