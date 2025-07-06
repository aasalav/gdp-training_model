Model Comparison: Top 10 vs All Features
R²: Models using all features outperform those with only the top 10 variables on both training and test sets (Train: 0.82 vs 0.70, Test: 0.83 vs 0.76).

RMSE & MAE: The errors (RMSE and MAE) are consistently lower when using all variables, indicating improved prediction accuracy.

Summary: Including all 27 variables leads to better and more reliable model performance compared to limiting the dataset to the top 10 correlated features.

Metric	Top 10 Variables	All Variables
R² (Train)	0.700	0.822
R² (Test)	0.763	0.833
RMSE (Train)	8950.800	6900.696
RMSE (Test)	7470.319	6262.955
MAE (Train)	6099.180	5294.338
MAE (Test)	5319.696	5022.357
