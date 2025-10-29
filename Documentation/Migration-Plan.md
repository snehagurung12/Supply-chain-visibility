# ☁️ Migration Plan — Free Simulation → Azure Cloud

This document describes how the current free-tool implementation can be migrated into a full-scale Azure environment.

## 🎯 Objective
To migrate the current free-tool simulation into a scalable Azure-based supply chain analytics solution.

---

## 🗃️ Step 1: Data Storage (GitHub → Blob Storage)
- Create containers: `raw/`, `clean/`, `ml-outputs/`
- Upload datasets
- Enable SAS URLs for Power BI connections

---

## ⚙️ Step 2: Data Factory Pipelines
- Pipeline 1: Copy raw → clean
- Pipeline 2: Run Colab equivalent via Azure ML Notebook activity
- Pipeline 3: Export ML results → `ml-outputs/`

---

## 🧠 Step 3: Synapse Analytics
- Create external tables on Blob datasets
- Design fact and dimension tables (`OrdersFact`, `SupplierDim`)
- Use SQL views for Power BI connections

---

## 📊 Step 4: Power BI Service
- Connect to Synapse SQL endpoint
- Enable incremental refresh
- Publish dashboards to Power BI workspace

---

## 🔄 Step 5: Automation & Cost Optimization
- Schedule daily ADF refresh
- Use Synapse Serverless (pay-per-query)
- Host ML models via Azure Functions

✅ *End result:* Fully cloud-native, automated supply chain analytics system.
