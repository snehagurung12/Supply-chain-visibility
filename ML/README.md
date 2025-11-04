# 🧠 Machine Learning — Supply Chain Visibility & Predictive Analysis

This folder contains all machine learning-related assets for the project.  
It includes model training scripts, exported predictions, evaluation metrics, and plots used in the Power BI **Forecast** and **Delay Risk** pages.

---

## 📁 Folder Structure

ML/

├─ notebooks/ # development & training

│ ├─ 01_features_delay.ipynb

│ └─ 02_forecast_demand.ipynb

├─ models/ # optional: saved models / model cards

├─ outputs/ # ⬅ Power BI reads these

│ ├─ shipment_delay_pred.csv

│ └─ forecast_fact.csv

├─ metrics/ # evaluation artifacts (JSON/CSV)

│ ├─ delay_regression.json # {rmse, mae, r2}

│ └─ forecast_metrics.json # {mape, rmse, r2}

├─ visuals/ # charts exported from notebooks

└─ README.md



---

## 🎯 Objectives

- **Delay regression:** predict `DelayDays` for each shipment using route, distance, supplier lead time, etc.
- **Demand forecast:** predict upcoming order volume at month/region/category granularity.

---

## 🔄 Workflow

Data/clean → ML/notebooks (feature, train, eval) → ML/outputs/*.csv → Power BI

Inputs expected:
- `Data/clean/fact_shipments.csv`
- `Data/clean/fact_orders.csv`
- `Data/clean/dim_suppliers.csv`
- `Data/clean/dim_calendar.csv`

Outputs produced:
- `ML/outputs/shipment_delay_pred.csv`
- `ML/outputs/forecast_fact.csv`

---

## 🧮 Models & Metrics

| Task | Model | Key Features | Target | Metrics (saved in /metrics) | Output |
|---|---|---|---|---|---|
| Delay Prediction | RandomForestRegressor | DistanceKM, LeadTimeDays, SupplierRating, Route, Month | DelayDays | `rmse`, `mae`, `r2` → `delay_regression.json` | `shipment_delay_pred.csv` |
| Demand Forecast | (your choice) e.g., XGBoost / DT / SARIMAX | Month, Region, Category, Lag features | Next-period Orders | `rmse`, `mape`, `r2` → `forecast_metrics.json` | `forecast_fact.csv` |

> **Tip:** Use calendar joins to add `Month`, `Year`, `Season`, and lag features.

---

## 🧪 Minimal example (pseudo-code)

```python
import pandas as pd, numpy as np
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score

ship = pd.read_csv('Data/clean/fact_shipments.csv')
X = ship[['DistanceKM','LeadTimeDays','SupplierRating']].fillna(0)
y = ship['DelayDays'].fillna(0)

rf = RandomForestRegressor(n_estimators=200, random_state=42)
rf.fit(X, y)

pred = rf.predict(X)
rmse = mean_squared_error(y, pred, squared=False)
mae  = mean_absolute_error(y, pred)
r2   = r2_score(y, pred)

pd.DataFrame({
    'ShipmentID': ship['ShipmentID'],
    'DelayDays': y,
    'PredictedDelay': pred
}).to_csv('ML/outputs/shipment_delay_pred.csv', index=False)

pd.Series({'rmse': rmse, 'mae': mae, 'r2': r2}).to_json('ML/metrics/delay_regression.json')
🔗 Power BI Integration

Operations / Risk pages → ML/outputs/shipment_delay_pred.csv

Forecast page → ML/outputs/forecast_fact.csv (columns: Date, Actual, Forecast, optional Lower, Upper)

After you run notebooks, open the PBIX:

Transform Data → Data source settings → Change Source to ML/outputs/… (once).

Refresh → visuals update automatically.

☁️ Azure Upgrade (later)
| Function           | Azure service                    |
| ------------------ | -------------------------------- |
| Notebook execution | Azure ML / Synapse Spark         |
| Model registry     | Azure ML Registry                |
| Batch scoring      | ADF Pipeline (notebook activity) |
| Output storage     | Blob `ml-outputs/`               |
| BI                 | Power BI Service / Fabric        |

📜 Notes

Synthetic / anonymized data only; for academic/portfolio use.

Keep random seeds fixed for reproducibility.

If outputs grow large, track with Git LFS.

---

# 📄 `ML/models/README.md` — (optional) copy-paste

```markdown
# models/

Optional folder for persisted models and model cards.

- Store `.pkl` files only if needed.
- Prefer rebuilding models from notebooks for transparency.
- Include a short **MODEL_CARD.md** per model (data, features, metrics, caveats).
