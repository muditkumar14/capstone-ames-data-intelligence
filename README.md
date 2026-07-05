# capstone-ames-data-intelligence
End-to-end data intelligence system using the Ames Housing dataset. Covers EDA, supervised learning, ensemble modeling, and LLM-powered insights.

Numeric columns with less than 20% missing values were imputed using the median because the median is robust to outliers and skewed distributions. Unlike the mean, the median is not significantly influenced by extreme values, making it a more reliable measure of central tendency for the Ames Housing dataset. Columns with more than 20% missing values were intentionally left unchanged for further analysis and handling in later stages.
