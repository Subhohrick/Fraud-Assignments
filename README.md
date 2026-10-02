Fraud Detection: Sampling, Feature Selection & Anomaly Detection

Exploratory analysis of financial transaction data to understand what separates fraudulent transactions from normal ones. The project covers data sampling techniques, data quality checks, statistical feature selection, outlier detection, and unsupervised anomaly detection with DBSCAN.

Built as part of the MBA (Data Science & Analytics) coursework at Symbiosis Centre for Information Technology (SCIT), Pune.

Dataset

Fraud_Detection_Dataset.csv has about 51,000 transactions and 12 columns:

Column	Description
Transaction_ID, User_ID	Identifiers
Transaction_Amount	Value of the transaction
Transaction_Type	ATM Withdrawal, Bank Transfer, Bill Payment, Online Purchase, POS Payment
Time_of_Transaction	Hour of the day (0–23)
Device_Used	Desktop, Mobile, Tablet, Unknown Device
Location	8 US cities
Previous_Fraudulent_Transactions	Prior fraud count for the user
Account_Age	Age of the account
Number_of_Transactions_Last_24H	Recent activity level
Payment_Method	Credit Card, Debit Card, UPI, Net Banking, Invalid Method
Fraudulent	Target: 1 = fraud, 0 = normal

The data is imbalanced: only about 5% of transactions are fraudulent. About 5% of values are missing in each of five columns, and the dataset contains duplicate records.

Notebooks
FDCH1.ipynb: Sampling & Feature Selection
Sampling techniques: partition (70%), simple random, stratified (by Location), and cluster sampling
Data preparation: median and mode imputation, label encoding of categorical columns
Feature selection: correlation matrix heatmap and Chi-Square test (SelectKBest)
Train/test split: 70/30, stratified on the target to preserve the fraud ratio
FDCH_2.ipynb: EDA, Outliers & Anomaly Detection
Missing-value percentage and duplicate checks
Fraud class distribution and transaction amount distribution plots
Correlation heatmap of numeric features
Outlier detection with box plots and the IQR method
Common and uncommon value analysis for categorical columns
DBSCAN clustering on scaled features. Points labelled -1 are flagged as anomalies and visualised against normal clusters.
Key Findings
Chi-Square test: Transaction_Amount, Account_Age, Time_of_Transaction and Location are significantly related to fraud (p < 0.05). Device, payment method and previous fraud count show no significant relationship.
Rare values: Unknown Device and Invalid Method each appear in only about 3% of rows. Their fraud rate is no higher than the overall rate, so they look like data-quality flags rather than fraud signals.
Most categorical columns, such as location and transaction type, are spread almost evenly across their values.
Tech Stack

Python · pandas · NumPy · Matplotlib · Seaborn · scikit-learn · imbalanced-learn

How to Run
bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
Clone the repository and keep Fraud_Detection_Dataset.csv in the same folder as the notebooks.
Open the notebooks in Jupyter or VS Code and run the cells from top to bottom.
Next Steps
Handle class imbalance with SMOTE, ADASYN or random oversampling
Train and compare classification models such as Logistic Regression, Decision Tree and Random Forest
Evaluate with precision, recall, F1-score and ROC-AUC, since accuracy is misleading for imbalanced data# Fraud-Assignments
