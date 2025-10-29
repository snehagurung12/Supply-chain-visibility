# 🖥️ Usage Guide

### 💡 Power BI Dashboard
- Open `PowerBi/SCV_Report.pbix`
- Refresh connections to `/Data/clean/`
- Explore:
  - **Overview Page:** High-level KPIs
  - **Suppliers Page:** Performance matrix
  - **Forecast Page:** Actual vs Predicted trends

### 🧠 Machine Learning Results
- Output: `/ML/outputs/forecast_fact.csv`
- Columns: Date, Actual, Forecast, Error
- Metrics shown in Power BI (RMSE, MAE, R²)

### 🌩️ Cloud Simulation
- Equivalent flow: GitHub → Colab → Power BI (→ Azure in future)
