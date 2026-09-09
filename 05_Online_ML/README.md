# Online Machine Learning

## What is Online Machine Learning?

**Online Machine Learning** is a machine learning paradigm where a model updates its parameters **incrementally** as new data arrives. Instead of collecting the entire dataset and retraining the model from scratch, the model learns from **one sample or a small mini-batch at a time**.

Online learning is also known as **incremental learning** or **streaming learning**.

The general learning process is:

```text
New Data → Prediction → Receive Label → Model Update → New Data → ...
```

This makes online learning particularly useful for systems where data is continuously generated and the underlying patterns may change over time.

---

## Batch Learning vs Online Learning

In **Batch Learning**, the model is trained using a complete dataset or large batches of data. After deployment, the model generally remains unchanged until it is retrained.

In **Online Learning**, the model continuously receives new data and updates itself incrementally.

```text
Batch Learning:

Dataset → Train Model → Deploy Model
                    ↓
              Periodic Retraining


Online Learning:

Data 1 → Update Model
Data 2 → Update Model
Data 3 → Update Model
Data 4 → Update Model
   ↓
Continuous Learning
```

---

## When to Use Online Learning

Online learning is useful when one or more of the following conditions apply:

### 1. High-Velocity Data

When data is generated continuously and at a high speed.

Examples:

* Website clicks
* Financial transactions
* Sensor readings
* Application logs
* User interactions

### 2. Changing Environments

Online learning can adapt to **concept drift**, where the relationship between input data and the target changes over time.

Examples:

* Fraud detection
* Advertisement click-through prediction
* News recommendation
* Recommendation systems

### 3. Limited Memory

When the complete dataset cannot fit into memory, the model can process data incrementally instead of loading everything at once.

### 4. Real-Time Personalization

Online learning can continuously adapt predictions according to new user behavior.

Examples:

* Product recommendations
* Content recommendations
* Personalized search results

### 5. Expensive Retraining

If retraining a model from scratch is computationally expensive or takes too much time, incremental updates can be more efficient.

---

## How Online Learning Works

A typical online learning process consists of the following steps:

### Step 1: Initialize the Model

Start with a new model or an existing model that has been trained using historical data.

### Step 2: Receive New Data

A new observation arrives:

```text
(xₜ, yₜ)
```

where:

* `xₜ` = input features
* `yₜ` = actual target

### Step 3: Make a Prediction

The model predicts the output:

```text
ŷₜ = model.predict(xₜ)
```

### Step 4: Receive the Actual Label

Once the actual outcome becomes available, the prediction can be evaluated.

### Step 5: Update the Model

The model learns from the new observation:

```text
model.partial_fit(xₜ, yₜ)
```

or an equivalent incremental learning operation.

### Step 6: Repeat

The process continues whenever new data arrives.

```text
Initialize Model
      ↓
Receive Data
      ↓
Make Prediction
      ↓
Receive Actual Result
      ↓
Update Model
      ↓
Monitor Performance
      ↓
Receive Next Data
      ↺
```

---

## Common Algorithms

Several machine learning algorithms can be adapted for online learning.

### Stochastic Gradient Descent (SGD)

SGD updates model parameters using individual samples or small batches.

Examples in Scikit-learn include:

```python
from sklearn.linear_model import SGDClassifier

model = SGDClassifier(loss="log_loss")
```

### Perceptron

The Perceptron can learn incrementally and update its parameters when new training examples arrive.

### Naive Bayes

Some Naive Bayes implementations support incremental learning through `partial_fit()`.

### FTRL

**Follow-The-Regularized-Leader (FTRL)** is commonly used for large-scale online optimization problems such as advertising and recommendation systems.

### Streaming Decision Trees and Ensembles

Specialized streaming algorithms can continuously update tree-based models as new observations arrive.

---

## Online Learning with Scikit-Learn

Some Scikit-learn estimators provide the `partial_fit()` method for incremental learning.

Example:

```python
from sklearn.linear_model import SGDClassifier

model = SGDClassifier(loss="log_loss", random_state=42)

classes = [0, 1]

for X_batch, y_batch in data_stream:

    model.partial_fit(
        X_batch,
        y_batch,
        classes=classes
    )
```

The important difference is that the model is **not retrained from scratch** for every batch.

Instead:

```text
Batch 1 → Model Update
Batch 2 → Model Update
Batch 3 → Model Update
Batch 4 → Model Update
```

