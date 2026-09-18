# ML Practical Code

Machine Learning practical exercises — all seven algorithms in one notebook, with comments and saved outputs.

## Download the notebook

**[cheeseballs.ipynb](https://github.com/beerus-Ai/ml-practical-code/releases/download/v1.0/cheeseballs.ipynb)** — click to download

Or [view it rendered on GitHub](cheeseballs.ipynb).

## Contents

| Exercise | Dataset | Metric |
|---|---|---|
| Linear Regression | mba_salary_data | R² = 0.950 |
| Logistic Regression | german_credit_risk | Accuracy = 0.70 |
| Decision Tree | Iris | Accuracy = 1.00 |
| Random Forest | wine | Accuracy = 1.00 |
| KNN | Customer_Churn_Dataset | Accuracy = 0.63, best K = 15 |
| Sentiment Analysis | tweets_dataset | Accuracy = 0.56 |
| ARIMA | tourism_data_2005_onwards | MAPE = 6.22% |

`cheeseballs.ipynb` runs everything from the repo root. Each exercise also has its own notebook inside its folder.

## Requirements

```
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels wordcloud
```

## Notes

- **Sentiment accuracy is ~56%** because the labels in `tweets_dataset.csv` are mislabelled (e.g. "I love this product! It's amazing." is tagged negative). The code is correct; the data is not.
- **KNN accuracy is 63%**, but predicting "No churn" for everyone already scores 63% — use recall on the churn class to evaluate it properly.

`ML_Practical_Cheatsheet.html` is the same code as a single-page reference.
