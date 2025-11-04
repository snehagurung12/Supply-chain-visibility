# 📊 Data — Supply Chain Visibility & Predictive Analysis

This folder contains all datasets used throughout the project.  
They are **synthetic, anonymized, and created for academic demonstration only** — replicating real-world supply chain structures such as orders, shipments, and suppliers.

---

## 📁 Folder Structure

Data/
┣ 📁 raw/ # Original input CSVs (source layer)

┣ 📁 clean/ # Processed & joined data for ML + Power BI

┣ 📁 ml-outputs/ # Model predictions (forecast + delays)

┣ 📄 README.md # You're here


---

## 🗃️ Dataset Overview

| Dataset | Folder | Description | Used In |
|----------|---------|--------------|----------|
| **orders.csv** | `/raw/` | All customer orders with product, region, and date details | Power BI & ML |
| **shipments.csv** | `/raw/` | Shipment information incl. status, route, and delivery dates | Power BI & ML |
| **suppliers.csv** | `/raw/` | Supplier performance data (lead time, rating) | Power BI (Suppliers Page) |
| **fact_orders.csv** | `/clean/` | Merged and cleaned orders dataset | Power BI Overview |
| **fact_shipments.csv** | `/clean/` | Shipment-level analytics dataset | Power BI Operations |
| **forecast_fact.csv** | `/ml-outputs/` | ML model output: predicted vs actual demand | Power BI Forecast |
| **shipment_delay_pred.csv** | `/ml-outputs/` | ML output: predicted delay days per shipment | Power BI Risk Insights |

---

## ⚙️ Data Flow Summary

Raw (GitHub CSVs)
↓
Cleaned & merged (Colab notebooks)
↓
ML outputs (forecast + delay)
↓
Power BI report (pbix visuals)


Each stage simulates **Azure Blob zones**:
- `/raw/` → corresponds to `Blob/raw/`
- `/clean/` → corresponds to `Blob/clean/`
- `/ml-outputs/` → corresponds to `Blob/ml-outputs/`

---

## 🧠 Data Dictionary Reference
For detailed column names, data types, and example values,  
see 👉 [`Documentation/Data-Dictionary.md`](../Documentation/Data-Dictionary.md)

---

## 🪶 Notes
- All data are sample or generated for testing, **not confidential**.  
- Versioning is handled through Git commits.  
- Large data files may be uploaded via **Git LFS** if they exceed 100 MB.

---


