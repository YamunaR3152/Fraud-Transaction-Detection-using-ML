# Fraud-Transaction-Detection-Using-Machine-Learning

Built a machine learning model to detect fraudulent financial transactions and generate actionable business insights to help prevent fraud. The project focuses on handling large-scale, highly imbalanced data and optimizing model performance for real-world deployment.

## Objective
The objective of this project is to build a machine learning model that can accurately predict fraudulent transactions for a financial company and derive meaningful business insights that support fraud prevention strategies.

## Dataset Overview
- Large-scale financial transaction dataset  
- Highly imbalanced target variable (fraud cases are rare)  
- Target variable: `isFraud`  

## Feature Selection
- Removed identifier columns (`nameOrig`, `nameDest`) as they do not add predictive value  
- Dropped `isFlaggedFraud` to avoid data leakage  
- Retained transaction amount, transaction type, and balance-related features  
- Encoded transaction type features (e.g., CASH_OUT, TRANSFER)

## Sampling Strategy & Train-Test Split
- Used a **stratified 3M-row sample** to reduce computation time while preserving fraud distribution  
- Performed an **80–20 stratified train-test split** to maintain class balance  

## Model Building
- Used a **Random Forest Classifier**  
- Applied `class_weight='balanced'` to handle class imbalance  
- Model constraints:
  - `n_estimators = 30`
  - `max_depth = 10`

### Why Random Forest?
- Captures non-linear relationships  
- Robust to outliers  
- Performs well on imbalanced datasets  
- Provides feature importance for explainability  

## Model Performance
Evaluation on the test dataset:

- **Accuracy:** 0.99  
- **ROC-AUC Score:** 0.996  

| Class | Precision | Recall | F1-score |
|------|----------|--------|---------|
| Non-Fraud (0) | 1.00 | 0.99 | 1.00 |
| Fraud (1) | 0.12 | 0.93 | 0.21 |

### Performance Insights
- High **recall (0.93)** ensures most fraudulent transactions are detected  
- Lower precision is acceptable in proactive fraud detection systems  
- ROC-AUC > 0.99 indicates excellent class separation  

## Key Factors Predicting Fraud
- Transaction amount (log-transformed)  
- High-risk transaction types (CASH_OUT, TRANSFER)  
- Abnormal sender and receiver balance changes  

## Business Insights
- Large-value transactions are more prone to fraud  
- CASH_OUT and TRANSFER transactions carry higher fraud risk  
- Balance inconsistencies strongly indicate fraudulent behavior  

## Recommendations for Fraud Prevention
- Enable real-time monitoring for high-risk transaction types  
- Set alerts for unusually large transaction amounts  
- Apply multi-factor authentication for sensitive transfers  
- Monitor balance anomalies before transaction completion  
- Deploy the model for automated fraud risk scoring  

## Measuring Effectiveness
- Track precision, recall, F1-score, and ROC-AUC over time  
- Monitor reduction in successful fraud incidents  
- Periodically retrain the model to adapt to evolving fraud patterns  

## Technologies Used
- Python  
- Pandas  
- NumPy  
- Scikit-learn  
- Matplotlib / Seaborn  

## Skills Demonstrated
- Machine Learning  
- Imbalanced Data Handling  
- Feature Engineering  
- Model Evaluation  
- Business Analytics  

