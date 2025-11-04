<h1 align="center">🌐 Supply Chain Visibility & Predictive Analysis</h1>
<h3 align="center">🔹 Free-Tools Simulation → Azure Cloud Migration Ready 🔹</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10-blue?logo=python"/>
  <img src="https://img.shields.io/badge/Power%20BI-Analytics-yellow?logo=powerbi"/>
  <img src="https://img.shields.io/badge/Azure-Ready-blue?logo=microsoftazure"/>
  <img src="https://img.shields.io/badge/License-MIT-green"/>
</p> 

---

## 🚀 **Project Overview**

This project showcases a **real-world supply chain analytics system** built entirely with **free tools** (Google Colab + Power BI + GitHub) while **simulating Azure Cloud architecture**.  
It provides complete **visibility**, **predictive insights**, and **performance analytics** — all ready for direct migration to Azure services.

🎯 **Goal:** Demonstrate how powerful cloud-inspired architectures can be built cost-free — ideal for students, analysts, and cloud architects.

---

## 🧩 **Why This Project Matters**
> _“In supply chains, visibility is power.”_

Enterprises often lack integrated data and forecasting capabilities.  
This project bridges that gap by:

✅ Creating a **single source of truth** for orders, shipments, and suppliers  
✅ Predicting **shipment delays** and **demand fluctuations**  
✅ Providing **real-time dashboards** for smarter decision making  
✅ Using **Azure-equivalent architecture** with 100% free tools  

---

## 🏗️ **Tech Stack & Architecture**

| Layer            | Free Tools (Simulation)        | Azure Equivalent          |
| ---------------- | ------------------------------ | ------------------------- |
| Data Storage     | GitHub `/Data/`                | Blob Storage (ADLS Gen2)  |
| ETL / Pipeline   | Google Colab (Pandas + Python) | Azure Data Factory        |
| Data Warehouse   | CSV / Parquet                  | Synapse Analytics         |
| Machine Learning | Scikit-Learn in Colab          | Azure ML / Synapse ML     |
| Visualization    | Power BI Desktop               | Power BI Service / Fabric |
 
---

## 🧩 Azure-Inspired Architecture

![Azure Architecture Diagram](Architecture/AzureArchitecture_SupplyChain.png)

*Figure: Azure Data Architecture for Supply Chain Visibility*

This diagram illustrates how raw supply chain data (e.g., from CSV files) flows through Azure services — starting from Blob Storage, processed by Data Factory, transformed in Synapse Analytics, and visualized in Power BI. The final dashboard offers insights into delays, inventory, and costs for improved decision-making.
> The architecture includes:
> - Azure Blob Storage for raw data upload  
> - Google Colab for ETL and predictive modeling  
> - Power BI for data visualization  
> - GitHub for version control and collaboration

---

## Free tools → Azure mapping
| Capability            | Free-tools now                          | Azure later (planned)              |
|---|---|---|
| Object storage        | GitHub repo (small CSVs)               | Blob Storage containers            |
| Orchestration         | Colab notebook steps + README          | Azure Data Factory pipelines       |
| Transform/warehouse   | Pandas in Colab                        | Synapse Serverless/Dedicated SQL   |
| ML training/inference | Scikit-learn in Colab                  | Azure ML / Synapse ML              |
| BI                    | Power BI Desktop                       | Power BI Service (workspaces)      |

---

🧠 Key Components
🏗️ 1. Data Pipeline (/pipeline)

Cleans and merges raw CSVs

Creates derived metrics like DelayDays, LateFlag

Outputs cleaned_supply_data.csv used in ML & Power BI

🤖 2. Machine Learning (/ML)

Predicts shipment delays (Random Forest Regressor)

Forecasts monthly demand (Decision Tree Classifier)

Exports forecast_fact.csv & shipment_delay_pred.csv

📊 3. Power BI Dashboard (/PowerBi)

5 pages: Overview, Operations, Suppliers, Live Tracking, Forecast

Uses DAX measures (see Add MEASURES.md)

Integrates ML outputs for predictive visuals

📘 4. Documentation (/Documentation)

Full project report, presentation guide, migration plan

Data dictionary and architecture references

☁️ 5. Architecture (/Architecture)

Visual diagrams of data flow, deployment topology, and zones

Architecture-Mapping.md shows free tools → Azure service parity
---

## 🎯 Project Goals
- Enhance transparency across the supply chain
- Predict delivery risks and delays before they happen
- Visualize performance metrics through interactive dashboards
- Use mostly free / accessible tools (Google Colab, Power BI, Azure Free Tier)

---

## 📊 Highlights from EDA
- *Delivery Status:* Many orders delayed — investigate shipping, product, region causes.
- *Order Types:* Payments & Expenses dominate; digital-first flow.
- *Shipping Methods:* Mostly Standard Class — opportunity to optimize for speed vs cost.
- *Customer Segments:* Balanced Consumer & Corporate, small Home Office niche.
- *Correlations:* Delays linked with risk and discounts — ideal for predictive models.
- *Seasonality:* Monthly fluctuations show demand cycles.

---

## ⚙ Features
- Upload & store datasets in Azure Blob
- Simulate ETL pipeline in Python notebooks
- Run predictive analyses (risk, delays)
- Build interactive dashboards in Power BI
- Collaborate via GitHub with a modular structure

---

## 🏗 Deployment Pipeline Overview

![Deployment Diagram](Architecture/deployment_architecture.png)

- **Data Ingestion**: CSVs uploaded to GitHub
- **Preprocessing & ML**: Performed in Colab (null handling, feature engineering, model training)
- **Model Output**: Exported `.csv` of forecasts merged with actuals
- **Visualization**: Dashboard in Power BI with slicers, KPI cards, forecast tooltips

