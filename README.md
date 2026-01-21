# Naive-Bayes-Beyond-Independence
Naive Bayes analysis showing stable fraud detection performance despite violated independence assumptions (correlated features) on extremely imbalanced Snowflake credit card fraud data. Compares GaussianNB vs 
Logistic Regression & KNN, with recall stability experiments across training data sizes. ​
Analysis showing why Naive Bayes excels in credit card fraud detection despite violated independence assumptions, compared to Logistic Regression and KNN on imbalanced Snowflake data.
​
​


## **Table of Contents**
- About the Project
- Dataset
- Features
- Analysis
- Results
- Installation
- Usage

## **About The Project**
This project demonstrates that Naive Bayes (GaussianNB) maintains stable fraud recall on highly imbalanced data even when features are correlated, violating its core independence assumption.
​
**Key insights from the analysis:**
- Extreme class imbalance (noted as "Extremely imbalanced" in data)
- Strong feature correlations shown via heatmap
- Stable minority-class performance vs flexible discriminative models
​
​


## **Dataset**
- **Source:** Snowflake database (`CREDITCARDFRAUD → CREDITFRAUD` table)  
- **Target:** CLASS (0: normal, 1: fraud) – highly imbalanced  
- **Features:** Numeric transaction features with correlations  
- **Load query:**  
```sql
SELECT * FROM "CREDITFRAUD";​

## **Features**

- Loads data via `snowflake-connector-python`
- EDA includes:
  - `info()`
  - `describe()`
  - Class distribution bar plot
  - Correlation heatmap
- Stratified train-test split: 30% test
- Models:
  - **GaussianNB**: Low-variance, stable under imbalance → Metrics: Confusion matrix, report, ROC-AUC
  - **LogisticRegression**: Convergence issues noted → Metrics: Report, ROC-AUC
  - **KNN (n=5)**: Struggles with local density dominance → Metrics: Report
- Varying training fractions (0.1–0.9) for NB vs LR recall comparison


**## Analysis**

- **Violation test:** Heatmap shows correlations breaking Naive Bayes assumption  
- **Small data experiment:** NB fraud recall stays stable as data grows; LR favors majority class  
- **Plots:** Class distribution bar, correlation heatmap, recall vs data fraction  



**## Results**

- Naive Bayes captures fraud patterns probabilistically despite assumptions, outperforming in imbalance without heavy tuning  
- Discriminative models (Logistic Regression, KNN) need more data or tuning  



**## Installation**

Clone the repo:

git clone https://github.com/yourusername/naive-bayes-beyond-independence.git
cd naive-bayes-beyond-independence