---

## Learning Rate

The **learning rate (`η`)** determines how strongly new observations influence the model's parameters.

### High Learning Rate

A high learning rate can cause large parameter updates.

```text
New Data
   ↓
Large Update
   ↓
Fast Adaptation
   ↓
Possible Instability
```

### Low Learning Rate

A low learning rate produces smaller updates.

```text
New Data
   ↓
Small Update
   ↓
Stable Learning
   ↓
Slower Adaptation
```

Therefore, the learning rate should be selected carefully.

### Common Learning Rate Strategies

#### Fixed Learning Rate

A constant learning rate is used throughout training.

#### Decaying Learning Rate

The learning rate gradually decreases as more observations are processed.

A common form is:

```text
ηₜ ∝ 1 / √t
```

#### Adaptive Learning Rate

Algorithms such as **AdaGrad, Adam, and FTRL** can adjust learning rates based on the learning process.

---

## Out-of-Core Learning

**Out-of-core learning** refers to training a model when the complete dataset cannot fit into RAM.

Instead of loading the entire dataset:

```text
Large Dataset
     ↓
┌───────────┐
│ Chunk 1   │ → Model Update
├───────────┤
│ Chunk 2   │ → Model Update
├───────────┤
│ Chunk 3   │ → Model Update
├───────────┤
│ Chunk 4   │ → Model Update
└───────────┘
```

Only a portion of the dataset is loaded and processed at a time.

Online learning naturally fits this approach because the model can process data incrementally.

### Example

```python
for chunk in pd.read_csv(
    "large_dataset.csv",
    chunksize=1000
):

    X = chunk.drop("target", axis=1)
    y = chunk["target"]

    model.partial_fit(X, y)
```

This allows machine learning models to work with datasets that are too large to load into memory at once.

---

## Online Learning vs Out-of-Core Learning

These concepts are related but not identical.

| Aspect             | Online Learning               | Out-of-Core Learning                        |
| ------------------ | ----------------------------- | ------------------------------------------- |
| Main idea          | Continuously update the model | Process data that does not fit in RAM       |
| Data source        | Usually a stream              | Usually files, databases, or large datasets |
| Model updates      | Incremental                   | Can be incremental or batch-based           |
| Memory requirement | Usually low                   | Low compared with loading everything        |
| Main purpose       | Adapt to new data             | Handle datasets larger than memory          |

**Online learning focuses on how the model learns, while out-of-core learning focuses on how large datasets are processed.**

---

## Concept Drift

One important reason to use online learning is **concept drift**.

Concept drift occurs when the statistical properties or relationships within the data change over time.

For example:

```text
Historical Data
      ↓
Model learns old pattern
      ↓
Environment changes
      ↓
New Data has different pattern
      ↓
Online Model adapts
```

Examples include:

* Changing customer preferences
* New fraud patterns
* Changing user behavior
* Changing market conditions
* Seasonal trends

Online learning can continuously update the model to respond to these changes.

---

## Monitoring Online Models

Because an online model continuously changes, its performance should be monitored.

Useful metrics include:

* Accuracy
* Precision
* Recall
* F1-score
* Log loss
* ROC-AUC
* Mean Absolute Error (MAE)
* Mean Squared Error (MSE)

### Rolling Metrics

Instead of evaluating the model only once, performance can be measured over a moving window.

```text
Recent 100 predictions
        ↓
Calculate Metric
        ↓
Monitor Performance
        ↓
Next 100 predictions
```

This helps identify performance degradation and concept drift.

---

## Advantages

### 1. Continuous Adaptation

The model can learn from new information as it becomes available.

### 2. Lower Memory Requirement

The complete dataset does not necessarily need to be stored in memory.

### 3. Fast Updates

Small updates can be performed without completely retraining the model.

### 4. Suitable for Streaming Data

Online learning is well suited to continuously generated data.

### 5. Handles Concept Drift

The model can adapt when patterns in the environment change.

### 6. Efficient for Large Datasets

It can process datasets incrementally instead of loading everything at once.

---

## Disadvantages and Risks

### 1. Sensitivity to Noisy Data

A poor-quality observation can influence the model immediately.

### 2. Catastrophic Forgetting

The model may gradually lose important historical patterns when it focuses heavily on recent data.

### 3. Reproducibility Challenges

