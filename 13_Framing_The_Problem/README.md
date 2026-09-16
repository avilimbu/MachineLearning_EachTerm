
# Framing the Problem

## What is Problem Framing?

**Problem Framing** is the process of understanding a real-world problem and converting it into a clear, well-defined Machine Learning problem.

Before building a Machine Learning model, we need to understand:

- What problem are we trying to solve?
- Why is the problem important?
- What data do we need?
- What type of ML problem is it?
- How will we measure success?
- Should we use Batch Learning or Online Learning?
- What assumptions do we need to check?

> **Important:** A successful Machine Learning project starts with a clearly defined problem, not with choosing an algorithm.

---

# 1. Business Problem to ML Problem

## 1.1 What is a Business Problem?

A **Business Problem** is a real-world challenge faced by an organization, company, or individual that needs to be solved.

Examples:

- A bank wants to detect fraudulent transactions.
- A company wants to predict customer churn.
- A hospital wants to identify patients at risk of a disease.
- A real estate company wants to estimate house prices.
- A school wants to predict student performance.

### Example

A company is losing customers every month.

**Business Problem:**

> Why are customers leaving the company, and how can we reduce customer churn?

This is a business problem because it focuses on a real-world business goal.

---

## 1.2 What is an ML Problem?

An **ML Problem** is a business problem converted into a task that a Machine Learning model can solve using data.

For example:

**Business Problem:**

> Reduce customer churn.

**ML Problem:**

> Build a classification model that predicts whether a customer will leave the company based on customer information and usage history.

The ML model learns patterns from historical data and uses them to make predictions about new customers.

---

## 1.3 Steps to Convert a Business Problem into an ML Problem

### Step 1: Understand the Business Objective

Identify what the business wants to achieve.

Example:

> Reduce customer churn by identifying customers who are likely to leave.

### Step 2: Define the ML Objective

Convert the business objective into a prediction or learning task.

Example:

> Predict whether a customer will churn or stay.

### Step 3: Identify the Target Variable

The **Target Variable** is the value that the model is expected to predict.

Example:

```text
Customer Churn = Yes or No
```

Here:

- Target Variable: `Churn`
- Possible values: `Yes`, `No`

### Step 4: Identify the Features

**Features** are the input variables used by the model to make predictions.

Example:

| Feature | Description |
|---|---|
| Customer Age | Age of the customer |
| Monthly Charges | Monthly bill |
| Contract Type | Type of subscription |
| Tenure | How long the customer has been with the company |
| Support Calls | Number of customer support calls |

### Step 5: Define the Prediction

The model should predict:

```text
Input: Customer information
Output: Churn = Yes or No
```

### Step 6: Define Success Criteria

Decide how to measure whether the ML solution is useful.

Example:

- Improve recall for customers who are likely to churn.
- Reduce customer churn.
- Reduce the cost of retaining customers.

> Business success and ML model performance are related, but they are not always the same.

---

## 1.4 Business Problem vs ML Problem

| Business Problem | ML Problem |
|---|---|
| Reduce customer churn | Predict customer churn |
| Detect fraud | Classify transactions as fraudulent or legitimate |
| Predict house prices | Build a regression model |
| Recommend products | Build a recommendation system |
| Identify spam emails | Classify emails as spam or not spam |
| Predict student performance | Predict student scores or grades |

---

## 1.5 Example: House Price Prediction

### Business Problem

A real estate company wants to estimate house prices.

### ML Problem

Build a regression model that predicts the selling price of a house using historical housing data.

### Features

```text
Area
Number of Bedrooms
Location
House Age
Number of Floors
```

### Target

```text
House Price
```

### ML Type

```text
Supervised Learning
Regression
```

---

# 2. Types of Problem

After understanding the business problem, we need to identify the type of Machine Learning problem.

The main types are:

1. Supervised Learning
2. Unsupervised Learning
3. Semi-Supervised Learning
4. Self-Supervised Learning
5. Reinforcement Learning

In traditional ML project framing, the most common categories are supervised learning, unsupervised learning, and reinforcement learning.

---

## 2.1 Supervised Learning

**Supervised Learning** is a type of Machine Learning where the model learns from labeled data.

