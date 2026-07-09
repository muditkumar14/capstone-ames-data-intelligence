# 🏠 Ames Housing Data Intelligence – End-to-End Machine Learning Capstone

## Overview

This repository contains an end-to-end Machine Learning capstone project built using the **Ames Housing Dataset**. The project demonstrates the complete machine learning workflow, beginning with data preprocessing and exploratory analysis, progressing through supervised learning models, and concluding with advanced ensemble techniques, hyperparameter tuning, and model deployment.

The primary objective is to predict house prices and classify houses based on whether their sale price is above or below the median while following machine learning best practices.

This project was developed using **Python** and the **Scikit-learn** ecosystem.

---

# 📂 Repository Structure

```
capstone-ames-data-intelligence/
│
├── Part-1/
│   ├── Part1.ipynb
│   └── README.md
│
├── Part-2/
│   ├── Part2.ipynb
│   └── README.md
│
├── Part-3/
│   ├── Part3.ipynb
│   ├── README.md
│   └── best_model.pkl
│
├── cleaned_data.csv
├── requirements.txt
└── README.md
```

---

# 📊 Dataset

The project uses the **Ames Housing Dataset**, which contains detailed information about residential properties sold in Ames, Iowa.

The dataset includes:

- Property characteristics
- Construction details
- Neighborhood information
- Basement and garage information
- Lot dimensions
- House quality ratings
- Sale Price

The dataset was cleaned and preprocessed before training machine learning models.

---

# 🚀 Project Workflow

```
Raw Dataset
      │
      ▼
Data Cleaning
      │
      ▼
Feature Engineering
      │
      ▼
Exploratory Data Analysis
      │
      ▼
Feature Encoding
      │
      ▼
Train-Test Split
      │
      ▼
Feature Scaling
      │
      ▼
Supervised Learning
      │
      ▼
Ensemble Learning
      │
      ▼
Hyperparameter Tuning
      │
      ▼
Model Evaluation
      │
      ▼
Model Serialization
```

---

# 📘 Part 1 – Data Preprocessing

The first stage of the project focuses on preparing the dataset for machine learning.

### Topics Covered

- Loading the dataset
- Exploratory Data Analysis (EDA)
- Missing value handling
- Duplicate detection
- Outlier analysis
- Feature engineering
- Ordinal encoding
- One-Hot Encoding
- Dataset cleaning
- Exporting the cleaned dataset

### Output

- `cleaned_data.csv`

---

# 📗 Part 2 – Supervised Machine Learning

This section introduces supervised learning algorithms for both regression and classification tasks.

### Regression Models

- Linear Regression
- Ridge Regression

### Classification Model

- Logistic Regression

### Additional Analysis

- Feature Scaling
- ROC Curve
- AUC Score
- Decision Threshold Analysis
- Logistic Regression Regularization
- Bootstrap Confidence Interval

---

# 📙 Part 3 – Advanced Modeling

The final section focuses on advanced machine learning techniques and model optimization.

### Models Implemented

- Decision Tree
- Controlled Decision Tree
- Random Forest
- Gradient Boosting

### Advanced Topics

- Feature Importance
- Feature Ablation Study
- Cross Validation
- Machine Learning Pipeline
- GridSearchCV
- Hyperparameter Tuning
- Manual Learning Curve
- Model Serialization
- Model Reload & Prediction

---

# 🛠 Technologies Used

### Programming Language

- Python

### Libraries

- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Joblib

---

# 📈 Machine Learning Techniques

- Data Cleaning
- Feature Engineering
- Feature Encoding
- Standardization
- Linear Regression
- Ridge Regression
- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- Cross Validation
- Hyperparameter Tuning
- Pipeline
- Feature Importance
- Model Serialization

---

# 📁 Repository Contents

| File | Description |
|------|-------------|
| Part-1 | Data preprocessing and cleaning |
| Part-2 | Supervised Machine Learning |
| Part-3 | Advanced Modeling and Ensemble Learning |
| cleaned_data.csv | Cleaned dataset used for Parts 2 and 3 |
| best_model.pkl | Serialized best-performing machine learning pipeline |
| requirements.txt | Project dependencies |

---

# ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/muditkumar14/capstone-ames-data-intelligence.git
```

### 2. Navigate into the project

```bash
cd capstone-ames-data-intelligence
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Open the notebooks

Run the notebooks in the following order:

1. Part-1
2. Part-2
3. Part-3

---

# 📊 Key Highlights

✔ Complete end-to-end Machine Learning workflow

✔ Clean and well-documented code

✔ Ensemble Learning implementation

✔ Hyperparameter Optimization using GridSearchCV

✔ Feature Importance Analysis

✔ Manual Learning Curve Analysis

✔ Cross-Validation

✔ Reproducible Scikit-learn Pipeline

✔ Model Serialization using Joblib

---

# 🎯 Learning Outcomes

Through this project, I gained practical experience with:

- Data preprocessing and feature engineering
- Regression and classification models
- Ensemble learning methods
- Model evaluation techniques
- Hyperparameter tuning
- Machine learning pipelines
- Cross-validation
- Model deployment preparation

---

# 🔮 Future Improvements

Possible future enhancements include:

- XGBoost and LightGBM implementation
- SHAP explainability
- Interactive Streamlit dashboard
- Automated model monitoring
- REST API deployment using FastAPI

---

# 👨‍💻 Author

**Mudit Kumar Singh**

This repository was created as part of a Machine Learning capstone project to demonstrate practical skills in data preprocessing, supervised learning, ensemble methods, model optimization, and reproducible machine learning workflows.
