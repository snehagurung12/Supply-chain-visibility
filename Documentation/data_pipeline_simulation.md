# 🧮 Data Pipeline Simulation (ETL Flow)


```python
Step 1 — Ingestion
orders = pd.read_csv('Data/raw/orders.csv')
shipments = pd.read_csv('Data/raw/shipments.csv')
Step 2 — Cleaning

Remove duplicates, fix date columns, handle missing supplier data.

Step 3 — Transformation

Create new calculated fields:

LateFlag

DelayDays

OnTime% summary

Step 4 — Merge

Join Orders, Shipments, Suppliers → Unified dataset.

Step 5 — Output

Export processed_data.csv for ML & Power BI.

📘 Equivalent to: Azure Data Factory pipeline → Data Flow → Sink.

---

## 📈 12. `processed_data.csv`
✅ Keep as a small cleaned version (show structure).  
Optional: Create a table in the README showing the first 5 rows (sample data).

---

## 📆 13. `progress_week2.txt`
Replace it with a formatted log:

