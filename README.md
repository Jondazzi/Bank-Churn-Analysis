# Bank Customer Churn Prediction
Predicting which bank customers are likely to churn using a 10,000-record customer dataset.
With business recommendations based on model insights.

## Process
- Cleaned 10,000 customer records, removed irrelevant ID columns and age outliers
- EDA to identify churn correlations across geography, gender, age, and account features
- Dropped the 'Complain' feature despite its near-perfect correlation (0.996) with churn
- Compared 4 classification models using F1 score (chosen over accuracy due to class imbalance, only 20.4% of customers churned)
- Tuned XGBoost and HistGradientBoosting with RandomizedSearchCV
- Used churn probability thresholds to flag high-risk customers for the business

## Results
- Final XGBoost model achieved **F1 Score: 0.611**
- Identified 333 customers (16.7% of test set) as high-risk (>70% churn probability)
- Model used to segment churn rate by geography, gender, age, and number of products

## Key Findings
- **Geography:** German customers churn at 32-44%, more than double the rate of France/Spain (~16-20%)
- **Gender:** Female customers churn 1.65x more often than male customers
- **Number of products:** Single-product customers churn at 39%, while two-product customers churn at just 8%
- **High-risk profile:** Middle-aged customers (43-52) with high balances ($65K-$128K) are most likely to be flagged as high-risk

## Business Recommendations
1. Investigate root causes behind elevated German market churn
2. Research potential service/product gaps affecting female customer retention
3. Proactively offer single product customers a second product after around 6 ish months to increase retention
4. Build targeted retention programs for high-balance, middle-aged customers in their peak-value years to avoid loses them to other banks

## Limitations
- Model explains who is likely to churn, not exactly why (need qualitative research for root causes)
- Dataset lacks behavioral features (transaction history, app usage, support interactions) that could improve performance
- Customers with 3-4 products had very small sample sizes (49 and 7) and need further data before drawing conclusions