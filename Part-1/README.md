# Part 1 – Data Acquisition, Data Cleaning and Exploratory Data Analysis

## Objective

The main objective of this part of the project was to understand the Ames Housing dataset and prepare it for machine learning. This involved downloading the dataset, checking data quality, handling missing values, removing duplicate records, correcting data types, performing statistical analysis, identifying outliers, and visualizing important patterns in the data.

The cleaned dataset generated in this part is used throughout the remaining parts of the project.

---

# Dataset Information

- **Dataset:** Ames Housing Dataset
- **Source:** Kaggle
- **Number of Records:** 2930
- **Number of Features:** 81
- **Target Variable:** SalePrice

The dataset contains information about residential properties such as lot size, neighborhood, house quality, living area, garage details, and final sale price.

---

# Data Acquisition

The dataset was downloaded from Kaggle using the Kaggle API and loaded into a Pandas DataFrame.

After loading the data, I checked:

- First few rows of the dataset
- Number of rows and columns
- Data types of each feature

This helped me understand the structure of the dataset before starting the preprocessing steps.

---

# Missing Value Analysis

The first step was to identify missing values in every column.

Both the number and percentage of missing values were calculated.

Columns having more than **20% missing values** were identified separately.

For numerical columns with less than **20% missing values**, I replaced the missing values using the **median** because the housing dataset contains several skewed distributions and the median is less affected by outliers than the mean.

After imputation, the remaining missing values were checked again.

---

# Duplicate Detection

Duplicate rows were identified using the Pandas `duplicated()` function.

The duplicate records were removed from the dataset.

After removing duplicates, I compared:

- Dataset size before and after removal
- Remaining duplicate rows
- Missing value percentages before and after removing duplicates

This ensured that the cleaning process did not introduce any unexpected changes.

---

# Data Type Correction

Some columns required changes to their data types.

The **PID** column represents a unique identifier rather than a numerical value, so it was converted from integer to string.

The following repetitive categorical columns were converted to the **category** data type:

- MS Zoning
- Street
- Lot Shape
- Neighborhood
- House Style

After the conversion, I compared the memory usage before and after the changes and observed a reduction in memory consumption.

---

# Descriptive Statistics

Descriptive statistics were generated for all numerical features using the `describe()` function.

The summary includes:

- Count
- Mean
- Standard Deviation
- Minimum
- Maximum
- Quartiles

These statistics provide a quick overview of the distribution of each numerical feature.

---

# Skewness Analysis

The skewness of every numerical feature was calculated.

The analysis helped identify:

- The most positively skewed feature
- The most negatively skewed feature
- The ten most skewed numerical features

Understanding skewness is useful because highly skewed features are more sensitive to outliers and usually require median-based preprocessing.

---

# Outlier Detection

Outliers were detected using the **Interquartile Range (IQR)** method.

The analysis was performed for:

- SalePrice
- Gr Liv Area

For each feature, the following values were calculated:

- First Quartile (Q1)
- Third Quartile (Q3)
- Interquartile Range (IQR)
- Lower Bound
- Upper Bound
- Number of Outliers

---

# Data Visualization

Several visualizations were created to better understand the dataset.

### Line Plot

Shows how SalePrice changes across different observations.

### Bar Chart

Displays the average SalePrice for each neighborhood.

### Histogram

Shows the distribution of the most skewed numerical feature.

### Scatter Plot

Illustrates the relationship between Ground Living Area and SalePrice.

### Box Plot

Compares SalePrice distributions across the most common neighborhoods.

### Correlation Heatmap

Shows the correlation between all numerical variables and helps identify highly correlated features.

---

# Mean vs Median Comparison

The two most skewed numerical features were selected.

For each feature, I compared:

- Mean
- Median
- Skewness

The comparison shows why the median is generally a better choice for imputing missing values in skewed datasets.

---

# Correlation Analysis

Both Pearson and Spearman correlation coefficients were calculated.

- **Pearson Correlation** measures linear relationships.
- **Spearman Correlation** measures monotonic relationships based on ranked values.

I compared both methods and identified the feature pairs with the largest differences.

---

# Grouped Aggregation

The dataset was grouped by **Neighborhood**.

For each neighborhood, I calculated:

- Mean SalePrice
- Standard Deviation
- Number of Houses

I also identified:

- Neighborhood with the highest average sale price
- Neighborhood with the largest variation in prices
- Ratio of the highest mean sale price to the lowest mean sale price

---

# Cleaned Dataset

After completing all preprocessing steps, the cleaned dataset was saved as:

```
cleaned_data.csv
```

This cleaned dataset is used in the remaining parts of the project for machine learning model development.

---

# Key Learnings

During this part of the project, I learned how to:

- Download datasets from Kaggle.
- Explore and understand a new dataset.
- Handle missing values using median imputation.
- Remove duplicate records.
- Correct inappropriate data types.
- Reduce memory usage using categorical variables.
- Detect skewed distributions and outliers.
- Create meaningful visualizations.
- Compare Pearson and Spearman correlation.
- Perform grouped statistical analysis.

---

# Conclusion

In this part of the project, I successfully cleaned and explored the Ames Housing dataset. The preprocessing steps improved the overall quality of the data by handling missing values, removing duplicate records, correcting data types, and identifying outliers. The exploratory analysis and visualizations provided useful insights into the dataset and helped understand the factors that influence house prices. The final cleaned dataset is now ready for machine learning models, which are implemented in the following parts of the project.