The final model can depend on the **order and timing of observations**, making exact reproduction more difficult.

### 4. Engineering Complexity

Production systems may require:

* Data pipelines
* Monitoring
* Drift detection
* Checkpointing
* Rollback mechanisms
* Delayed-label handling

### 5. Delayed Labels

In some applications, the correct label may not be available immediately.

For example:

```text
Transaction
    ↓
Prediction
    ↓
Wait for outcome
    ↓
Actual Label
    ↓
Model Update
```

### 6. Model Instability

If updates are too aggressive, the model may react excessively to temporary patterns or noisy observations.

---

## Batch Learning vs Online Learning

| Aspect                        | Batch Learning                             | Online Learning                               |
| ----------------------------- | ------------------------------------------ | --------------------------------------------- |
| **Data usage**                | Uses the complete dataset or large batches | Uses individual samples or small mini-batches |
| **Model updates**             | Periodic retraining                        | Continuous/incremental updates                |
| **Adaptability**              | Relatively low                             | High                                          |
| **Memory**                    | Can require substantial memory/storage     | Usually lower memory requirement              |
| **Data processing**           | Offline                                    | Streaming/incremental                         |
| **Response to concept drift** | Requires retraining                        | Can adapt continuously                        |
| **Retraining cost**           | Potentially high                           | Smaller incremental updates                   |
| **Reproducibility**           | Generally easier                           | More difficult because order can matter       |
| **Implementation**            | Relatively simpler                         | More complex                                  |
| **Best suited for**           | Static or periodically updated datasets    | Streaming and changing data                   |

---

## Online Learning Applications

Online learning can be applied to many real-world problems.

### Fraud Detection

Financial transactions can be evaluated as they occur, allowing the model to adapt to new fraud patterns.

### Recommendation Systems

Recommendations can be updated based on recent user interactions.

### Advertisement Systems

Models can learn from continuously changing click and conversion behavior.

### IoT and Sensors

Sensor data can arrive continuously from devices and be processed incrementally.

### Spam Detection

The model can adapt as new spam patterns emerge.

### Real-Time Personalization

Systems can continuously update predictions based on recent user behavior.

---

## Online Learning with River

**River** is a Python machine learning library specifically designed for **online machine learning and streaming data**.

A simplified example:

```python
from river import linear_model

model = linear_model.LogisticRegression()

for x, y in data_stream:

    prediction = model.predict_one(x)

    model.learn_one(x, y)
```

The important methods are:

```text
predict_one()
     ↓
Make prediction

learn_one()
     ↓
Update model
```

River is particularly useful when working with continuous data streams.

---

## Practical Online Learning Pipeline

A production-style online learning system can be represented as:

```text
        Data Stream
             ↓
      Data Validation
             ↓
       Preprocessing
             ↓
          Model
             ↓
        Prediction
             ↓
       Actual Label
             ↓
      Model Update
             ↓
    Performance Monitor
             ↓
       Drift Detection
             ↓
       Model Checkpoint
             ↺
```

A robust system should also consider:

* Missing values
* Outliers
* Data validation
* Delayed labels
* Concept drift
* Model versioning
* Monitoring
* Checkpointing
* Rollback

---

## Key Takeaways

* **Online Learning** updates a model incrementally as new data arrives.
* It is also called **incremental learning** or **streaming learning**.
* It is useful for **high-velocity and continuously changing data**.
* `partial_fit()` can be used for incremental learning with supported Scikit-learn estimators.
* **River** is a Python library designed specifically for online and streaming machine learning.
* Online learning can help models adapt to **concept drift**.
* **Out-of-core learning** allows datasets larger than RAM to be processed in chunks.
* Learning rate selection is important for stable and effective updates.
* Continuous monitoring is essential because the model changes over time.
* Online learning provides adaptability but introduces additional engineering and reproducibility challenges.

---

## Summary

**Online Machine Learning** is a learning approach in which a machine learning model continuously updates itself as new observations become available.

Unlike batch learning, where a model is periodically retrained using a fixed dataset, online learning follows an incremental process:

```text
New Data
   ↓
Prediction
   ↓
Actual Outcome
   ↓
Model Update
   ↓
Monitor Performance
   ↓
New Data
   ↺
```

This makes online learning particularly valuable for **streaming systems, real-time applications, large-scale datasets, personalization, fraud detection, IoT, and environments affected by concept drift**.
