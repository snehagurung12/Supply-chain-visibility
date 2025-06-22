# Simulated Azure Cloud Pipeline for Supply Chain Project

This document describes how we simulated Azure data processing using free tools.

## 🎯 Purpose
To mimic a real Azure pipeline (ADF, Blob Storage, SQL) using Google Colab and Pandas.

---

## 🛠 Tools Used

| Azure Component       | Simulated With           |
|-----------------------|---------------------------|
| Azure Blob Storage    | GitHub + Local Files      |
| Azure Data Factory    | Pandas in Google Colab    |
| Azure SQL DB          | Pandas DataFrame          |
| Power BI              | (Handled by teammate)     |

---

## 🔁 Pipeline Flow (Simulated)

1. *Data Ingestion*  
   - Uploaded raw CSV using files.upload() in Colab.

2. *Data Cleaning*  
   - Removed null values.
   - Filtered for shipment_status = 'delivered'.
   - Converted date columns to datetime.
   - Sorted by order date.

3. *Data Storage*  
   - Exported cleaned data to CSV (cleaned_supply_data.csv).
   - Exported HTML table (supply_table.html) for frontend/dashboard use.

---

## 📤 Outputs

- cleaned_supply_data.csv: Final processed dataset.
- supply_table.html: Table ready for embedding into a web dashboard.
- simulate_pipeline.ipynb: The full notebook with all logic.

---
