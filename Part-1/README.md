# 🏡 Capstone – Ames Data Intelligence

> **An End-to-End Data Intelligence System built using the Ames Housing Dataset, covering data acquisition, data cleaning, exploratory data analysis (EDA), statistical analysis, feature engineering preparation, and machine learning-ready data processing.**

## 📌 Project Overview

This project was developed as part of the **Applied AI & Machine Learning Capstone Project** with the objective of building a complete data intelligence pipeline from raw structured data to machine learning-ready datasets.

Using the **Ames Housing Dataset**, the project demonstrates a practical data science workflow by transforming raw housing records into a clean, well-structured dataset through systematic preprocessing, statistical analysis, and exploratory data analysis.

The project emphasizes not only writing functional code but also making data-driven decisions at every stage of the preprocessing pipeline. Each step is supported with statistical reasoning and documented observations to ensure transparency, reproducibility, and readiness for predictive modeling.

## 🎯 Project Objectives

The primary objectives of this project are to:

* Acquire and inspect raw structured data.
* Identify and handle missing values using statistically appropriate techniques.
* Detect and remove duplicate records.
* Optimize data types to improve memory efficiency.
* Perform descriptive statistical analysis.
* Analyze feature distributions using skewness.
* Detect potential outliers using the Interquartile Range (IQR) method.
* Explore relationships between variables through visualizations.
* Compare Pearson and Spearman correlation techniques.
* Evaluate grouped statistical summaries for categorical variables.
* Generate a clean dataset (`cleaned_data.csv`) that will be used for regression, classification, ensemble learning, and LLM-powered insights in subsequent parts of the capstone.

## 📊 Dataset Information

The project uses the **Ames Housing Dataset**, a widely used real-world housing dataset containing approximately **2,930 residential property records** and **82 features** describing different aspects of residential properties.

The dataset includes:

* Numerical features such as lot area, living area, garage size, construction year, and sale price.
* Categorical features such as neighborhood, zoning classification, street type, and house style.
* Missing values suitable for demonstrating preprocessing techniques.
* Outliers and skewed distributions that require statistical analysis.
* A continuous target variable (`SalePrice`) suitable for regression and capable of being converted into a binary target for classification tasks.

The Ames Housing dataset was selected because it satisfies all the requirements of the capstone project while closely representing the type of structured data encountered in real-world business analytics and machine learning projects.

## 🛠️ Technologies Used

* Python 3
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook / Google Colab

## 🔍 Skills Demonstrated

This project showcases practical skills in:

* Data Cleaning
* Exploratory Data Analysis (EDA)
* Statistical Analysis
* Feature Engineering Preparation
* Missing Value Treatment
* Duplicate Detection
* Data Type Optimization
* Outlier Detection
* Correlation Analysis
* Data Visualization
* Data Preprocessing for Machine Learning
* Technical Documentation

## 📂 Repository Structure

```text
capstone-ames-data-intelligence/
│
├── Part_1_EDA.ipynb          # Complete preprocessing and EDA notebook
├── cleaned_data.csv          # Clean dataset generated after preprocessing
├── README.md                 # Project documentation
└── requirements.txt          # Python dependencies (optional)
```

## 🚀 Key Highlights

* Processed and analyzed nearly **3,000 housing records** across **80+ features**.
* Performed comprehensive missing value analysis with statistically justified median imputation.
* Optimized memory usage through efficient data type conversion.
* Investigated feature distributions using descriptive statistics and skewness analysis.
* Detected potential outliers using the IQR method without discarding valuable observations.
* Built multiple visualizations to uncover relationships among housing features.
* Compared Pearson and Spearman correlation techniques to evaluate both linear and monotonic relationships.
* Generated a machine learning-ready dataset for use in regression, classification, and ensemble modeling tasks.

## 📈 Future Work

The remaining phases of this capstone project will extend this foundation by:

* Developing supervised machine learning models.
* Building ensemble learning models for improved predictive performance.
* Evaluating regression and classification algorithms.
* Integrating an LLM-powered feature capable of generating structured explanations and insights from the dataset and trained models.
