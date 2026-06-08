💳 Credit Card Fraud Detection
A machine learning project that detects fraudulent credit card transactions.
Dataset: Kaggle — Credit Card Fraud Detection
---
What This Project Does
We trained a model that looks at a credit card transaction and predicts — is this fraud or not?
The dataset has 10,000 transactions where only 1.51% are fraud. That imbalance is the main challenge of this project.
---
Steps We Followed
1. Loaded the data
Checked for missing values and duplicates. Found none.
2. Explored the data (EDA)
Plotted charts to understand which features matter most.
Found that `device_trust_score` and `velocity_last_24h` are the strongest fraud signals.
3. Created new features
Added 6 new columns to help the model learn better — like `log_amount`, `is_night`, and `risk_score`.
4. Fixed categorical columns
`merchant_category` had text values like "Food", "Electronics". Converted them to numbers so the model could understand them.
5. Split the data
80% for training, 20% for testing — split in a way that keeps the fraud ratio equal in both.
6. Balanced the data with SMOTE
Since only 1.51% of transactions are fraud, we used SMOTE to create synthetic fraud samples so the model doesn't just learn to always predict "not fraud".
7. Trained 3 models
Logistic Regression (simple baseline)
Random Forest
XGBoost ✅ (best performer)
8. Evaluated the models
Compared all 3 using Precision, Recall, F1-Score, and ROC-AUC.
9. Built a real-time predictor
A function that takes a single transaction and returns: fraud or not, fraud probability, and how long it took (< 3ms per transaction).
---
Results
Model	F1 Score	ROC-AUC
Logistic Regression	0.43–0.54	0.87–0.91
Random Forest	0.74–0.83	0.95–0.98
XGBoost ✅	0.77–0.86	0.96–0.99
XGBoost won — best across all metrics.
---
Top Features That Predict Fraud
`device_trust_score` — low trust = suspicious
`velocity_last_24h` — too many transactions in a day = suspicious
`risk_score` — a combined score of all risky signals
`log_amount` — unusually high amounts
`location_mismatch` — billing and transaction location don't match
---
How to Run
```bash
# 1. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn joblib

# 2. Download the dataset from Kaggle and place it in the project folder

# 3. Open and run the notebook
jupyter notebook main.ipynb
```
---
Libraries Used
`pandas` · `numpy` · `scikit-learn` · `XGBoost` · `imbalanced-learn` · `matplotlib` · `seaborn` · `joblib`