Labeled data contains:

- Input features (`X`)
- Target/output (`y`)

The model learns the relationship between inputs and outputs.

### Example

| Hours Studied | Attendance | Result |
|---|---|---|
| 2 | 60% | Fail |
| 5 | 85% | Pass |
| 8 | 95% | Pass |

The model learns from the input features and the known result.

### Main Types

#### A. Classification

Classification predicts a category or class.

Examples:

- Spam or Not Spam
- Fraud or Legitimate
- Pass or Fail
- Disease or No Disease

Output:

```text
Class Label
```

#### B. Regression

Regression predicts a continuous numerical value.

Examples:

- House Price
- Temperature
- Salary
- GDP
- Sales Revenue

Output:

```text
Numerical Value
```

### Classification vs Regression

| Classification | Regression |
|---|---|
| Predicts categories | Predicts numerical values |
| Output is a class label | Output is a continuous number |
| Spam detection | House price prediction |
| Fraud detection | Salary prediction |
| Pass/Fail prediction | Temperature prediction |

---

## 2.2 Unsupervised Learning

**Unsupervised Learning** is a type of Machine Learning where the model learns patterns from data without target labels.

The dataset contains input features but no known target variable.

### Example

A company has customer information but does not know customer groups.

The model can discover groups of similar customers.

### Main Types

#### A. Clustering

Groups similar data points together.

Examples:

- Customer segmentation
- Grouping similar documents
- Grouping similar products

Algorithms:

```text
K-Means
Hierarchical Clustering
DBSCAN
```

#### B. Dimensionality Reduction

Reduces the number of features while trying to preserve useful information.

Examples:

- Data visualization
- Feature compression
- Noise reduction

Algorithms:

```text
PCA
t-SNE
UMAP
```

---

## 2.3 Semi-Supervised Learning

**Semi-Supervised Learning** uses a combination of labeled and unlabeled data.

Example:

```text
100 labeled images
10,000 unlabeled images
```

The model uses both types of data to learn.

### Why is it useful?

Labeling data can be expensive and time-consuming.

Examples:

- Image classification
- Speech recognition
- Document classification

---

## 2.4 Self-Supervised Learning

**Self-Supervised Learning** creates learning signals from the data itself instead of requiring manually created labels for every example.

### Example

In language modeling:

```text
Input: Machine Learning is
Target: interesting
```

The model learns to predict missing or next tokens from the text.

Self-supervised learning is widely used in modern language models and representation learning.

---

## 2.5 Reinforcement Learning

**Reinforcement Learning** is a type of Machine Learning where an agent learns by interacting with an environment.

The agent receives rewards or penalties based on its actions.

### Main Components

| Component | Meaning |
|---|---|
| Agent | Learner or decision-maker |
| Environment | World in which the agent operates |
| Action | Decision taken by the agent |
| Reward | Feedback received |
| State | Current situation |

### Example

A robot learns to navigate a room.

```text
Agent → Takes Action → Environment
Agent ← Receives Reward ← Environment
```

The agent learns which actions produce better long-term rewards.

---

## 2.6 How to Identify the Problem Type?

Ask these questions:

### Question 1

Do we have labeled target data?

- Yes → Supervised Learning
- No → Consider Unsupervised Learning or other approaches

### Question 2

Is the target a category?

- Yes → Classification

### Question 3

Is the target a numerical value?

- Yes → Regression

### Question 4

Do we want to discover hidden groups?

- Yes → Clustering

### Question 5

Does an agent learn through rewards?

- Yes → Reinforcement Learning

---

# 3. Current Solutions

Before building a Machine Learning model, we should understand how the problem is currently solved.

This helps us determine whether ML is actually needed.

## 3.1 What are Current Solutions?

**Current Solutions** are the methods, systems, tools, or processes already used to solve a problem.

They may include:

- Manual work
- Rule-based systems
- Existing software
- Human experts
- Statistical models
- Existing ML models

---

## 3.2 Why Do We Need to Study Current Solutions?

### 1. Understand the Existing Process

We need to know how the problem is solved today.

### 2. Identify Limitations

