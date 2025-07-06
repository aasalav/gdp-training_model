
# 📝 Conclusions

## Q1: Key Variables for Predicting GDP per Capita

### Important Features Identified by Both Linear Regression (LR) and Random Forest (RF):

- **Life Expectancy at Birth**  
  - RF importance score: 0.57  
  - LR correlation coefficient: 0.72  
- **Random Forest (RF) also highlights:**  
  Revenue, Adolescent Fertility Rate, Precipitation per Year, Water Productivity  
- **Linear Regression (LR) additionally emphasizes:**  
  School Enrollment, Water Productivity, Remittances, Revenue  

---

### Understanding Differences in Feature Importance: RF vs LR

- **Random Forest (RF):**  
  Evaluates feature importance based on how much each variable reduces prediction error across many decision trees.  
  - Captures **nonlinear relationships** and **feature interactions**.  
  - Importance reflects overall predictive contribution beyond simple correlations.

- **Linear Regression (LR):**  
  Assesses feature importance through correlation coefficients that measure **linear associations** with the target variable.  
  - Reflects direct, additive influence of each predictor.  

---

### Why Do Rankings Differ?

- RF accounts for complex patterns and interactions between variables, adjusting feature importance accordingly.  
- LR ranks features purely based on their linear correlation with GDP per capita, which may overemphasize variables strongly correlated with each other.  

---

### Example from Your Data

- *Life Expectancy* consistently ranks highly in both models, confirming it as a robust predictor.  
- RF assigns high importance to *Revenue* and *Adolescent Fertility Rate* due to their nonlinear effects.  
- LR highlights *School Enrollment* and *Remittances* because of their strong linear correlations with GDP per capita.

---

### Summary

- **Linear Regression** highlights variables with strong linear influence on GDP per capita.  
- **Random Forest** reveals a broader set of important predictors, including those involved in nonlinear relationships and interactions.  

Both approaches offer valuable insights, and combining their interpretations provides a more comprehensive understanding of key drivers of GDP per capita.

---

<div style="border-left: 4px solid #1E90FF; padding: 10px; background-color: #f0f8ff;">
    
## Q2: Compare models 📈 Linear Regression vs 🌲 Random Forest 
---
### Choose an appropriate model for this analysis

<div style="font-size: 18px;">

## Train vs Test Metrics

| Metric           | Linear Regression (Top 10) | Linear Regression (All) | Random Forest (Top 10) | Random Forest (All) |
|------------------|----------------------------|------------------------|-----------------------|---------------------|
| **R² (Train)**   | 0.700                      | 0.822                  | 0.831                 | 0.862               |
| **R² (Test)**    | 0.763                      | 0.833                  | 0.772                 | 0.829               |
| **RMSE (Train)** | 8,950.800                  | 6,900.696              | 6,724.287             | 6,069.157           |
| **RMSE (Test)**  | 7,470.319                  | 6,262.955              | 7,319.621             | 6,352.898           |
| **MAE (Train)**  | 6,099.180                  | 5,294.338              | 4,993.757             | 4,539.835           |
| **MAE (Test)**   | 5,319.696                  | 5,022.357              | 5,532.461             | 4,712.208           |

</div>

### Comparing LR vs RF methods

- **Using all variables improves model performance** for both Linear Regression and Random Forest, yielding higher R² and lower errors compared to using only the top 10 features.

- **Random Forest fits the training data better** and captures nonlinear relationships, resulting in slightly higher accuracy and robustness.

- **Both models perform similarly on test data** (Test R² ≈ 0.83), indicating good generalization.

- **Linear Regression is simpler and more interpretable**, with coefficients that clearly represent feature effects.

<div style="border-left: 4px solid #228B22; padding: 10px; background-color: #f0fff0;">

### **Recommended approach:**  
Use **Random Forest for prediction** due to its better accuracy, and **Linear Regression for interpretability** to explain key drivers to stakeholders.

This hybrid strategy balances accuracy and transparency effectively.

</div>
</div>


