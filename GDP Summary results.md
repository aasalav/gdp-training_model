# Project Report

## 1. Introduction & Data Cleaning

The initial dataset contained more than 50 columns, many of which had missing values and non-numeric data. Therefore, the original dataset was reduced, and this project starts with the `cleaned_data_project1_ds.csv` file.

The variable **GNI per capita** was removed from the dataset because it is highly correlated with **GDP per capita**. In initial model training, including GNI per capita caused it to dominate the predictions and accurately predict the outcome on its own, overshadowing the influence of other variables.

By removing this variable, the analysis aims to highlight the contribution of additional factors to predicting GDP per capita.

---

## 2. Data Cleaning Summary

- The original dataset had 56 columns with mixed data types; all non-numeric columns were removed to simplify analysis, leaving 27 numeric variables.
- The dataset contained 21% missing values. Instead of dropping rows (which would reduce sample size), missing values were imputed using the median of each column, preserving all data points.
- Median imputation can reduce data variance and may weaken correlations if missingness is systematic, potentially introducing bias and affecting model reliability.
- Despite these limitations, median imputation offers a practical balance by maintaining dataset size while enabling modeling. More advanced missing data methods can be considered if needed.

---

## 3. Data Modelling

As outlined in the project goals, **GDP per capita** will be predicted using two modeling approaches:  
- **Linear Regression (LR)**  
- **Random Forest (RF)**  

To evaluate variable importance, two dataset versions were used:  
- **Top 10 features** (selected by highest correlation coefficients)  
- **Full dataset** with all 27 features  

### Linear Regression Model Comparison: Top 10 vs All Features

- **R²:** Models using all features outperform those with only the top 10 variables on both training and test sets (Train: 0.82 vs 0.70, Test: 0.83 vs 0.76).
- **RMSE & MAE:** The errors (RMSE and MAE) are consistently lower when using all variables, indicating improved prediction accuracy.
- **Summary:** Including all 27 variables leads to better and more reliable model performance compared to limiting the dataset to the top 10 correlated features.

| Metric       | Top 10 Variables | All Variables |
|--------------|------------------|---------------|
| R² (Train)   | 0.700            | 0.822         |
| R² (Test)    | 0.763            | 0.833         |
| RMSE (Train) | 8950.800         | 6900.696      |
| RMSE (Test)  | 7470.319         | 6262.955      |
| MAE (Train)  | 6099.180         | 5294.338      |
| MAE (Test)   | 5319.696         | 5022.357      |