Find out what is slow, expensive, inaccurate, or difficult.

### 3. Compare ML with Existing Methods

Machine Learning is not automatically better than a simple solution.

### 4. Avoid Unnecessary Complexity

If a simple rule solves the problem well, an ML model may not be necessary.

---

## 3.3 Example: Spam Email Detection

### Current Solution 1: Manual Checking

A person reads every email and identifies spam.

**Limitations:**

- Time-consuming
- Difficult to scale
- Human errors

### Current Solution 2: Rule-Based System

The system blocks emails containing certain words.

Example:

```python
if "win money" in email:
    mark_as_spam()
```

**Limitations:**

- Rules may be too simple.
- Spammers can change their wording.
- Many rules may be required.

### Proposed ML Solution

Train a classification model using historical emails.

```text
Email Text → ML Model → Spam / Not Spam
```

The model can learn patterns from examples rather than relying only on manually written rules.

---

## 3.4 Current Solution Comparison

| Solution | Advantages | Limitations |
|---|---|---|
| Manual Work | Simple to start | Slow and difficult to scale |
| Rule-Based System | Easy to understand | Limited flexibility |
| Statistical Model | Can capture relationships | Requires suitable assumptions |
| Existing ML Model | May already solve the task | May need adaptation |
| New ML Model | Can be customized | Requires data, development, and maintenance |

---

## 3.5 Baseline Solution

A **Baseline** is a simple method used as a reference for comparing ML models.

Examples:

- Predict the majority class.
- Predict the average house price.
- Use a simple rule.
- Use an existing model.

### Example: Classification Baseline

Suppose a dataset contains:

```text
90% Not Spam
10% Spam
```

A model that always predicts `Not Spam` achieves 90% accuracy.

However, it may fail to detect spam.

This shows why we need appropriate evaluation metrics.

### Important Principle

> A complex ML model should provide meaningful improvement over a reasonable baseline.

---

# 4. Getting Data

Data is the foundation of Machine Learning.

A model learns patterns from data, so the quality and relevance of the data are extremely important.

## 4.1 What is Data Collection?

**Data Collection** is the process of gathering information required to solve the ML problem.

The data should be relevant to the business objective and the target variable.

---

## 4.2 Sources of Data

### 1. Existing Databases

Data stored in databases.

Examples:

```text
MySQL
PostgreSQL
MongoDB
```

### 2. APIs

Data collected from external services.

Examples:

- Weather API
- Financial API
- Social media API

### 3. Files

Common file formats:

```text
CSV
Excel
JSON
Parquet
```

### 4. Web Scraping

Collecting publicly available information from websites, where permitted.

### 5. Sensors and IoT Devices

Examples:

- Temperature sensors
- GPS devices
- Smart watches
- Industrial sensors

### 6. Surveys and Forms

Collecting data from users or customers.

### 7. Public Datasets

Examples:

- World Bank datasets
- UCI Machine Learning Repository
- Kaggle datasets
- Hugging Face datasets

---

## 4.3 Questions to Ask Before Getting Data

### Question 1: What data do we need?

Identify the features and target variable.

Example:

For house price prediction:

```text
Area
Bedrooms
Location
House Age
House Price
```

### Question 2: Where can we get the data?

Possible sources:

```text
Database
API
CSV file
Public dataset
Company records
```

### Question 3: Is the data relevant?

The data should represent the actual problem.

### Question 4: Is the data sufficient?

We need enough examples to learn useful patterns.

### Question 5: Is the data reliable?

Check for:

- Missing values
- Incorrect values
- Duplicate records
- Outliers
- Inconsistent formats

### Question 6: Is the data legally and ethically usable?

Consider:

- Privacy
- Consent
- Licensing
- Data protection
- Bias
- Sensitive information

---

## 4.4 Data Quality

Good data should be:

| Quality | Meaning |
|---|---|
| Relevant | Related to the problem |
| Accurate | Contains correct information |
| Complete | Has fewer missing values |
| Consistent | Uses consistent formats |
| Representative | Reflects the real population |
| Timely | Appropriate for the prediction period |
| Reliable | Comes from a trustworthy source |

---

## 4.5 Data Leakage

