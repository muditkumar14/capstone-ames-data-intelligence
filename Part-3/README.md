# Part 3 – Advanced Modeling: Ensemble Learning, Hyperparameter Tuning and Machine Learning Pipeline

## Objective

The objective of this part of the project was to improve the performance of the machine learning models developed in Part 2 by using advanced ensemble learning techniques. Different tree-based models were trained and compared, hyperparameters were optimized using GridSearchCV, and the final model was saved for reuse in the next part of the project.

The cleaned dataset generated in Part 1 was used throughout this notebook.

---

# Dataset

The project uses the cleaned Ames Housing dataset.

- **Input Features:** All columns except `SalePrice`
- **Target Variable:** Houses with sale prices above the median were assigned class **1**, while the remaining houses were assigned class **0**.

Before training the models, categorical variables were encoded and the features were standardized using `StandardScaler`.

---

# Decision Tree Baseline

A Decision Tree classifier was first trained using the default parameters.

The training and testing accuracy were compared to check whether the model was overfitting.

Since the training accuracy was much higher than the testing accuracy, the model showed signs of overfitting.

---

# Controlled Decision Tree

To reduce overfitting, another Decision Tree model was trained using:

- Maximum Depth = 5
- Minimum Samples Split = 20

The performance of both Decision Tree models was compared using:

- Training Accuracy
- Testing Accuracy
- ROC-AUC Score

Reducing the tree depth improved the model's ability to generalize to unseen data.

---

# Gini vs Entropy Comparison

Two Decision Tree models were trained using different splitting criteria.

- Gini Impurity
- Entropy

The testing accuracy of both models was compared to determine whether one criterion performed better than the other.

Both approaches produced very similar results.

---

# Random Forest Classifier

A Random Forest model was trained using:

- 100 Trees
- Maximum Depth = 10

The model was evaluated using:

- Training Accuracy
- Testing Accuracy
- ROC-AUC Score

Random Forest performed better than a single Decision Tree because it combines predictions from multiple trees and reduces overfitting.

---

# Feature Importance

Feature importance scores were extracted from the Random Forest model.

The five most important features were identified and visualized using a bar chart.

This analysis helps understand which variables contribute the most to the prediction.

---

# Gradient Boosting

A Gradient Boosting classifier was trained using:

- 100 Estimators
- Learning Rate = 0.1

Unlike Random Forest, Gradient Boosting builds trees sequentially, where each tree tries to correct the mistakes made by the previous one.

The model was evaluated using:

- Training Accuracy
- Testing Accuracy
- ROC-AUC Score

---

# Feature Ablation Study

The five least important features identified by the Random Forest model were removed from the dataset.

A new Random Forest model was trained using the reduced feature set.

The ROC-AUC scores of both models were compared to understand whether those features contributed meaningful information.

---

# Cross Validation

Five-fold Stratified Cross Validation was performed for four different models:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

The mean ROC-AUC and standard deviation were calculated for each model.

Cross-validation provides a more reliable estimate of model performance because every observation is used for both training and validation.

---

# Machine Learning Pipeline

A Scikit-learn Pipeline was created using:

- SimpleImputer
- StandardScaler
- RandomForestClassifier

Using a pipeline keeps the preprocessing and model training steps together, making the workflow easier to reuse.

---

# Hyperparameter Tuning

GridSearchCV was used to find the best Random Forest hyperparameters.

The following parameters were tuned:

- Number of Trees
- Maximum Depth
- Minimum Samples per Leaf

The best parameter combination was selected using five-fold cross-validation with ROC-AUC as the evaluation metric.

---

# Manual Learning Curve

The best pipeline was trained using different portions of the training dataset.

Training fractions:

- 20%
- 40%
- 60%
- 80%
- 100%

For each fraction, both the training ROC-AUC and testing ROC-AUC were calculated.

This analysis helps understand whether the model benefits from additional training data.

---

# Model Serialization

The best-performing pipeline was saved using Joblib.

Two files were generated:

- `best_model.pkl`
- `feature_columns.pkl`

The saved model was then loaded again and tested on sample data to confirm that it can be reused without retraining.

The feature column file ensures that future predictions use exactly the same feature order as the training data.

---

# Final Model Comparison

The following models were compared:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

The comparison includes:

- Five-Fold Mean ROC-AUC
- Five-Fold Standard Deviation
- Test ROC-AUC

This makes it easy to identify the best-performing model.

---

# Key Learnings

During this part of the project, I learned how to:

- Build ensemble learning models.
- Compare different Decision Tree configurations.
- Understand Gini and Entropy criteria.
- Use Random Forest feature importance.
- Perform feature ablation.
- Apply cross-validation correctly.
- Tune model hyperparameters using GridSearchCV.
- Build reusable machine learning pipelines.
- Save and reload trained models using Joblib.

---

# Conclusion

In this part of the project, I successfully implemented several advanced machine learning techniques to improve prediction performance. Ensemble models such as Random Forest and Gradient Boosting produced better results than a single Decision Tree. Cross-validation and GridSearchCV helped identify the most reliable model, while model serialization made it possible to reuse the trained pipeline in Part 4 without retraining.
