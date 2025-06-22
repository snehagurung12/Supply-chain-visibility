# 🔄 Data Pipeline Simulation – Supply Chain Project

This document describes how we simulated an Azure-like cloud data pipeline using *Google Colab, **Pandas, and **GitHub*, tailored to the supply chain dataset used in this project.

---

## 🧭 Azure Architecture Mapping

| Azure Service             | Simulated Using              | Description |
|---------------------------|-------------------------------|-------------|
| Azure Blob Storage        | GitHub + Colab File System    | Used for storing raw and cleaned datasets |
| Azure Data Factory        | Pandas in Google Colab        | Handles ingestion, transformation, filtering |
| Azure SQL Database        | Pandas DataFrame              | Temporary in-memory data storage |
| Azure Logic Apps / Triggers | Python manual function       | Simulated pipeline trigger |
| Power BI                  | Power BI Desktop (by teammate) | For dashboard and visualization |

---

## 🔁 Pipeline Flow (Step-by-Step)

1. *Upload Raw Dataset*
   - Uploaded using files.upload() in Colab.
   - Optional: load via GitHub raw link for automation.

2. *Clean and Filter Data*
   - Removed null values using dropna().
   - Filtered for rows where shipment_status == "delivered".
   - Converted date columns to datetime.
   - Sorted rows by order_date.

3. *Export Results*
   - Saved cleaned dataset as cleaned_supply_data.csv.
   - Exported to supply_table.html for website/dashboard integration.

---

## 📂 Project Files

| File | Description |
|------|-------------|
| [simulate_pipeline.ipynb](../pipeline/simulate_pipeline.ipynb) | Full Google Colab notebook |
| [cleaned_supply_data.csv](../pipeline/cleaned_supply_data.csv) | Cleaned and processed data |
| [supply_table.html](../pipeline/supply_table.html) | Converted HTML table |

---

## 🚀 Future Expansion

- Use GitHub raw CSV instead of manual upload.
- Automate trigger using scheduled Python scripts.
- Deploy as a web app using Streamlit or Flask.

---

## ✅ Conclusion

This simulation shows how Azure-like data pipelines can be designed and explained without using a paid cloud environment. The architecture and execution follow cloud standards, making this ideal for learning and showcasing Solution Architect skills.