**Data Leakage** occurs when information that would not be available at prediction time is used to train the model.

This can make model performance appear better than it really is.

### Example

Predict whether a customer will cancel a subscription.

Feature:

```text
Cancellation Confirmation Date
```

This feature reveals that the customer has already canceled.

Using it to predict churn would be leakage.

### How to Avoid Data Leakage

- Use only information available at prediction time.
- Split data before preprocessing when appropriate.
- Fit preprocessing steps only on training data.
- Avoid using future information.
- Check features for hidden target information.

---

## 4.6 Example: Getting Data for GDP Prediction

### Problem

Predict the upcoming-year GDP of South Asian countries.

### Possible Data Sources

- World Bank World Development Indicators
- National statistical agencies
- Central banks
- Other reliable economic databases

### Possible Features

```text
GDP Growth
Inflation
Population
Exports
Imports
Foreign Direct Investment
```

### Target

```text
Upcoming-Year GDP
```

### Data Collection Steps

```text
1. Define the countries.
2. Define the time period.
3. Select the indicators.
4. Download the data.
5. Combine the datasets.
6. Clean missing values.
7. Prepare the target variable.
8. Split the data.
```

---

# 5. Metrics to Measure

> **Note:** The correct term is generally **Metrics to Measure**, not "Matrices to Measure." A matrix is a mathematical arrangement of values, while a metric is a measurement used to evaluate performance.

## 5.1 What are ML Evaluation Metrics?

**Evaluation Metrics** are measurements used to determine how well a Machine Learning model performs.

They help us compare:

- Different models
- Model predictions and actual values
- Model performance against a baseline
- ML performance against business goals

---

## 5.2 Why Do We Need Metrics?

Accuracy alone is not always sufficient.

Example:

A fraud detection dataset contains:

```text
99% Legitimate Transactions
1% Fraudulent Transactions
```

A model that predicts every transaction as legitimate may achieve 99% accuracy.

But it detects zero fraud cases.

Therefore, we need appropriate metrics.

---

## 5.3 Metrics for Classification

Classification predicts categories.

### A. Accuracy

Accuracy measures the proportion of correct predictions.

\[
Accuracy = \frac{Correct\ Predictions}{Total\ Predictions}
\]

Using confusion matrix terms:

\[
Accuracy = \frac{TP + TN}{TP + TN + FP + FN}
\]

Where:

- TP = True Positive
- TN = True Negative
- FP = False Positive
- FN = False Negative

### When to Use?

Accuracy is useful when classes are reasonably balanced and the costs of errors are similar.

---

### B. Precision

Precision measures how many predicted positive cases are actually positive.

\[
Precision = \frac{TP}{TP + FP}
\]

Example:

Out of 100 emails predicted as spam, 80 are actually spam.

```text
Precision = 80 / 100 = 80%
```

### When is Precision Important?

When false positives are costly.

Example:

- Legitimate email incorrectly marked as spam.
- Legitimate transaction incorrectly blocked.

---

### C. Recall

Recall measures how many actual positive cases are correctly identified.

\[
Recall = \frac{TP}{TP + FN}
\]

Example:

There are 100 actual fraud cases, and the model detects 90.

```text
Recall = 90 / 100 = 90%
```

### When is Recall Important?

When missing a positive case is costly.

Examples:

- Fraud detection
- Disease screening
- Safety monitoring

---

### D. F1-Score

F1-score is the harmonic mean of precision and recall.

\[
F1 = 2 \times \frac{Precision \times Recall}{Precision + Recall}
\]

It is useful when we want a balance between precision and recall.

---

### E. Confusion Matrix

A **Confusion Matrix** is a table that compares actual labels with predicted labels.

| | Predicted Positive | Predicted Negative |
|---|---|---|
| Actual Positive | TP | FN |
| Actual Negative | FP | TN |

Example:

```text
TP = Correctly predicted positive
TN = Correctly predicted negative
FP = Incorrectly predicted positive
FN = Incorrectly predicted negative
```

---

## 5.4 Metrics for Regression

Regression predicts numerical values.

### A. MAE — Mean Absolute Error

MAE measures the average absolute difference between actual and predicted values.

