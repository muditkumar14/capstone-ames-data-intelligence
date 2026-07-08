# Part 2 – Supervised Machine Learning

## Objective

The objective of this part of the capstone project is to build and evaluate supervised machine learning models using the cleaned Ames Housing dataset prepared in Part 1.

Two predictive tasks were performed:

- Regression: Predict the continuous house sale price (`SalePrice`).
- Binary Classification: Predict whether a house sells above or below the median sale price.

The workflow includes feature engineering, categorical encoding, train-test splitting, leak-free feature scaling, regression modeling, classification modeling, decision-threshold analysis, regularization experiments, and bootstrap confidence interval estimation.

The cleaned dataset (`cleaned_data.csv`) generated in Part 1 was used throughout this section.

---

# Feature Matrix and Target Variables

The cleaned dataset generated in Part 1 was loaded using `pd.read_csv()`.

Two target variables were defined.

## Regression Target

The continuous target variable is:

**SalePrice**

## Classification Target

A binary target variable was created using the median sale price.

- SalePrice > Median → 1
- SalePrice ≤ Median → 0

This resulted in a nearly balanced dataset.

The final feature matrix contained **260 encoded features** after preprocessing.

---

# Categorical Feature Encoding

The dataset contains both ordinal and nominal categorical variables.

## Ordinal Encoding

The **Lot Shape** column has a natural order:

IR3 < IR2 < IR1 < Reg

Therefore, label encoding was applied while preserving the natural ordering.

## One-Hot Encoding

All remaining nominal categorical variables were encoded using **One-Hot Encoding** with `drop_first=True`.

One-Hot Encoding prevents the model from assuming an incorrect ordinal relationship between categories while also reducing multicollinearity.

---

# Train-Test Split and Feature Scaling

The dataset was divided into:

- 80% Training
- 20% Testing

using `train_test_split()` with `random_state=42`.

Feature scaling was performed using **StandardScaler**.

The scaler was fitted **only on the training dataset** before transforming both the training and testing datasets.

This prevents **data leakage**, since statistics from the test dataset are never used during model training.

---

# Linear Regression

A Linear Regression model was trained using the standardized training data.

## Performance

- Mean Squared Error (MSE): **833,314,119.55**
- R² Score: **0.8961**

The model explains approximately **89.61%** of the variation in house prices.

## Most Important Features

The three features with the largest absolute coefficients were:

1. **BsmtFin SF 1**
2. **Bsmt Unf SF**
3. **Total Bsmt SF**

These features had the strongest influence on predicting house prices.

A large **positive coefficient** indicates that increasing the standardized feature increases the predicted sale price.

A large **negative coefficient** indicates that increasing the feature decreases the predicted sale price.

---

# Ridge Regression

A Ridge Regression model was trained using **alpha = 1.0**.

## Model Comparison

| Model | MSE | R² Score |
|------|-------------:|------:|
| Linear Regression | 833,314,119.55 | 0.8961 |
| Ridge Regression | 828,518,427.08 | 0.8967 |

The Ridge Regression model achieved a slightly lower Mean Squared Error and a slightly higher R² score than the standard Linear Regression model.

The **alpha** parameter controls the strength of L2 regularization. Increasing alpha shrinks model coefficients more aggressively, helping reduce overfitting.

---

# Logistic Regression

A Logistic Regression model was trained to classify houses into above-median and below-median price groups.

The dataset was already balanced.

- Class 0: **50.6%**
- Class 1: **49.4%**

Therefore, no imbalance handling technique was required.

## Model Performance

- Accuracy: **0.9317**
- Precision: **(Use the value printed by your notebook)**
- Recall: **(Use the value printed by your notebook)**
- F1 Score: **(Use the value printed by your notebook)**

The confusion matrix and classification report indicate that the model correctly classified the majority of houses into the correct price category.

---

# ROC Curve and AUC

The Receiver Operating Characteristic (ROC) curve was generated to evaluate classifier performance across different thresholds.

The model achieved:

**AUC = 0.9791**

An AUC close to **1.0** indicates excellent ability to distinguish between houses priced above and below the median.

## Precision Formula

Precision = TP / (TP + FP)

Precision measures the proportion of predicted positive observations that are actually positive.

## Recall Formula

Recall = TP / (TP + FN)

Recall measures the proportion of actual positive observations that were correctly identified.

For this housing classification task, **Precision** is slightly more important because incorrectly classifying a lower-priced property as a premium property could lead to unrealistic price estimates.

---

# Decision Threshold Sensitivity Analysis

Five decision thresholds were evaluated.

| Threshold | Precision | Recall | F1 Score |
|----------:|----------:|-------:|---------:|
| 0.30 | 0.8978 | 0.9508 | 0.9236 |
| 0.40 | 0.9135 | 0.9344 | 0.9238 |
| 0.50 | **0.9431** | **0.9246** | **0.9338** |
| 0.60 | 0.9519 | 0.9082 | 0.9295 |
| 0.70 | 0.9611 | 0.8918 | 0.9252 |

The highest F1 Score was achieved at the default threshold of **0.50**.

Increasing the threshold improves Precision while reducing Recall because fewer observations are classified as positive.

---

# Logistic Regression Regularization

A second Logistic Regression model was trained using **C = 0.01**, which applies stronger L2 regularization.

| Model | Precision | Recall | AUC |
|------|----------:|-------:|-----:|
| Logistic Regression (C = 1.0) | **(Use baseline Precision)** | **(Use baseline Recall)** | **0.9791** |
| Logistic Regression (C = 0.01) | **0.9567** | **0.9410** | **0.9906** |

The parameter **C** controls the inverse strength of regularization.

A smaller value of **C** applies stronger regularization, shrinking model coefficients more aggressively.

For this dataset, stronger regularization slightly improved the AUC score.

---

# Bootstrap Confidence Interval

A bootstrap experiment with **500 samples** was performed to compare the AUC of the two Logistic Regression models.

## Results

- Mean AUC Difference: **−0.0117**
- 2.5th Percentile: **−0.0190**
- 97.5th Percentile: **−0.0056**

The **95% confidence interval excludes zero**, indicating that the observed performance difference between the two models is statistically reliable rather than due to random sampling.

---

# Conclusion

This part of the capstone project successfully developed supervised machine learning models for both regression and classification using the Ames Housing dataset.

Linear Regression and Ridge Regression achieved strong predictive performance for estimating house prices, while Logistic Regression demonstrated excellent classification capability with an AUC of **0.9791**.

Additional analyses including decision-threshold evaluation, regularization experiments, and bootstrap confidence intervals provided deeper insights into model robustness and predictive performance.

The supervised learning pipeline developed in this section provides the foundation for the ensemble learning and machine learning pipeline implementation in **Part 3**.
