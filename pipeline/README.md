# 🔄 Data Pipeline — Supply Chain Visibility & Predictive Analysis

This module simulates the **Azure Data Factory pipeline** using free tools (Google Colab / Jupyter Notebook).  
It represents the **ETL process** — Extract, Transform, Load — for all datasets used in this project.

---

## 🎯 Objective

To replicate an end-to-end **Azure Data Factory (ADF)** workflow using **Python (Pandas)** and **Google Colab**, transforming raw CSVs into clean, analytics-ready datasets consumed by Power BI and Machine Learning models.

---

## 🧱 Pipeline Overview

| Stage | Description | Equivalent Azure Activity | Output |
|--------|-------------|----------------------------|---------|
| **Extract** | Import raw CSVs from GitHub `/Data/raw/` | Copy Data | Raw dataframes |
| **Transform** | Clean missing values, merge datasets, derive new fields | Mapping Data Flow | `cleaned_supply_data.csv` |
| **Feature Engineering** | Add calculated flags (LateFlag, DelayDays, OnTime%) | Data Flow Script | `supply_table.html` preview |
| **Load / Export** | Write clean data for Power BI + ML | Sink Activity | `/Data/clean/` and `/ML/inputs/` |
| **Visual Check** | Display HTML summary tables | Synapse / Notebook Activity | `supply_table.html` |

---

## ⚙️ How It Works

### 1️⃣ Load & Inspect Data
```python
import pandas as pd
orders = pd.read_csv('../Data/raw/orders.csv')
shipments = pd.read_csv('../Data/raw/shipments.csv')
suppliers = pd.read_csv('../Data/raw/suppliers.csv')

print(orders.shape, shipments.shape, suppliers.shape)

2️⃣ Clean & Merge

Handle missing or inconsistent values

Convert dates to datetime

Remove duplicates

Standardize column names

Merge datasets on OrderID and SupplierID
merged = (orders
    .merge(shipments, on='OrderID', how='left')
    .merge(suppliers, on='SupplierID', how='left'))
merged.to_csv('cleaned_supply_data.csv', index=False)

3️⃣ Add Calculated Fields
merged['DelayDays'] = (pd.to_datetime(merged['DeliveredDate']) - 
                       pd.to_datetime(merged['ShipDate'])).dt.days
merged['LateFlag'] = merged['DelayDays'].apply(lambda x: 1 if x > 0 else 0)

4️⃣ Export and Visualize
from IPython.display import HTML
HTML(merged.head(10).to_html('supply_table.html'))


Outputs:

🧾 cleaned_supply_data.csv → used by ML & Power BI

📊 supply_table.html → quick preview of final data

📈 Pipeline Flow Diagram (concept)

GitHub /Data/raw/
       ↓
simulate_pipeline.ipynb
       ↓
cleaned_supply_data.csv
       ↓
ML/ & PowerBi/ datasets
Equivalent Azure flow:
Blob → Data Factory → Synapse → Power BI

🧩 Key Transformations

| Column         | Description                | Logic                                 |
| -------------- | -------------------------- | ------------------------------------- |
| `LateFlag`     | Delay indicator            | 1 if DeliveredDate > ShipDate else 0  |
| `DelayDays`    | Number of delayed days     | DeliveredDate - ShipDate              |
| `OnTime%`      | Shipment performance ratio | (1 - LateFlag avg) * 100              |
| `CostCategory` | Based on total amount      | Derived using bins (<500 = Low, etc.) |


🧠 How It Connects

The cleaned_supply_data.csv file becomes the base for ML training.

The same output feeds into Power BI Overview and Operations pages.

Acts as a simulation of Azure Data Factory pipelines without any cost.

☁️ Azure Migration Equivalent

| Current Tool           | Azure Service            | Function                       |
| ---------------------- | ------------------------ | ------------------------------ |
| Google Colab / Jupyter | Azure Data Factory (ADF) | Orchestration & transformation |
| CSV in GitHub          | Blob Storage             | Raw data storage               |
| Pandas Cleaning        | ADF Mapping Data Flow    | Data transformation            |
| CSV Export             | Synapse SQL Output       | Clean zone output              |
| HTML Summary           | Power BI Data Preview    | Validation layer               |


🪶 Notes

This is a fully offline, cost-free simulation of Azure pipelines.

The notebook simulate_pipeline.ipynb can be rerun anytime for reproducibility.

Each step is modular and maps directly to ADF pipeline activities.

Data is synthetic and used only for academic and portfolio purposes.

💡 This pipeline transforms simple CSVs into business-ready insights — mirroring how Azure Data Factory automates enterprise data flows.

---

### ✅ Summary

| File | Role |
|------|------|
| `simulate_pipeline.ipynb` | The main ETL simulation (Colab/Jupyter notebook) |
| `cleaned_supply_data.csv` | Output file used for analytics |
| `supply_table.html` | Quick preview of cleaned table |
| `README.md` | Explains pipeline and Azure mapping |

---