\[
MAE = \frac{1}{n}\sum_{i=1}^{n}|y_i-\hat{y}_i|
\]

Where:

- \(y_i\) = Actual value
- \(\hat{y}_i\) = Predicted value
- \(n\) = Number of observations

Example:

```text
Actual:    100, 200, 300
Predicted: 110, 190, 330
```

Absolute errors:

```text
10, 10, 30
```

```text
MAE = (10 + 10 + 30) / 3
MAE = 16.67
```

---

### B. MSE — Mean Squared Error

MSE calculates the average squared error.

\[
MSE = \frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
\]

Large errors receive more weight because errors are squared.

---

### C. RMSE — Root Mean Squared Error

RMSE is the square root of MSE.

\[
RMSE = \sqrt{MSE}
\]

RMSE is expressed in the same units as the target variable.

Example:

If the target is house price in dollars, RMSE is also measured in dollars.

---

### D. R² Score

R² measures how much of the variation in the target is explained by the model relative to a mean-prediction baseline.

\[
R^2 = 1 - \frac{SS_{res}}{SS_{tot}}
\]

Where:

- \(SS_{res}\) = Residual sum of squares
- \(SS_{tot}\) = Total sum of squares

A higher R² can indicate better fit, but it should not be used alone.

---

## 5.5 Choosing the Right Metric

| Problem | Possible Metrics |
|---|---|
| Balanced Classification | Accuracy, F1-score |
| Spam Detection | Precision, Recall, F1-score |
| Fraud Detection | Recall, Precision, PR-AUC |
| Regression | MAE, MSE, RMSE, R² |
| House Price Prediction | MAE, RMSE, R² |
| Imbalanced Classification | Precision, Recall, F1-score, PR-AUC |

> Choose metrics based on the actual business cost of false positives, false negatives, and other errors.

---

## 5.6 Define the Metric Before Training

Example:

```text
Business Goal:
Reduce missed fraudulent transactions.

ML Metric:
Recall.

Reason:
Missing fraud cases is costly.
```

This makes the evaluation process clear before model training.

---

# 6. Online vs Batch?

After understanding the problem and data, decide how the model will learn.

The two common learning approaches are:

1. Batch Learning
2. Online Learning

---

## 6.1 Batch Learning

**Batch Learning**, also called Offline Learning, trains a model using a fixed dataset.

The model is trained on available data and deployed.

When new data arrives, the model is usually retrained periodically.

### Workflow

```text
Collect Data
     ↓
Train Model
     ↓
Evaluate Model
     ↓
Deploy Model
     ↓
Collect New Data
     ↓
Retrain Later
```

### Example

A company trains a customer churn model every month using the latest customer data.

### Advantages

- Simple to manage
- Works well with historical datasets
- Suitable for periodic retraining
- Easy to reproduce training experiments

### Limitations

- May not adapt immediately to new data
- Retraining can require time and computing resources
- Model may become outdated if patterns change quickly

---

## 6.2 Online Learning

**Online Learning** updates a model incrementally as new data arrives.

The model can learn from individual examples or small batches.

### Workflow

```text
New Data Arrives
      ↓
Model Makes Prediction
      ↓
Model Updates
      ↓
Next Data Arrives
      ↓
Repeat
```

### Example

A fraud detection system updates its model as new labeled transactions become available.

### Advantages

- Can adapt to changing patterns
- Useful for streaming data
- Can process data incrementally
- May require less memory than training on all historical data at once

### Limitations

- Sensitive to noisy data
- Requires monitoring
- Can be affected by concept drift
- Updates need careful management

---

## 6.3 Batch Learning vs Online Learning

| Batch Learning | Online Learning |
|---|---|
| Trains on a fixed dataset | Updates incrementally |
| Retraining is periodic | Learning can happen continuously |
| Suitable for static data | Suitable for streaming data |
| Easier to reproduce | Requires monitoring |
| May adapt slowly | Can adapt faster |
| Example: Monthly churn model | Example: Streaming fraud model |

---

## 6.4 How to Choose?

Ask these questions:

### Question 1

Does new data arrive continuously?

