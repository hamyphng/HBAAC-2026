# HBAAC 2026 — Data Modeling Hackathon

Predict **daily sales quantity** for **15,972 SKUs** of a Vietnamese Auto Parts distributor  
over a **56-day horizon** (2025-09-06 → 2025-10-31).

**Metric:** WRMSSE (Weighted Root Mean Squared Scaled Error) — lower is better.

---

## Project Structure

```
hbaac-2026/
├── configs/
│   ├── config.yaml       ← hyperparameters & paths
├── data/
│   ├── raw/              ← Kaggle CSVs (gitignored)
│   ├── processed/        ← Parquet cache (gitignored)
│   └── external/         ← holidays, macroeconomic signals
├── models/               ← saved .pkl checkpoints
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_feature_engineering.ipynb
│   └── 03_modeling.ipynb
├── src/
│   ├── __init__.py
│   ├── data_loader.py    ← load + melt + merge
│   ├── features.py       ← lags, rolling, calendar, price
│   ├── model.py          ← LightGBM train + recursive forecast
│   ├── evaluate.py       ← WRMSSE metric
│   └── utils.py          ← helpers, plotting, SHAP
├── configs/config.yaml   ← hyperparameters & paths
├── output/               ← submission CSVs
```

---

## Quick Start

```bash
# 1. Install dependencies
python -m venv venv && venv\Scripts\activate    # Windows
pip install -r requirements.txt

# 2. Download data
kaggle competitions download -c hbaac-round2 -p data/raw/

# 3. Build dataset
python src/data_loader.py

# 4. Train + submit
python src/model.py
```

---

## Leaderboard Info

| Split   | Days        | Purpose             |
|---------|-------------|---------------------|
| Public  | F1–F28      | Validation feedback |
| Private | F29–F56     | Final ranking       |