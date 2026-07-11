# Part 2 – Supervised Machine Learning

## Objective

The objective of this part of the project was to build supervised machine learning models using the cleaned Ames Housing dataset created in Part 1.

Both **regression** and **classification** problems were explored. Regression models were used to predict the actual sale price of a house, while classification models were used to predict whether a house belongs to the above-median or below-median price category.

---

# Dataset

The cleaned dataset generated in Part 1 (`cleaned_data.csv`) was used for model development.

- **Features:** All columns except `SalePrice`
- **Regression Target:** `SalePrice`
- **Classification Target:** Houses with sale price above the median were assigned class **1**, and houses below or equal to the median were assigned class **0**.

---

# Data Preparation

Before training the models, the dataset was preprocessed.

### Feature Encoding

Categorical variables were converted into numerical values.

Two different encoding techniques were used:

- **Ordinal Encoding**
  - Lot Shape

- **One-Hot Encoding**
  - All remaining categorical features

This allowed machine learning models to process categorical information correctly.

---

# Train-Test Split

The dataset was divided into:

- **80% Training Data**
- **20% Testing Data**

The same split was used for both regression and classification models.

For the classification task, stratified sampling was applied to maintain the class distribution in both training and testing datasets.

---

# Feature Scaling

StandardScaler was applied to normalize the numerical features.

The scaler was fitted only on the training data and then applied to both the training and testing datasets to prevent data leakage.

---

# Linear Regression

A Linear Regression model was trained to predict house sale prices.

The model was evaluated using:

- Mean Squared Error (MSE)
- R² Score

The feature coefficients were also analyzed to identify which variables had the strongest influence on house prices.

The three most important features were reported based on the absolute coefficient values.

---

# Ridge Regression

A Ridge Regression model was trained using **alpha = 1.0**.

The model was evaluated using the same metrics as Linear Regression.

The performance of both regression models was compared using:

- Mean Squared Error
- R² Score

This comparison helped understand the effect of L2 regularization on model performance.

---

# Logistic Regression

The regression problem was converted into a binary classification problem by comparing each house price with the median sale price.

The Logistic Regression model was trained using the scaled features.

The class distribution was checked before training.

If class imbalance had been detected, the model would have used `class_weight="balanced"`.

---

# Classification Evaluation

The classification model was evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix
- Classification Report

These metrics provide a detailed understanding of model performance beyond simple accuracy.

---

# ROC Curve and AUC

The Receiver Operating Characteristic (ROC) curve was generated to evaluate classification performance across different decision thresholds.

The Area Under the Curve (AUC) score was also calculated.

A higher AUC indicates better classification performance.

---

# Decision Threshold Analysis

Instead of using the default probability threshold of **0.50**, multiple thresholds were evaluated:

- 0.30
- 0.40
- 0.50
- 0.60
- 0.70

For each threshold, the following metrics were calculated:

- Precision
- Recall
- F1 Score

The threshold with the highest F1 Score was identified as the best decision threshold.

---

# Regularization Experiment

A second Logistic Regression model was trained using stronger regularization (**C = 0.01**).

The performance of both models was compared using:

- Precision
- Recall
- ROC-AUC

This experiment demonstrated the effect of stronger regularization on classification performance.

---

# Bootstrap Confidence Interval

Bootstrap sampling was performed using **500 resamples**.

For each bootstrap sample, the difference in ROC-AUC between the two Logistic Regression models was calculated.

Finally, a **95% confidence interval** was computed.

This analysis helps determine whether the difference between the two models is statistically significant.

---

# Key Learnings

During this part of the project, I learned how to:

- Prepare data for supervised learning.
- Encode categorical variables.
- Apply feature scaling correctly.
- Build Linear Regression and Ridge Regression models.
- Train Logistic Regression models.
- Evaluate regression and classification performance.
- Interpret ROC curves and AUC scores.
- Analyze different classification thresholds.
- Understand the impact of regularization.
- Estimate model uncertainty using bootstrap confidence intervals.

---

# Conclusion

In this part of the project, I successfully developed both regression and classification models using the cleaned housing dataset. Different preprocessing techniques, evaluation metrics, and validation methods were applied to compare model performance. The experiments provided a better understanding of supervised machine learning and prepared the dataset for the more advanced ensemble learning techniques implemented in Part 3.
