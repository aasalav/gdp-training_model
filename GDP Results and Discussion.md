# Summary Results

# 1.📊 Data understanding

The initial dataset contained more than 50 columns, many of which had missing values and non-numeric data. Therefore, the original dataset was reduced, and this project starts with the `cleaned_data_project1_ds.csv` file.

The variable **GNI per capita** was removed from the dataset because it is highly correlated with **GDP per capita**. In initial model training, including GNI per capita caused it to dominate the predictions and accurately predict the outcome on its own, overshadowing the influence of other variables.

By removing this variable, the analysis aims to highlight the contribution of additional factors to predicting GDP per capita.

---

# 🧹 2. Data Cleaning Summary

- The original dataset had 56 columns with mixed data types; all non-numeric columns were removed to simplify analysis, leaving 27 numeric variables.
- The dataset contained 21% missing values. Instead of dropping rows (which would reduce sample size), missing values were imputed using the median of each column, preserving all data points.
- Median imputation can reduce data variance and may weaken correlations if missingness is systematic, potentially introducing bias and affecting model reliability.
- Despite these limitations, median imputation offers a practical balance by maintaining dataset size while enabling modeling. More advanced missing data methods can be considered if needed.

---

# 🤖 3. Data Modelling

As outlined in the project goals, **GDP per capita** will be predicted using two modeling approaches:  
- **Linear Regression (LR)**  
- **Random Forest (RF)**  

To evaluate variable importance, two dataset versions were used:  
- **Top 10 features** (selected by highest correlation coefficients)  
- **Full dataset** with all 27 features  

---
## 📈 3.1 Linear Regression
### 📈 Linear Regression Model Comparison: Top 10 vs All Features

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

---
## 3.2 🌳 Random Forest
### 🌳 Random Forest Model Comparison: Top 10 vs All Features

#### Intro
✅ **Can Random Forest help you select relevant variables?**

**Yes!**

Random Forest is very popular for feature selection because:

- It can capture non-linear relationships and interactions.  
- It provides a measure of feature importance based on how much each variable reduces prediction error in the trees.

So, instead of just looking at correlation, you use Random Forest to learn which variables are truly helpful for predicting GDP.

---

#### How does Random Forest compute feature importance?

In Random Forest, each decision tree splits data using the variables that most reduce the prediction error (measured by impurity, like Mean Squared Error for regression).  
The importance of a variable is calculated as the average reduction in error it brings across all trees.

Variables that frequently split nodes near the top of the trees (which means they explain a lot of the variation) get higher importance scores.

---

#### Model Comparison: Random Forest — Top 10 vs All Features

- **R²:** All features slightly outperform Top 10 (Train: 0.86 vs 0.85, Test: 0.83 vs 0.82).  
- **RMSE & MAE:** Prediction errors (RMSE & MAE) are marginally lower with all features on both train and test sets.  
- **Summary:** Top 10 features offer strong performance, but including all variables yields slightly better overall accuracy.

| Metric       | Top 10 Variables | All Variables |
|--------------|------------------|---------------|
| R² (Train)   | 0.853            | 0.862         |
| R² (Test)    | 0.815            | 0.829         |
| RMSE (Train) | 6274.602         | 6069.157      |
| RMSE (Test)  | 6593.996         | 6352.898      |
| MAE (Train)  | 4622.395         | 4539.835      |
| MAE (Test)   | 4838.279         | 4712.208      |

---
## 3.3 Comparison 📈 Linear Regression vs 🌲Random Forest

### ✅ Model Comparison: Linear Regression vs Random Forest

### 1️⃣ Train vs Test Metrics

| Metric          | Linear Regression (Top 10) | Linear Regression (All) | Random Forest (Top 10) | Random Forest (All) |
|-----------------|----------------------------|-------------------------|------------------------|---------------------|
| **R² (Train)**  | 0.700                      | 0.822                   | 0.831                  | 0.862               |
| **R² (Test)**   | 0.763                      | 0.833                   | 0.772                  | 0.829               |
| **RMSE (Train)**| 8,950.800                  | 6,900.696               | 6,724.287              | 6,069.157           |
| **RMSE (Test)** | 7,470.319                  | 6,262.955               | 7,319.621              | 6,352.898           |
| **MAE (Train)** | 6,099.180                  | 5,294.338               | 4,993.757              | 4,539.835           |
| **MAE (Test)**  | 5,319.696                  | 5,022.357               | 5,532.461              | 4,712.208           |

---

### 2️⃣ Interpretation & Insights

✅ **Impact of Using All Variables**  
- Both models perform better when using **all variables** rather than just the top 10:  
  - **Higher R²** means more variance explained.  
  - **Lower RMSE (Root Mean Squared Error) & MAE (Mean Absolute Error)** means more accurate predictions.  
- This shows that additional variables contain relevant information.

---

✅ **Linear Regression vs Random Forest**  
- **Random Forest** has higher Train R² and lower Train error — showing it fits the training data better and can capture nonlinear patterns.  
- However, both models perform **very similarly on Test data**.  
  - Test R² is ~0.83 for both.  
  - Test RMSE and MAE are comparable.  
- **Linear Regression** is simpler and more interpretable.  
- **Random Forest** is more flexible but has a mild risk of overfitting.

---

### 3️⃣ Key Takeaways

| Aspect              | Linear Regression | Random Forest      |
|---------------------|-------------------|--------------------|
| **Training Fit**    | Lower            | Higher            |
| **Test Performance**| Similar          | Similar           |
| **Captures Nonlinearities** | ❌ No           | ✅ Yes             |
| **Interpretability**| ✅ High          | ❌ Lower          |
| **Overfitting Risk**| ✅ Low           | ⚠️ Slightly Higher |

---

### 4️⃣ Next Steps

- ✅ Tune Random Forest hyperparameters for potential improvements.  
- ✅ Use feature importance from Random Forest to refine feature selection.  
- ✅ Consider Linear Regression if interpretability is a priority.  
- ✅ Keep monitoring the Train-Test gap to avoid overfitting.

---

**Overall:**  
Using **all variables** provides the best predictive power for both methods. Random Forest slightly improves training fit but both models generalize equally well.

✨ **Good practice:** Balance accuracy, interpretability, and complexity based on your project goals!

---

# 📝 Step 4: Conclusions

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


