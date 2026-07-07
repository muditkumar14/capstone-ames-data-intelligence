# Part 2 – Supervised Machine Learning

## Objective

The objective of this part of the capstone project is to build and evaluate supervised machine learning models using the cleaned Ames Housing dataset prepared in Part 1.

Two predictive tasks were performed:

- Regression: Predict the continuous house sale price (`SalePrice`)
- Binary Classification: Predict whether a house sells above or below the median sale price.

The workflow includes feature engineering, categorical encoding, train-test splitting, leak-free feature scaling, regression modeling, classification modeling, threshold analysis, regularization experiments, and bootstrap confidence interval estimation.

The cleaned dataset (`cleaned_data.csv`) generated in Part 1 was used throughout this section.

---

# Feature Matrix and Target Variables

The cleaned dataset generated in Part 1 was loaded using `pd.read_csv()`.

Two target variables were defined.

### Regression Target

The continuous target variable is:

**SalePrice**

### Classification Target

A binary target variable was created using the median sale price.

- SalePrice > Median → 1
- SalePrice ≤ Median → 0

This resulted in a nearly balanced dataset.

The feature matrix contains **260 encoded features** after preprocessing.

---

# Categorical Feature Encoding

The dataset contains both ordinal and nominal categorical variables.

## Ordinal Encoding

The **Lot Shape** column has a natural order:

IR3 < IR2 < IR1 < Reg

Therefore, it was label encoded while preserving the ordering.

## One-Hot Encoding

The remaining categorical columns were encoded using **One-Hot Encoding** with `drop_first=True`.

One-Hot Encoding prevents the model from assuming an incorrect numerical relationship among nominal categories while also avoiding multicollinearity.

After encoding, the dataset contained **260 features**.

---

# Train-Test Split and Feature Scaling

The dataset was divided into:

- 80% Training
- 20% Testing

using `random_state=42`.

Feature scaling was performed using **StandardScaler**.

The scaler was fitted **only on the training dataset** before transforming both training and testing datasets.

This prevents **data leakage** because statistics from the testing data are never used during model training.

---

# Linear Regression

A Linear Regression model was trained using the standardized training data.

## Performance

- Mean Squared Error (MSE): **833,314,119.55**
- R² Score: **0.8961**

The model explains approximately **89.61%** of the variation in house prices.

## Most Important Features

The three largest absolute coefficients were:

1. **BsmtFin SF 1**
2. **Bsmt Unf SF**
3. **Total Bsmt SF**

These features had the strongest influence on predicting house prices.

Positive coefficients indicate that increasing the standardized feature increases the predicted sale price.

Negative coefficients indicate the opposite.

---

# Ridge Regression

Ridge Regression was trained using **alpha = 1.0**.

## Model Comparison

| Model | MSE | R² |
|------|-------------:|------:|
| Linear Regression | 833,314,119.55 | 0.8961 |
| Ridge Regression | 828,518,427.08 | 0.8967 |

The Ridge model produced a slightly lower MSE and a slightly higher R² Score, indicating a small improvement over ordinary Linear Regression.

The alpha parameter controls the strength of L2 Regularization.

Smaller alpha values apply weaker regularization, while larger alpha values shrink coefficients more aggressively to reduce overfitting.

---

# Logistic Regression

A Logistic Regression model was trained to classify houses into above-median and below-median price groups.

The dataset was already balanced:

- Class 0: **50.6%**
- Class 1: **49.4%**

Therefore, no imbalance handling technique was required.

## Model Performance

- Accuracy: **0.9317**
- Precision: **0.9431**
- Recall: **0.9246**
- F1 Score: **0.9338**

The confusion matrix shows that the classifier correctly predicted the majority of observations.

---

# ROC Curve and AUC

The Receiver Operating Characteristic (ROC) Curve was generated to evaluate classifier performance across different decision thresholds.

The model achieved:

**AUC = 0.9791**

An AUC close to 1 indicates excellent discrimination between the two classes.

### Precision

Precision = TP / (TP + FP)

Precision measures how many predicted positive observations are actually positive.

### Recall

Recall = TP / (TP + FN)

Recall measures how many actual positive observations were correctly classified.

For this project, Precision is slightly more important because incorrectly predicting a lower-priced house as a premium property may lead to unrealistic pricing decisions.

---

# Decision Threshold Sensitivity Analysis

Thresholds from **0.30 to 0.70** were evaluated.

| Threshold | Precision | Recall | F1 Score |
|----------:|----------:|-------:|---------:|
| 0.30 | 0.8978 | 0.9508 | 0.9236 |
| 0.40 | 0.9135 | 0.9344 | 0.9238 |
| 0.50 | **0.9431** | **0.9246** | **0.9338** |
| 0.60 | 0.9519 | 0.9082 | 0.9295 |
| 0.70 | 0.9611 | 0.8918 | 0.9252 |

The highest F1 Score was achieved at the default threshold of **0.50**.

Increasing the threshold improves Precision but reduces Recall because fewer observations are classified as positive.

---

# Logistic Regression Regularization

A second Logistic Regression model was trained using **C = 0.01**.

| Model | Precision | Recall | AUC |
|------|----------:|-------:|-----:|
| Logistic Regression (C=1.0) | **Update after fixing variable overwrite** | **Update** | 0.9791 |
| Logistic Regression (C=0.01) | 0.9567 | 0.9410 | 0.9906 |

The parameter **C** controls the inverse strength of regularization.

A smaller C applies stronger L2 Regularization and shrinks model coefficients.

For this dataset, stronger regularization slightly improved the AUC score.

---

# Bootstrap Confidence Interval

A bootstrap experiment with **500 samples** was conducted.

## Results

- Mean AUC Difference: **−0.0117**
- 2.5th Percentile: **−0.0190**
- 97.5th Percentile: **−0.0056**

The **95% confidence interval excludes zero**.

This indicates that the performance difference between the two Logistic Regression models is statistically reliable rather than due to random sampling variation.

---

# Conclusion

This part of the capstone project successfully developed supervised machine learning models for both regression and classification using the Ames Housing dataset.

Linear Regression and Ridge Regression achieved strong predictive performance for house price estimation, while Logistic Regression demonstrated excellent classification capability with an AUC of **0.9791**.

Additional experiments involving threshold analysis, regularization, and bootstrap confidence intervals provided deeper insights into model reliability and predictive performance.

The complete preprocessing and modeling pipeline developed in this section forms the foundation for the ensemble learning and machine learning pipeline implementation in **Part 3**.
