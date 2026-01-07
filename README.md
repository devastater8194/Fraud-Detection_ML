# Fraud Transaction Detection using Machine Learning

##  Project Overview
This project focuses on building a machine learning model to detect fraudulent financial transactions using a highly imbalanced real-world dataset. The goal is not only to build an accurate model, but also to extract meaningful insights and propose actionable fraud prevention strategies.

The project was completed as part of the **Accredian Technologies Internship Case Study**.

---

## Dataset Description
- Total records: ~6.3 million transactions
- Target variable: `isFraud` (0 = Non-Fraud, 1 = Fraud)
- Features include:
  - Transaction amount
  - Account balances before and after transaction
  - Transaction type (categorical)
  - Engineered balance-based indicators

Due to confidentiality, the dataset is not included in this repository.

---

##  Data Cleaning & Preprocessing
- No missing values were present in the dataset.
- Extreme transaction values were retained as they represent valid fraud behavior.
- Identifier columns (`nameOrig`, `nameDest`) were removed to avoid overfitting.
- Categorical feature (`type`) was one-hot encoded.
- Feature engineering included zero-balance indicators to capture risky patterns.
- Scaling was applied only where required (Logistic Regression).

---

##  Modeling Approach
This problem was treated as a **binary classification task**.

### Models Used
1. **Logistic Regression**
   - Used as a baseline model
   - Provided high recall but very low precision

2. **XGBoost (Final Model)**
   - Chosen for its ability to handle:
     - Non-linear relationships
     - Large-scale tabular data
     - Severe class imbalance
   - Threshold tuning was applied to balance recall and precision

---

## Model Evaluation
Given the highly imbalanced nature of the data, accuracy was not the primary metric.

### Key Evaluation Metrics
- ROC-AUC
- Precision
- Recall
- F1-score
- Precision–Recall AUC (PR-AUC)
- Confusion Matrix
- Threshold-based analysis

### Final XGBoost Performance (Approx.)
- **ROC-AUC:** ~0.96  
- **PR-AUC:** ~0.48  
- **Recall (Fraud):** ~0.99  
- **Precision (Fraud):** Improved over baseline via threshold tuning  

These results demonstrate strong discriminative power and effective fraud detection capability.

---

## Key Factors Predicting Fraud
Feature importance analysis revealed that fraud is strongly associated with:
- High transaction amounts
- Zero or low account balance before transaction
- Sudden balance changes
- Certain transaction types

These patterns align well with real-world financial fraud behavior.

---

## Business Recommendations
Based on model insights, the following prevention strategies are recommended:
- Real-time transaction monitoring using risk scores
- Additional verification for high-risk transactions
- Temporary account holds for suspicious activity
- Dynamic threshold adjustment based on operational risk tolerance

---

## Measuring Effectiveness
The success of the fraud detection system can be measured using:
- Reduction in fraud rate and financial losses
- Monitoring recall and false positive rates
- Tracking ROC-AUC and PR-AUC over time
- Periodic model retraining to handle evolving fraud patterns

---

## Tech Stack
- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Matplotlib / Seaborn
- Jupyter Notebook
