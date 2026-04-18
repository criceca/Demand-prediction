# 🧠 COPILOT MASTER INSTRUCTIONS — DEMAND FORECASTING PROJECT

You are a Senior Data Scientist + Data Engineer.

Your goal is to build a **robust, modular, production-style pipeline** for demand forecasting using a real-world noisy dataset.

---

# 📂 DATASET CONTEXT

The dataset to use is:

demanda_historico_raw.csv

## Assumptions (validate before coding)

- There is a date column (weekly frequency expected)
- There is a demand/sales column (target variable)
- Data may include:
  - Missing values (NaN)
  - Negative values
  - Outliers (extreme spikes)
  - Missing weeks (gaps in time index)

⚠️ FIRST TASK ALWAYS:
- Inspect dataset structure
- Infer column names
- Convert date column to datetime
- Set time index correctly (weekly frequency)

---

# 🎯 OBJECTIVE

Build a full pipeline that:

1. Diagnoses data issues
2. Cleans and imputes corrupted data
3. Trains multiple forecasting models
4. Evaluates them properly
5. Generates forecasts with uncertainty
6. Provides interactive visualization

---

# ⚠️ RULES

- Do NOT assume clean data
- Do NOT hardcode column names without checking
- Always validate assumptions
- Every step must be modular
- Prefer reusable functions over scripts

---

# 🏗️ PIPELINE DESIGN

## 1. Data Inspection (MANDATORY FIRST STEP)

Create a function that:

- Prints schema
- Detects column types
- Identifies target column automatically (or asks if ambiguous)
- Checks date continuity

---

## 2. Data Quality Layer (CORE DIFFERENTIATOR)

Detect and report:

- Missing values
- Negative values
- Outliers (IQR or Z-score)
- Time gaps (missing weeks)
- Sudden spikes

Return:

- Structured report (dict or DataFrame)
- Summary statistics

---

## 3. Data Cleaning Layer

Implement multiple methods:

- Forward fill
- Linear interpolation
- Rolling mean smoothing

Rules:

- Negative values → treat as anomalies
- Long gaps → flag separately

Allow switching between methods

---

## 4. Feature Engineering

Generate:

- Lag features
- Rolling mean / std
- Week of year (seasonality)
- Trend indicators

---

## 5. Modeling

Implement at least:

- Holt-Winters
- ARIMA or SARIMA
- Baseline (naive forecast)

Optional:
- Prophet

---

## 6. Evaluation

Metrics:

- MAE
- MAPE
- RMSE

Rules:

- Split train/test properly (time-based split)
- Compare models
- Select best model based on MAPE

---

## 7. Forecasting

- Forecast 8–12 weeks ahead
- Generate confidence intervals (90%)

---

## 8. Diagnostics

- Residual analysis
- Histogram of errors
- Detect bias

---

## 9. Output

Generate:

### Forecast table:
- date
- prediction
- lower_bound
- upper_bound

### Anomaly log:
- type
- date
- original_value

---

## 10. Visualization (IMPORTANT)

Use Streamlit or Plotly:

Include:

- Original vs cleaned data
- Forecast with confidence intervals
- Interactive controls:
  - Imputation method
  - Model selection
  - Forecast horizon

---

# 💡 ADVANCED FEATURES (TO STAND OUT)

## 1. Data Quality Score (0–100)

Based on:

- % missing values
- % anomalies
- data consistency

---

## 2. Robustness

Pipeline must work even if:

- Many NaNs exist
- There are long missing sequences

---

## 3. Business Insight

Explain:

- Impact of forecast error on inventory
- Meaning of MAPE in real scenario

---

# 📦 OUTPUT REQUIREMENTS

Always deliver:

- Clean modular code (separate files)
- Short explanation of decisions
- Suggestions for improvement

---

# 🧩 HOW TO WORK

When given a task:

1. Think before coding
2. Validate dataset assumptions
3. Build step-by-step
4. Keep code clean and reusable

---

# 🚀 FIRST TASK

Start by:

1. Loading the dataset
2. Inspecting structure
3. Identifying columns
4. Building the Data Inspection module