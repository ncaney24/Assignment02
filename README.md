# EECE 5644 - Assignment #02: Telco Monthly Charge Prediction

## What this project does
Builds a multivariable linear regression model to predict a Telco customer's
monthly charge based on which optional add-on services they subscribe to.
The model learns an individual dollar contribution for each of 10 services
and answers 8 practical billing questions for the revenue team.

## Dataset
`telco.csv` - 7,043 rows, pre-cleaned from the Telco Customer Churn dataset.
The file is included in this repository so no Kaggle download is needed.

The target column is `target` (MonthlyCharges). The 10 predictor columns are
all binary 0/1 service indicators: PhoneService, MultipleLines, OnlineSecurity,
OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies,
InternetService_Fiber optic, InternetService_No.

## How to run

### Google Colab (recommended)
1. Upload `Assignment_02_Telco.ipynb` to Colab
2. Run the first cell - it installs all dependencies automatically
3. When the `files.upload()` cell runs, upload `telco.csv`
4. Run all cells top to bottom (Runtime → Run all)
5. Three chart PNGs will be saved to the Colab file browser

### Locally
```bash
git clone <your-repo-url>
cd <repo-folder>
pip install -r requirements.txt
jupyter notebook Assignment_02_Telco.ipynb
```

## Repository structure

```
├── Assignment_02_Telco.ipynb       # main notebook - all 9 requirements
├── findings_summary_A02.md         # one-page summary answering all 8 questions
├── telco.csv                       # input dataset
├── chart_actual_vs_predicted.png   # actual vs predicted scatter (run to generate)
├── chart_model_comparison.png      # R2 comparison bar chart (run to generate)
├── chart_coefficients.png          # coefficient bar chart (run to generate)
├── requirements.txt
└── README.md
```

## Key results

| Metric | Single-variable model | Multivariable model |
|--------|-----------------------|---------------------|
| R2 | 0.599 | **0.999** |
| MAE | $16.97 | **$0.79** |
| RMSE | $19.06 | **$1.05** |

- Base plan cost (intercept): **$24.97/mo**
- Most expensive add-on: **Fiber optic internet (+$24.95/mo)**
- Cheapest add-on: **OnlineBackup (+$4.98/mo)**
- Knowing *which* services a customer has is far more accurate than
  just knowing *how many* — R2 jumps from 0.599 to 0.999
