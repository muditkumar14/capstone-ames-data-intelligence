# capstone-ames-data-intelligence
End-to-end data intelligence system using the Ames Housing dataset. Covers EDA, supervised learning, ensemble modeling, and LLM-powered insights.

Numeric columns with less than 20% missing values were imputed using the median because the median is robust to outliers and skewed distributions. Unlike the mean, the median is not significantly influenced by extreme values, making it a more reliable measure of central tendency for the Ames Housing dataset. Columns with more than 20% missing values were intentionally left unchanged for further analysis and handling in later stages.

Duplicate Detection and Removal:
The dataset was checked for duplicate records using df.duplicated().sum(). A total of X duplicate rows were identified and removed using drop_duplicates(). After removal, the dataset contained Y rows, and no duplicate records remained. The null percentage before and after duplicate removal was compared. (If no change) The comparison showed that removing duplicate rows did not significantly affect the percentage of missing values in any column. (If there were changes) The change occurred because duplicate records containing missing values were removed, slightly altering the proportion of missing data.
