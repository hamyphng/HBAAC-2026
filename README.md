# HBAAC 2026 — Data Modeling Hackathon

Predict **daily sales quantity** for **15,972 SKUs** of a Vietnamese Auto Parts distributor  
over a **56-day horizon** (2025-09-06 → 2025-10-31).

**Metric:** WRMSSE (Weighted Root Mean Squared Scaled Error) — lower is better.

## Quick Start

```bash
# 1. Install dependencies
python -m venv venv && venv\Scripts\activate    # Windows
pip install -r requirements.txt

# 2. Download data
kaggle competitions download -c hbaac-round2 -p data/raw/

# 3. Run code
python src/forecast_v3.ipynb
```

---

## Leaderboard Info

| Split   | Days        | Purpose             |
|---------|-------------|---------------------|
| Public  | F1–F28      | Validation feedback |
| Private | F29–F56     | Final ranking       |
