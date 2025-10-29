# 🏗️ Architecture Diagram — Supply Chain Visibility Project

This project follows an **Azure-inspired architecture** simulated using **free tools**.

---

## 🔹 Logical Architecture Overview
**Flow:**  
**Data Source (CSV/GitHub)** ➜ **Google Colab (Cleaning & ML)** ➜ **Processed CSVs** ➜ **Power BI Dashboard**

---

## 🔸 Azure Equivalent Flow
**Azure Blob Storage** ➜ **Data Factory** ➜ **Synapse Analytics** ➜ **Power BI Service**

---

## 🧩 Layer Description
| Layer | Tool Used | Azure Equivalent | Description |
|-------|------------|------------------|-------------|
| Ingestion | GitHub Repo | Blob Storage | Store raw data |
| Processing | Google Colab (Pandas) | Data Factory | Data cleaning & transformation |
| Analytics | Colab (Scikit-learn) | Synapse / Azure ML | Predictive modeling |
| Visualization | Power BI Desktop | Power BI Service | Dashboards & KPIs |

---

## 📊 Diagram Reference
The diagram `SCV_Architecture.png` in `/Architecture` folder visually represents this flow.
