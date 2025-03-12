# Fraud Detection with Machine Learning

## Project Overview
This project applies **machine learning** techniques to detect fraudulent transactions in online financial data. Fraud detection is a critical challenge for financial institutions, as fraudulent activities cause significant economic losses. This project focuses on analyzing transaction data, building predictive models, and evaluating their effectiveness in fraud prevention.

The primary objectives of this project are:
- Understanding the **patterns in fraudulent transactions** through exploratory data analysis (EDA).
- Developing **multiple machine learning models** to classify transactions as fraudulent or non-fraudulent.
- Optimizing model performance using **feature engineering**, **data balancing techniques**, and **hyperparameter tuning**.
- Comparing different models based on **accuracy, recall, precision, F1-score, and AUC-ROC**.

---

## Dataset Overview
This project utilizes a dataset containing **online financial transactions** with multiple attributes related to user behavior, payment methods, and transaction details.

### Dataset Details:
- **Total Number of Records:** ~590,000 transactions
- **Fraudulent Transactions:** ~3.5% (highly imbalanced dataset)
- **Number of Features:** 393
- **Target Variable:** `isFraud`
  - `1` → Fraudulent transaction
  - `0` → Legitimate transaction
- **Data Type:** Structured tabular data with numerical and categorical features.

### Feature Categories:
1. **Transaction Features:**
   - `TransactionDT`: Transaction timestamp  
   - `TransactionAmt`: Amount spent in the transaction  
   - `ProductCD`: Product category purchased  
2. **Card Details:**
   - `card1`, `card2`, `card3`, `card4`, `card5`, `card6`: Information related to the card used (e.g., issuer, type: credit/debit)
3. **Customer Identity Features:**
   - `id_01` to `id_38`: Various anonymized identity-related information (e.g., IP, device type)
4. **Behavioral Features:**
   - `V1` to `V339`: Features extracted from transaction history, user behavior, and anomaly detection signals.

### Data Challenges:
- **Class Imbalance:** Fraud cases represent only **~3.5%** of the total transactions, making the dataset highly imbalanced.  
- **Missing Values:** Many anonymized features contain missing values that must be handled properly.  
- **Feature Engineering Required:** Several features require transformation, encoding, and scaling to improve model performance.

---

## Machine Learning Models Used
This project experiments with **multiple supervised learning models**, with **performance comparison** across key metrics.

### **Baseline Model - Logistic Regression**
- **Accuracy:** 95.2%  
- **Precision:** 63.1%  
- **Recall:** 47.4%  
- **F1-Score:** 54.1%  
- **AUC-ROC:** 0.79  
- Logistic Regression serves as a simple baseline but **struggles with recall**, meaning many fraud cases are misclassified.

### **Random Forest Classifier**
- **Accuracy:** 97.5%  
- **Precision:** 76.3%  
- **Recall:** 64.8%  
- **F1-Score:** 70.1%  
- **AUC-ROC:** 0.86  
- The model improves over Logistic Regression but still struggles with recall.

### **Gradient Boosting (XGBoost)**
- **Accuracy:** 98.1%  
- **Precision:** 83.2%  
- **Recall:** 75.9%  
- **F1-Score:** 79.3%  
- **AUC-ROC:** 0.91  
- XGBoost significantly improves **fraud recall** while keeping precision high.

### **CatBoost (Best Performing Model)**
- **Accuracy:** 98.6%  
- **Precision:** 88.4%  
- **Recall:** 81.7%  
- **F1-Score:** 84.9%  
- **AUC-ROC:** 0.94  
- **CatBoost** outperforms all other models with the **best balance between precision and recall**.

### **Neural Network (MLP)**
- **Accuracy:** 97.8%  
- **Precision:** 80.1%  
- **Recall:** 70.6%  
- **F1-Score:** 75.0%  
- **AUC-ROC:** 0.89  
- Neural Networks perform well but require significant **hyperparameter tuning**.

---

## Data Processing & Feature Engineering
- **Missing Value Handling:** Imputation for missing card and transaction details.
- **Feature Scaling:** Normalization of numerical values (e.g., `TransactionAmt`).
- **One-Hot Encoding:** For categorical features such as `ProductCD` and `card4`.
- **Balancing Techniques:**  
  - **SMOTE (Synthetic Minority Over-sampling Technique)**: Generates synthetic fraud cases to balance the dataset.  
  - **Undersampling:** Reduces the number of non-fraud cases to prevent model bias.  

---

## Evaluation Metrics
Since fraud detection is a **highly imbalanced problem**, **accuracy alone is not sufficient**. The following metrics were used:

1. **Precision:** Measures how many transactions **predicted as fraud** are actually fraudulent.
2. **Recall (Sensitivity):** Measures how many **actual fraud cases** were correctly detected.
3. **F1-Score:** The balance between **precision and recall**.
4. **AUC-ROC Score:** Measures how well the model differentiates fraud from non-fraud.

CatBoost achieved the **highest recall and precision**, making it the **most effective model for fraud detection**.