- Yes → Consider Online Learning.
- No → Batch Learning may be suitable.

### Question 2

Do patterns change quickly?

- Yes → Online Learning may be useful.
- No → Batch Learning may be sufficient.

### Question 3

Is retraining periodically acceptable?

- Yes → Batch Learning may work well.
- No → Consider incremental updates.

### Question 4

Are there enough resources to update the model safely?

Online learning requires monitoring and careful handling of updates.

---

## 6.5 Example: GDP Prediction

Suppose we want to predict GDP for South Asian countries.

GDP data is usually released periodically rather than continuously.

A reasonable approach may be:

```text
Collect historical economic data
          ↓
Train model
          ↓
Evaluate model
          ↓
Predict upcoming GDP
          ↓
Update data when new economic reports arrive
          ↓
Retrain periodically
```

This is an example of a batch-oriented workflow.

The final choice should depend on data availability, update frequency, and project requirements.

---

# 7. Check Assumptions

Before training and deploying a Machine Learning model, we need to check the assumptions behind the problem, data, and evaluation process.

**Assumptions** are beliefs or conditions we expect to be true.

If assumptions are incorrect, model performance may suffer.

---

## 7.1 Why Check Assumptions?

Assumptions help us identify:

- Whether the problem is suitable for ML
- Whether the data is useful
- Whether the target can be predicted
- Whether the features are available
- Whether the evaluation is realistic
- Whether the model can work in the real world

---

## 7.2 Business Assumptions

### Assumption 1: The Problem is Important

Example:

> Predicting customer churn will help the business improve customer retention.

We should verify whether churn prediction actually supports useful business decisions.

### Assumption 2: ML is Necessary

Ask:

> Can a simple rule or existing system solve the problem?

If yes, compare that approach with ML.

### Assumption 3: Predictions Can Lead to Action

Example:

If the model predicts a customer may churn, the company should have an appropriate retention strategy.

A prediction is useful only when it supports an action or decision.

---

## 7.3 Data Assumptions

### Assumption 1: Historical Data Represents Future Data

Machine Learning often assumes that training data is reasonably representative of future data.

This may fail when:

- Customer behavior changes
- Economic conditions change
- New products are introduced
- Data collection methods change

### Assumption 2: Data is Relevant

Features should contain useful information for the target.

### Assumption 3: Data is Sufficient

The dataset should contain enough examples to learn meaningful patterns.

### Assumption 4: Data is Reliable

Check:

```text
Missing Values
Duplicates
Incorrect Values
Outliers
Inconsistent Formats
```

### Assumption 5: Target is Available

For supervised learning, we need target labels for training.

---

## 7.4 Feature Assumptions

### Assumption 1: Features are Available at Prediction Time

Example:

When predicting house prices before a sale, we should not use the final selling price as an input feature.

### Assumption 2: Features Contain Useful Information

Some features may not help the model.

### Assumption 3: Features Do Not Leak the Target

Avoid features that reveal the answer.

### Assumption 4: Features are Properly Represented

Categorical and numerical data may need different preprocessing.

Example:

```text
Gender → Encoding
Age → Numerical feature
City → Encoding
```

---

## 7.5 ML Assumptions

Some ML algorithms rely on specific assumptions.

### Example: Linear Regression

Linear Regression assumes a linear relationship between predictors and the target, along with other modeling conditions.

Important considerations include:

- Linearity
- Independence of errors
- Constant error variance for standard inference
- Residual behavior
- Multicollinearity among predictors

Not every assumption applies equally to every algorithm.

### Example: K-Means Clustering

K-Means works by assigning points to clusters around centroids.

It is most suitable when clusters are reasonably represented by their centroids and the chosen distance measure is meaningful.

---

## 7.6 Evaluation Assumptions

### Assumption 1: Train and Test Data are Properly Separated

The test set should represent unseen data.

### Assumption 2: No Data Leakage

Information from the test set should not influence training.

### Assumption 3: Evaluation Metric Matches the Goal

Example:

For fraud detection, accuracy alone may be misleading.

### Assumption 4: Test Data Represents Real-World Use

If the model will predict future data, a time-based split may be more realistic than a random split.

---

