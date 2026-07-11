# 🏡 End-to-End Data Intelligence System using Machine Learning and Large Language Models

## Overview

This project was developed as part of an Applied AI & Machine Learning capstone project. The goal was to build a complete end-to-end machine learning pipeline using the Ames Housing Dataset.

The project begins with data acquisition and preprocessing, followed by exploratory data analysis, supervised machine learning, advanced ensemble learning, and finally integrates a Large Language Model (LLM) to generate human-readable explanations for model predictions.

This project demonstrates the complete machine learning lifecycle, from raw data to an explainable AI application.

---

# Project Objectives

The main objectives of this project are:

- Perform data cleaning and preprocessing.
- Explore the dataset using statistical analysis and visualization.
- Build regression and classification models.
- Improve model performance using ensemble learning techniques.
- Optimize models using GridSearchCV.
- Save trained models for future inference.
- Integrate an LLM using the OpenRouter API.
- Generate structured explanations for machine learning predictions.
- Validate LLM responses using JSON Schema.

---

# Dataset

**Dataset:** Ames Housing Dataset

The dataset contains information about residential properties, including:

- Lot Area
- Neighborhood
- Overall Quality
- Living Area
- Garage Information
- Basement Features
- Sale Price

The target variable used throughout the project is **SalePrice**.

---

# Project Structure

```text
capstone-ames-data-intelligence/
│
├── README.md
├── requirements.txt
│
├── Part-1/
│   ├── Part1_Data_Acquisition_Cleaning_EDA.ipynb
│   ├── README.md
│   └── cleaned_data.csv
│
├── Part-2/
│   ├── Part2_Supervised_Machine_Learning.ipynb
│   ├── README.md
│   └── cleaned_data.csv
│
├── Part-3/
│   ├── Part3_Advanced_Modeling_Ensembles.ipynb
│   ├── README.md
│   ├── cleaned_data.csv
│   ├── best_model.pkl
│   └── feature_columns.pkl
│
└── Part-4/
    ├── Part4_LLM_Powered_Prediction_Explanation.ipynb
    ├── README.md
    ├── cleaned_data.csv
    ├── best_model.pkl
    ├── feature_columns.pkl
    └── prediction_summary.csv
```

---

# Project Workflow

```
Raw Dataset
      ↓
Data Cleaning
      ↓
Exploratory Data Analysis
      ↓
Feature Engineering
      ↓
Regression Models
      ↓
Classification Models
      ↓
Ensemble Learning
      ↓
Hyperparameter Tuning
      ↓
Model Serialization
      ↓
LLM Integration
      ↓
Prediction Explanation
```

---

# Part 1 – Data Acquisition, Cleaning and Exploratory Data Analysis

The first part focuses on preparing the dataset for machine learning.

### Tasks Completed

- Dataset acquisition
- Missing value analysis
- Median imputation
- Duplicate removal
- Data type correction
- Memory optimization
- Descriptive statistics
- Skewness analysis
- Outlier detection
- Correlation analysis
- Data visualization
- Grouped aggregation

### Output

- `cleaned_data.csv`

---

# Part 2 – Supervised Machine Learning

In this part, regression and classification models were developed using the cleaned dataset.

### Models

- Linear Regression
- Ridge Regression
- Logistic Regression

### Evaluation Metrics

- Mean Squared Error (MSE)
- R² Score
- Accuracy
- Precision
- Recall
- F1 Score
- ROC Curve
- ROC-AUC

Additional experiments include:

- Decision Threshold Analysis
- Regularization Comparison
- Bootstrap Confidence Interval

---

# Part 3 – Advanced Machine Learning

This part focuses on improving prediction performance using ensemble learning techniques.

### Models

- Decision Tree
- Controlled Decision Tree
- Random Forest
- Gradient Boosting

### Additional Tasks

- Feature Importance Analysis
- Feature Ablation Study
- Cross Validation
- Machine Learning Pipeline
- Hyperparameter Tuning
- Learning Curve Analysis
- Model Serialization

### Generated Files

- `best_model.pkl`
- `feature_columns.pkl`

---

# Part 4 – LLM Powered Prediction Explanation

The final part integrates the trained machine learning model with a Large Language Model using the OpenRouter API.

### Features Implemented

- OpenRouter API Integration
- GPT-4.1 Mini
- Prompt Engineering
- JSON Schema Validation
- PII Guardrail
- Temperature Comparison
- Structured Prediction Explanation

For each prediction, the LLM generates:

- Prediction Label
- Confidence Level
- Top Reason
- Second Reason
- Suggested Next Step

The explanations are exported as:

- `prediction_summary.csv`

---

# Technologies Used

### Programming

- Python

### Data Analysis

- Pandas
- NumPy

### Machine Learning

- Scikit-learn
- Joblib

### Visualization

- Matplotlib

### LLM Integration

- OpenRouter API
- GPT-4.1 Mini

### Validation

- JSON Schema
- Regular Expressions

---

# Skills Demonstrated

Through this project, I gained practical experience in:

- Data Cleaning and Preprocessing
- Exploratory Data Analysis
- Feature Engineering
- Regression and Classification
- Ensemble Learning
- Hyperparameter Tuning
- Cross Validation
- Model Serialization
- API Integration
- Prompt Engineering
- Explainable AI
- JSON Validation

---

# Results

The project successfully demonstrates an end-to-end AI workflow.

Some of the key outcomes include:

- Successfully cleaned and prepared the Ames Housing dataset.
- Built and evaluated multiple regression and classification models.
- Improved prediction performance using Random Forest and Gradient Boosting.
- Saved reusable machine learning pipelines.
- Integrated a Large Language Model for prediction explanations.
- Generated structured JSON responses validated using JSON Schema.
- Created human-readable explanations for house price predictions.

---

# Future Improvements

Possible future enhancements include:

- Deploy the project as a Streamlit web application.
- Add support for real-time house price prediction.
- Compare multiple LLM providers.
- Build an interactive dashboard for prediction visualization.
- Containerize the project using Docker.

---

# Conclusion

This project demonstrates the complete machine learning lifecycle, starting from raw data preprocessing and ending with an explainable AI solution powered by a Large Language Model.

By combining traditional machine learning techniques with modern LLM capabilities, the project generates accurate house price predictions along with structured explanations that make the model's decisions easier to understand.

Overall, this project helped strengthen my understanding of data preprocessing, supervised learning, ensemble models, model deployment concepts, API integration, prompt engineering, and explainable AI.
