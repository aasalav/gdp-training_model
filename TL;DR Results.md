# 📝 Conclusions

# Introduction

This analysis compared two predictive modeling approaches—Linear Regression (LR) and Random Forest (RF)—to identify the key factors influencing GDP per capita. We evaluated feature importance from both models and assessed their predictive performance using training and test data. The goal was to understand which variables are most influential and to determine the most suitable model balancing accuracy and interpretability.

## Q1: Key Variables for Predicting GDP per Capita

### Important Features from Both Models

- **Life Expectancy at Birth**  
  - RF importance: 0.57  
  - LR correlation: 0.72  
- **Additional RF highlights:**  
  Revenue, Adolescent Fertility Rate, Precipitation, Water Productivity  
- **Additional LR highlights:**  
  School Enrollment, Water Productivity, Remittances, Revenue  

### Why Importance Rankings Differ

- **Random Forest (RF):** Captures nonlinearities and feature interactions; importance shows overall predictive power.  
- **Linear Regression (LR):** Reflects linear, direct relationships via correlation coefficients.  

### Example

- Life Expectancy ranks high in both models.  
- RF emphasizes nonlinear effects (e.g., Revenue, Adolescent Fertility Rate).  
- LR emphasizes strong linear correlates (e.g., School Enrollment, Remittances).  

### Summary

- LR shows linear influences.  
- RF reveals broader, complex predictors.  
- Combining both gives a fuller picture.

---

## Q2: Model Comparison — Linear Regression vs Random Forest

| Metric           | LR (Top 10) | LR (All) | RF (Top 10) | RF (All) |
|------------------|-------------|----------|-------------|----------|
| **R² (Train)**   | 0.70        | 0.82     | 0.83        | 0.86     |
| **R² (Test)**    | 0.76        | 0.83     | 0.77        | 0.83     |
| **RMSE (Train)** | 8951        | 6901     | 6724        | 6069     |
| **RMSE (Test)**  | 7470        | 6263     | 7319        | 6353     |
| **MAE (Train)**  | 6099        | 5294     | 4994        | 4540     |
| **MAE (Test)**   | 5319        | 5022     | 5532        | 4712     |

### Insights

- Using **all variables improves performance** for both models.  
- RF fits training data better, capturing nonlinearities.  
- Both models perform similarly on test data (R² ≈ 0.83).  
- LR is simpler and easier to interpret.  

### Recommended Approach

- Use **Random Forest** for accurate predictions.  
- Use **Linear Regression** for interpretability and explaining drivers.  

Balancing both methods delivers strong performance and transparency.

# Final Summary

Both Linear Regression and Random Forest provide valuable insights into the drivers of GDP per capita. Linear Regression offers straightforward interpretation by highlighting variables with strong linear effects, while Random Forest captures more complex nonlinear relationships and interactions, improving prediction accuracy. Using all variables improves model performance compared to limiting to the top features.

For practical applications, a hybrid approach is recommended: use Random Forest for robust, accurate predictions and Linear Regression to explain key factors to stakeholders. This strategy ensures a balance between predictive power and model transparency.
