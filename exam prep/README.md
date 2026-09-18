# Exam Prep — ITS2209 Machine Learning for Business

Built from the **September 2025 end-term paper** (`Machine Learning (2024-26).pdf`).
One notebook per question, matching the paper's structure and mark allocation.

## Files

| File | Question | Marks | Topic |
|---|---|---|---|
| `Q1.ipynb` | Q1 (a + b) | 15 | Boston Housing — pre-processing + **multiple** linear regression |
| `Q2.ipynb` | Q2 | 10 | Loan Prediction — decision tree classifier |
| `Q3.ipynb` | Q3 | 12.5 | IMDB Reviews — TF-IDF / CountVectorizer + logistic regression |
| `Q4.ipynb` | Q4 | 12.5 | Airline Passengers — ARIMA forecasting |

`Data_Q1.csv` … `Data_Q4.csv` are **stand-in datasets I generated** with the exact shapes
the paper specifies (506×14, 614×13, 2599×2, 144×2) so every notebook runs today.
In the exam, replace them with the real files from the LMS.

## On exam day

Each notebook starts with a **Settings** cell. That is the only cell you edit:

```python
CSV_FILE = "Data_Q1.csv"    # the file they give you
TARGET   = "MEDV"           # the target column
TEST_SIZE = 0.35            # the split the question asks for
```

Then Run All.

### Saving as HTML (the paper requires this)

> *"you must create a separate Python code file for each question and save it in
> executable HTML format using the question number as the file name"*

```bash
jupyter nbconvert --to html Q1.ipynb
```

Run all four, then put `Q1.html`–`Q4.html` in one folder named
`YourName_YourRollNumber`.

Run the notebook **before** exporting — nbconvert saves whatever outputs are in the
file, so an unexecuted notebook exports as code with no results.

## What each notebook covers

**Q1** — missing values (median/mode) · StandardScaler · correlation heatmap ·
65/35 split · multiple linear regression · coefficient table · **MSE, RMSE, MAE, R²** ·
Actual vs Predicted scatter with 45° line · residual plot

**Q2** — drop ID · missing values · target Y/N → 1/0 · one-hot encoding ·
60/40 stratified split · decision tree (`max_depth=4` so the plot stays readable) ·
**accuracy, precision, recall, F1** · confusion matrix heatmap · `plot_tree` · feature importances

**Q3** — 70/30 stratified split · **TF-IDF and CountVectorizer** (the paper allows either,
both are here) · logistic regression · **accuracy, precision, recall, F1** ·
confusion matrix · most positive/negative words · predicting a new review

**Q4** — datetime index · series plot · `seasonal_decompose` · **ADF stationarity test** ·
chronological split (never `train_test_split`) · ARIMA(1,1,1) · **MAPE** ·
forecast vs actual plots · SARIMA comparison

## Things worth saying in the written answers

- **Scaling:** needed for linear regression coefficients, logistic regression and KNN.
  Not needed for trees — they split on thresholds, so units are irrelevant.
- **`fit_transform` on train, `transform` on test.** Fitting on test data leaks information.
- **Time series are never shuffled.** `train_test_split` would let the model see the future.
- **Accuracy alone can mislead** on imbalanced data — quote recall or F1 on the minority class.
- **Plain ARIMA has no seasonal term**, so its forecast is smoother than reality. SARIMA fixes this.
  In this notebook SARIMA cuts MAPE from ~12% to ~3%.

## Note on the sample results

`Q3` scores 1.00 on my stand-in data because those reviews were generated from
templates and are trivially separable. Real IMDB data lands around **85–90%**.
Don't quote the 1.00 as a realistic figure.
