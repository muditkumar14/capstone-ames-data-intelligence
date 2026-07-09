# Part 3 – Advanced Modeling: Ensembles, Hyperparameter Tuning and Machine Learning Pipeline

## Overview

In this part of the project, I built advanced machine learning models to improve prediction performance and create a complete, production-ready workflow.

Unlike Part 2, which focused on basic supervised learning models, this section explores ensemble learning techniques, compares multiple classifiers using cross-validation, performs hyperparameter tuning using GridSearchCV, and saves the best-performing model for future use.

The complete workflow follows a structured machine learning pipeline, making the model reproducible, reusable, and suitable for deployment.

---

# Objectives

The main objectives of this part were to:

- Build Decision Tree and Ensemble models
- Compare multiple classification algorithms
- Evaluate models using ROC-AUC and Cross Validation
- Tune Random Forest using GridSearchCV
- Analyze feature importance
- Perform feature ablation
- Study model performance using a manual learning curve
- Save the best model using Joblib
- Reload the saved model and make predictions

---

# Dataset

The project uses the cleaned Ames Housing dataset prepared in **Part 1**.

The classification target was defined as:

- **1** → House price above the median
- **0** → House price equal to or below the median

The same preprocessing pipeline from Part 2 was reused throughout this project.

---

# Workflow

```text
Cleaned Dataset
        │
        ▼
Feature Encoding
        │
        ▼
Train-Test Split
        │
        ▼
Standard Scaling
        │
        ▼
Decision Tree Models
        │
        ▼
Random Forest
        │
        ▼
Gradient Boosting
        │
        ▼
Feature Importance
        │
        ▼
Feature Ablation
        │
        ▼
Cross Validation
        │
        ▼
GridSearchCV
        │
        ▼
Learning Curve
        │
        ▼
Save Best Model
        │
        ▼
Reload & Predict
```

---

# 1. Decision Tree Baseline

A default `DecisionTreeClassifier` was trained using the scaled training dataset.

## Performance

- **Training Accuracy:** **1.0000**
- **Testing Accuracy:** **0.8788**

The model achieved perfect training accuracy but significantly lower testing accuracy, indicating clear overfitting.

Decision Trees are considered **high-variance models** because they greedily split the training data until it is perfectly classified, which often causes them to memorize the training data instead of learning generalized patterns.

---

# 2. Controlled Decision Tree

A second Decision Tree model was trained using:

- `max_depth = 5`
- `min_samples_split = 20`

## Performance

- **Training Accuracy:** **0.9270**
- **Testing Accuracy:** **0.8976**
- **Test ROC-AUC:** **0.9573**

Compared to the default tree, the controlled model reduced overfitting and achieved better generalization.

### Hyperparameter Explanation

### max_depth

Limits the maximum depth of the tree, reducing variance and helping prevent overfitting.

### min_samples_split

Prevents nodes containing only a few observations from being split, reducing sensitivity to noisy data.

The controlled tree reduced the train-test performance gap from **0.1212** to **0.0294**, demonstrating improved generalization.

---

# 3. Gini vs Entropy

Two Decision Tree models were compared using different impurity measures.

- Gini Impurity
- Entropy

### Gini Formula

\[
Gini = 1-\sum p_i^2
\]

### Entropy Formula

\[
Entropy = -\sum p_i\log_2(p_i)
\]

A node with **Gini = 0** means every observation belongs to the same class.

Both impurity measures produced very similar performance, with Entropy performing slightly better.

---

# 4. Random Forest Classifier

Random Forest combines multiple Decision Trees into a single ensemble model.

The model was trained using:

- 100 Trees
- Maximum Depth = 10
- Random State = 42

## Performance

- **Training Accuracy:** **0.9893**
- **Testing Accuracy:** **0.9283**
- **ROC-AUC:** **0.9806**

Random Forest significantly reduced overfitting while improving predictive performance compared to a single Decision Tree.

---

# Feature Importance

Random Forest calculates feature importance by measuring the average reduction in Gini Impurity contributed by each feature across all trees.

Unlike Linear Regression coefficients, feature importance values measure predictive contribution rather than indicating positive or negative relationships.

The five most important features identified were:

- Full Bath
- Gr Liv Area
- Overall Qual
- Garage Area
- Garage Cars

These variables contributed most to predicting whether a house belonged to the above-median price category.

---

# Bagging (Bootstrap Aggregation)

Random Forest uses **Bagging**.

Each Decision Tree is trained using a random bootstrap sample of the training data.

At every split, only a random subset of features is considered.

This randomness reduces variance, improves robustness, and makes Random Forest significantly more stable than a single Decision Tree.

---

# 5. Gradient Boosting