---

## 💫 **Power BI Dashboard Pages**

| Page | Purpose | Highlights |
|------|----------|-------------|
| **1️⃣ Overview** | Executive summary | KPIs, trends, and region filters |
| **2️⃣ Operations** | Process tracking | In-transit vs delivered metrics, risk alerts |
| **3️⃣ Suppliers** | Performance ranking | Conditional formatting, late rate, fulfillment |
| **4️⃣ Live Tracking** | Control tower | Status filters with hover animations |
| **5️⃣ Forecast** | Predictive analytics | Actual vs Forecast lines + model accuracy |

✨ Each page uses **DAX measures**, **cross-filtering**, and **tooltip insights** for interaction.

---

## 📈 EDA Insights

- **Shipping Methods**: Standard Class had the highest delay rate.
- **Customer Segment**: Home Office segment was under-utilized.
- **Monthly Demand Trends**: Seasonal fluctuations in orders.
- **Correlations**: Delay tied to long-distance + standard shipping.
- **Forecast Tooltip**: Forecasted 3 months demand using Decision Tree Classifier.

---

### 📊 Power BI Dashboard Overview  
#### 🧭 **1. Overview Page**
KPI cards show *Total Orders*, *On-Time %*, and *Average Delay*.  
Visuals update dynamically by region, date, and shipment status.

#### ⚙️ **2. Operations Page**
Tracks active shipments, late orders, and performance across transport modes.  
Includes **risk alerts** (highlighted via DAX measures).

#### 🏢 **3. Suppliers Page**
Ranks suppliers by *on-time delivery rate*, *delay days*, and *fulfillment volume*.  
Uses conditional formatting to flag underperformers.

#### 🛰️ **4. Live Tracking Page**
Simulates a **control-tower view** with real-time shipment status.  
Interactive “In-Transit”, “Processing”, and “Delivered” filters with hover effects.

#### 🔮 **5. Forecast Page**
Compares **actual vs predicted demand** using machine learning models.  
Shows performance metrics: **RMSE**, **MAE**, and **R²**.

---

### 🧮 Key DAX Highlights  
```DAX
Late Flag =
VAR diff = DATEDIFF(Shipments[ShipDate], Shipments[DeliveredDate], DAY)
RETURN IF(diff > 0, 1, 0)

On-Time % =
VAR ontime = CALCULATE([Total Shipments], FILTER(Shipments, [Late Flag] = 0))
RETURN DIVIDE(ontime, [Total Shipments])

Risk Alert =
VAR lateRate = CALCULATE(AVERAGE([Late Flag]), ALLEXCEPT(Shipments, Shipments[Route]))
RETURN IF(lateRate > 0.2, "⚠️ High", "✅ Normal")

---

🔮 Machine Learning Overview
| Model                         | Type           | Target         | Tools         | Metrics          |
| ----------------------------- | -------------- | -------------- | ------------- | ---------------- |
| **Shipment Delay Prediction** | Regression     | Delay Days     | Scikit-Learn  | RMSE, MAE, R²    |
| **Demand Forecasting**        | Classification | Monthly Orders | Decision Tree | Accuracy, Recall |


🔁 Migration Path to Azure

When upgraded, this project will integrate directly with Azure:

Blob Storage for centralized data ingestion

Data Factory to automate ETL pipelines

Synapse Analytics for warehouse and modeling

Power BI Service for live dashboard updates

🧩 Documentation/Migration-Plan.md details step-by-step Azure equivalents.

🧠 Machine Learning Models

Shipment Delay Prediction: Random Forest Regressor

Demand Forecasting: Decision Tree Classifier

Evaluation Metrics: RMSE, MAE, R²

All models trained and visualized in Google Colab.

📈 Project Goals

✔ Enhance supply chain visibility
✔ Predict late deliveries
✔ Support data-driven logistics decisions
✔ Build Azure-ready architecture on free tools

🧠 Key Learnings

📍 Data Cleaning & EDA (Pandas, Matplotlib, Seaborn)
📍 ML Model Building (Scikit-Learn)
📍 DAX & Power BI Calculations
📍 Cloud Simulation & Architecture Design
📍 GitHub Version Control & Project Documentation

💡 Future Enhancements

⏩ Automate ETL with Azure Data Factory

☁️ Host model APIs using Azure Functions

🔗 Connect Power BI to live Synapse endpoints

📦 Deploy using Azure DevOps pipelines


👩‍💻 Contributors
| Name             | Role                          | Key Focus                      |
| ---------------- | ----------------------------- | ------------------------------ |
| **Sneha Gurung** | Azure Solution Architect Lead | Architecture • ML • Power BI   |
| **Srishti Poudel** | Data Analyst                  | Cleaning • EDA • Visualization |


🚀 Quick Start (Free Version)
git clone https://github.com/snehagurung12/Supply-chain-visibility.git
cd Supply-chain-visibility
1️⃣ Open Colab → run pipeline/simulate_pipeline.ipynb
2️⃣ Run ML notebooks → generate ML/outputs/ CSV files
3️⃣ Open PowerBi/SupplyChain_Visibility.pbix → refresh data sources
4️⃣ Explore interactive dashboards and forecasts

🧾 License & Use

License: MIT – Free for academic and portfolio use.

Data: Synthetic/anonymized; no real supply-chain information.

🌟 Let’s Connect

Author: Sneha Gurung

GitHub: github.com/snehagurung12

LinkedIn: linkedin.com/in/SnehaGurung

💬 “From raw CSVs to predictive insights — this project transforms data into clarity.”


---
