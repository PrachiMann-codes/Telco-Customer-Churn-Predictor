# Telco Customer Churn Predictor

## 1. Abstract
This project predicts customer churn in the telecom industry using the Telco Customer Churn dataset (7043 rows, 21 columns). Churn prediction is vital for customer retention strategies, as identifying at‑risk customers allows companies to take proactive measures. The project applies Exploratory Data Analysis (EDA), preprocessing, and multiple machine learning models to identify the best performing approach. Logistic Regression (Raw) was chosen as the final model due to its strong performance and interpretability.

---

## 2. Problem Statement
Telecom companies face significant losses due to customer churn. The challenge is to predict which customers are likely to leave based on demographic, service usage, and billing information. The goal is to build a predictive model that balances accuracy with interpretability, enabling actionable insights for business decision‑making.

---

## 3. Objectives
- Perform EDA to understand churn patterns and customer behavior.  
- Preprocess the dataset (handle missing values, encode categorical variables, scale numeric features).  
- Address class imbalance using SMOTE.  
- Train and evaluate multiple machine learning models.  
- Select the best model based on performance metrics and interpretability.  
- Use SHAP analysis to explain model predictions and feature importance.  

---

## 4. Dataset Description
- **Source**: Telco Customer Churn dataset (7043 rows, 21 columns).  
- **Features**: Customer demographics (gender, senior citizen, partner, dependents), service details (phone, internet, streaming, contract type), billing information (payment method, monthly charges, total charges).  
- **Target**: `Churn` (Yes/No).  
- **Class distribution**: 73% non‑churn, 27% churn → significant imbalance.  

---

## 5. Methodology
- **Preprocessing**: Converted `TotalCharges` to numeric, dropped missing values, encoded categorical features, scaled numeric features.  
- **EDA**:  
  - Churn Distribution: Confirmed imbalance (73% No, 27% Yes).  
  - Tenure: Short‑tenure customers churn more.  
  - Monthly Charges: Higher charges linked to churn.
  - Total Charges: Higher charges linked to churn.   
  - Payment Method: Electronic check users churn more.  
  - Internet Service: Fiber optic customers churn more than DSL.  
  - Correlation Heatmap: Strong correlation between tenure and total charges.  
- **Model Exploration**: Compared Logistic Regression, Decision Tree, Random Forest, KNN, XGBoost, and a stacked ensemble.  
- **Evaluation Metrics**: Accuracy, Balanced Accuracy, F1 scores, ROC‑AUC.  
- **SHAP Analysis**: Used to explain predictions globally (feature importance) and locally (individual customer churn risk).  

---

## 6. Exploratory Data Analysis (EDA)
EDA revealed key churn drivers:  
- Customers with Month‑to‑Month contracts and Electronic check payments are most at risk.  
- Longer tenure and Two‑year contracts reduce churn probability.  
- Fiber optic internet customers churn more compared to DSL.  
- Numeric features (`tenure`, `MonthlyCharges`, `TotalCharges`) show meaningful correlations.  

Visualizations included churn distribution plots, histograms for numeric features, bar plots for categorical features vs churn, and a correlation heatmap.

---

## 7. Machine Learning Models
- Logistic Regression (Raw): Accuracy ≈ 79%, ROC‑AUC ≈ 0.83.  
- Random Forest (SMOTE): Accuracy ≈ 76%, ROC‑AUC ≈ 0.81.  
- XGBoost (SMOTE): Accuracy ≈ 75%, ROC‑AUC ≈ 0.81.  
- Decision Tree: Accuracy ≈ 71%, weaker performance.  
- KNN: Accuracy ≈ 76%, ROC‑AUC ≈ 0.69.  
- Stacked Ensemble (RF + XGB): Accuracy ≈ 76%, ROC‑AUC ≈ 0.81.  

---

## 8. Results and Discussion
- Logistic Regression (Raw) outperformed other models in terms of accuracy, balanced accuracy, F1 score, and ROC‑AUC.  
- Threshold tuning (0.4 instead of 0.5) improved recall for churners, making the model more useful for retention strategies.  
- SHAP analysis confirmed that Contract type, Payment Method, Internet Service, Monthly Charges, and Tenure are the most influential features.  
- While ensemble models provided competitive performance, they lacked interpretability compared to Logistic Regression.  

---

## 9. Conclusion 
- Logistic Regression (Raw) provided the best balance of accuracy (≈79%), ROC‑AUC (≈0.83), and interpretability.  
- EDA revealed that churn is strongly influenced by contract type, payment method, internet service, monthly charges, and tenure.  
- SHAP analysis confirmed these features as the most important drivers of churn.  
- Adjusting the decision threshold improved recall, making the model more effective at identifying at‑risk customers.  