Gradient Boosting builds Decision Trees sequentially, where each new tree attempts to correct errors made by previous trees.

The model was trained using:

- 100 Estimators
- Learning Rate = 0.1

## Performance

- **Training Accuracy:** **0.9770**
- **Testing Accuracy:** **0.9266**
- **ROC-AUC:** **0.9822**

Gradient Boosting achieved the highest overall predictive performance among all evaluated models.

---

# 6. Feature Ablation Study

The five least important features identified by the Random Forest model were removed.

A second Random Forest model was trained using the reduced feature set.

## Results

| Model | ROC-AUC |
|------|---------:|
| Full Random Forest | **0.9806** |
| Reduced Random Forest | **0.9814** |

The reduced model achieved a slightly higher ROC-AUC score, indicating that the removed features contributed very little useful information and may have introduced minor noise.

Removing these features simplifies the model while maintaining predictive performance.

---

# 7. Cross Validation

Five-fold Stratified Cross Validation was performed using **ROC-AUC**.

| Model | Mean ROC-AUC | Standard Deviation |
|------|-------------:|-------------------:|
| Logistic Regression | **0.9648** | **0.0051** |
| Decision Tree | **0.9406** | **0.0060** |
| Random Forest | **0.9814** | **0.0034** |
| Gradient Boosting | **0.9825** | **0.0053** |

Cross Validation provides a more reliable estimate of model performance because every observation is used for both training and validation across multiple folds.

---

# 8. Hyperparameter Tuning

GridSearchCV was used to identify the best Random Forest configuration.

Pipeline components:

- SimpleImputer(strategy="median")
- StandardScaler()
- RandomForestClassifier(random_state=42)

Parameter grid:

- n_estimators = [50, 100, 200]
- max_depth = [5, 10, None]
- min_samples_leaf = [1, 5]

Parameter combinations evaluated:

**18**

Total models trained using 5-fold Cross Validation:

**90**

## Best Parameters

```python
{
    'randomforestclassifier__max_depth': None,
    'randomforestclassifier__min_samples_leaf': 1,
    'randomforestclassifier__n_estimators': 200
}
```

### Best Cross Validation ROC-AUC

**0.9822**

### Grid Search vs Randomized Search

Grid Search evaluates every possible parameter combination and guarantees the best solution within the specified search space.

Randomized Search evaluates only randomly selected combinations, making it computationally faster for larger search spaces.

---

# 9. Manual Learning Curve

The best pipeline was retrained using progressively larger portions of the training data.

| Training Fraction | Training ROC-AUC | Testing ROC-AUC |
|------------------:|-----------------:|----------------:|
| 20% | **1.0000** | **0.9730** |
| 40% | **1.0000** | **0.9776** |
| 60% | **1.0000** | **0.9809** |
| 80% | **1.0000** | **0.9810** |
| 100% | **1.0000** | **0.9806** |

The testing ROC-AUC improved steadily as more training data became available before stabilizing near the full dataset.

This suggests the model has reached a point where additional data provides only marginal improvement, indicating that performance is beginning to plateau.

---

# 10. Model Serialization

The best-performing pipeline was saved using Joblib.

```python
joblib.dump(best_pipeline, "best_model.pkl")
```

The saved model was successfully reloaded.

```python
loaded_model = joblib.load("best_model.pkl")
```

Predictions were generated on two unseen samples to verify that the serialized model can be reused without retraining.

---

# Final Model Comparison

| Model | 5-Fold Mean ROC-AUC | Std ROC-AUC | Test ROC-AUC |
|------|--------------------:|------------:|-------------:|
| Logistic Regression | **0.9648** | **0.0051** | **0.9654** |
| Decision Tree | **0.9406** | **0.0060** | **0.9573** |
| Random Forest | **0.9814** | **0.0034** | **0.9806** |
| Gradient Boosting | **0.9825** | **0.0053** | **0.9822** |

---

# Final Recommendation

Among all evaluated models, **Gradient Boosting Classifier** achieved the strongest overall performance with the highest cross-validation ROC-AUC and the best test-set ROC-AUC.

Although Random Forest also performed exceptionally well, Gradient Boosting demonstrated slightly better generalization while maintaining high predictive accuracy.

For deployment, Gradient Boosting is recommended because it provides the best balance between performance, robustness, and reliability.

---

# Conclusion

This part of the project successfully implemented advanced ensemble learning techniques, systematic hyperparameter tuning, feature importance analysis, feature ablation, cross-validation, manual learning curve analysis, and model serialization.

The final machine learning pipeline is fully reproducible, reusable, and suitable for real-world predictive applications.

Overall, ensemble learning significantly outperformed a single Decision Tree, demonstrating the effectiveness of combining multiple models to improve predictive performance and reduce overfitting.
