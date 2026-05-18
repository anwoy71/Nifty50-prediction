#  NIFTY50 Prediction

Financial ML project for predicting next-day NIFTY50 direction using engineered time-series features and walk-forward validation.

## Objective

Build a leakage-aware binary classification pipeline to predict whether the next trading day's NIFTY50 closing price will move up or down.

The project prioritizes:
- leakage prevention
- walk-forward validation
- conservative modeling
- robustness over aggressive optimization

---

## Repository Structure

```text
-Nifty50-prediction/
│
├── notebooks/
│   ├── 01_data_clean_align.ipynb
│   ├── 02_feature_dataset.ipynb
│   └── 03_modeling_walkforward.ipynb
│
├── data/
│   ├── raw_data/
│   │   ├── nifty50.csv
│   │   ├── banknifty.csv
│   │   ├── indiavix.csv
│   │   └── starter_features.csv
│   │
│   └── processed_data/
│       ├── master_dataframe.csv
│       └── final_model_dataset.csv
│
├── README.md
├── LICENSE
├── requirements.txt
└── ProjectReportFinal_Anwoy.pdf
```

---

## Workflow

### 1. Data Cleaning & Alignment
- Standardized timestamps
- Chronological sorting
- Leakage-safe alignment
- Target generation using next-day direction

### 2. Feature Engineering
- Momentum features
- Volatility features
- VIX regime features
- Cross-market relative strength
- NaN-aware feature filtering

### 3. Modeling & Validation
- XGBoost classifier
- Walk-forward validation
- TimeSeriesSplit
- Threshold analysis
- Trading backtest evaluation

---

## Final Feature Set

- ret_1d
- ret_overnight
- ret_5d
- close_vs_ma5
- momentum_5_20
- vol_20d
- vix_change
- vix_ma_ratio
- bn_ret_1d
- nifty_bn_spread
- ret_zscore
- high_low_range

---

## Validation Approach

To avoid look-ahead bias:
- chronological train/test splitting was used
- walk-forward validation was applied
- rolling features were verified to be backward-looking
- random shuffling was avoided

---

## Main Results

- OOS Accuracy: 54.4%
- Balanced Accuracy: 53.36%
- AUC: 0.5336
- Sharpe Ratio (after costs): 0.9198
- Hit Rate: 50.4%
- Max Drawdown: -0.04%

The model outperformed the majority-class baseline but remained below the persistence baseline, highlighting the difficulty of extracting stable short-term edge from financial time-series data.

---

## Notes

This project intentionally emphasizes:
- leakage awareness
- validation rigor
- reproducibility
- conservative interpretation of results

rather than maximizing backtest performance.

---

## Author

Anwoy Datta