## 7.7 Deployment Assumptions

Before deploying a model, check:

- Is the model fast enough?
- Is the required data available?
- Can the model handle missing values?
- Can the model be monitored?
- Can it be retrained?
- Is it fair and safe for the intended use?
- Is the prediction useful to the business?

---

# Complete Problem Framing Workflow

The following workflow summarizes the entire process.

```text
1. Understand the Business Problem
              ↓
2. Convert Business Problem into ML Problem
              ↓
3. Identify the Type of ML Problem
              ↓
4. Study Current Solutions
              ↓
5. Define Features and Target
              ↓
6. Collect Relevant Data
              ↓
7. Check Data Quality
              ↓
8. Define Evaluation Metrics
              ↓
9. Choose Batch or Online Learning
              ↓
10. Check Assumptions
              ↓
11. Train and Evaluate the Model
              ↓
12. Deploy and Monitor
```

---

# Practical Example: Customer Churn Prediction

## Step 1: Business Problem

A company wants to reduce customer churn.

## Step 2: ML Problem

Predict whether a customer will leave the company.

## Step 3: Type of Problem

```text
Supervised Learning
Classification
Binary Classification
```

## Step 4: Current Solution

The company may currently use manual analysis or simple rules.

## Step 5: Getting Data

Possible data:

```text
Customer Age
Monthly Charges
Contract Type
Tenure
Support Calls
Churn Label
```

## Step 6: Metrics

Possible metrics:

```text
Precision
Recall
F1-score
PR-AUC
```

The chosen metric depends on the cost of missed churners and unnecessary retention actions.

## Step 7: Online vs Batch

If customer data is updated periodically, batch learning may be suitable.

If the model must learn incrementally from streaming data, online learning may be considered.

## Step 8: Check Assumptions

- Historical churn patterns are useful for future predictions.
- Features are available before the customer leaves.
- The data does not contain leakage.
- The evaluation reflects real-world performance.
- The business can take action on predictions.

---

# Problem Framing Checklist

Use this checklist before starting an ML project.

- [ ] Define the business problem.
- [ ] Identify the business objective.
- [ ] Convert the business problem into an ML problem.
- [ ] Identify the target variable.
- [ ] Identify the input features.
- [ ] Determine the type of ML problem.
- [ ] Study current solutions.
- [ ] Establish a baseline.
- [ ] Find relevant data sources.
- [ ] Check data quality.
- [ ] Check for data leakage.
- [ ] Define evaluation metrics.
- [ ] Choose Batch or Online Learning.
- [ ] Check business assumptions.
- [ ] Check data assumptions.
- [ ] Check ML assumptions.
- [ ] Plan model evaluation.
- [ ] Plan deployment and monitoring.

---

# Key Takeaways

1. **Problem Framing** is the first important step in an ML project.
2. A business problem must be converted into a clear ML problem.
3. Identify whether the problem is classification, regression, clustering, or another ML task.
4. Understand current solutions before building a new model.
5. Data must be relevant, reliable, and representative.
6. Choose evaluation metrics based on the actual objective.
7. Batch Learning and Online Learning are different ways to train or update models.
8. Check assumptions before trusting model predictions.
9. A complex model is not always better than a simple baseline.
10. A successful ML project solves a real problem and provides useful results.

---

# Important Terms

| Term | Meaning |
|---|---|
| Business Problem | Real-world challenge to solve |
| ML Problem | Business problem converted into an ML task |
| Feature | Input variable used by the model |
| Target Variable | Output the model predicts |
| Classification | Predicting categories |
| Regression | Predicting numerical values |
| Clustering | Grouping similar data |
| Baseline | Simple reference solution |
| Evaluation Metric | Measurement of model performance |
| Batch Learning | Training on a fixed dataset |
| Online Learning | Incremental model updates |
| Data Leakage | Unintended use of information unavailable at prediction time |
| Assumption | Condition expected to be true |

---

## Final Thought

> **Frame the problem correctly before solving it.**

A good Machine Learning engineer does not begin by asking:

> Which algorithm should I use?

Instead, they ask:

> What problem am I solving, what data do I have, and how will I know whether my solution is useful?