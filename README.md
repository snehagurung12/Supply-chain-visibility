<!-- Banner or cover image -->
<p align="center">
  <img src="Architecture/SCV_Architecture.png" width="90%" alt="Supply Chain Architecture Overview"/>
</p>

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

| Layer | Free Tools (Simulation) | Azure Equivalent |
|-------|--------------------------|------------------|
| **Data Storage** | GitHub CSVs | Blob Storage |
| **ETL & Processing** | Google Colab (Pandas, NumPy) | Data Factory + Synapse |
| **ML Models** | Scikit-Learn | Azure ML / Synapse ML |
| **Visualization** | Power BI Desktop | Power BI Service |

<p align="center">
  <img src="Architecture/Azure_Like_Pipeline.png" width="80%" alt="Azure Inspired Architecture Diagram"/>
</p>

---

🗂️ **Folder Structure**
📦 Supply-chain-visibility
┣ 📁 Architecture # Azure-like architecture diagrams
┣ 📁 Data # Raw & cleaned datasets
┣ 📁 Documentation # Project documentation and presentation guide
┣ 📁 ML # Forecasting and delay prediction outputs
┣ 📁 Notebook # Google Colab notebooks for EDA & ML
┣ 📁 pipeline # Simulated ETL pipeline steps
┣ 📁 PowerBi # Power BI report (.pbix) and screenshots
┗ 📄 README.md

---

## 🧩 Architecture Diagram

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

## 🧠 Key Features

- ✅ Simulated Azure architecture using free tools
- 🧪 Data pipeline with Colab-based ETL & machine learning
- 📈 Interactive Power BI dashboard with slicers, icons, and forecast tooltips
- 🔮 Predictive models: demand classification & delay forecasting
- 📦 Shipment tracking by status, region, and supplier performance
- 🔔 Risk alerts and forecast overlays inspired by enterprise BI dashboards
---

## 🎯 Project Goals
- Enhance transparency across the supply chain
- Predict delivery risks and delays before they happen
- Visualize performance metrics through interactive dashboards
- Use mostly free / accessible tools (Google Colab, Power BI, Azure Free Tier)

---

## 🏗 Architecture Overview
![Architecture Deployment Diagram](Architecture/deployment_architecture.png)

*Pipeline:*
- *Azure Blob Storage:* Stores raw and cleaned datasets.
- *Python ETL:* Simulated in Google Colab notebooks (cleaning, feature engineering).
- *Azure Synapse (simulated):* For advanced analytics and warehousing.
- *Power BI:* Builds live dashboards with predictive insights.

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

## 🧩 Azure-Inspired Architecture

![Architecture Diagram](architecture/AzureArchitecture_SupplyChain.png)

> Simulated components include:
> - **GitHub** as Azure Blob Storage (for versioned CSVs)
> - **Google Colab** as Azure Data Factory + ML Studio
> - **Power BI** to replicate the Power BI Service
> - **Scikit-learn models** for forecasting & delay prediction

---

## 🏗 Deployment Pipeline Overview

![Deployment Diagram](architecture/deployment_architecture.png)

- **Data Ingestion**: CSVs uploaded to GitHub
- **Preprocessing & ML**: Performed in Colab (null handling, feature engineering, model training)
- **Model Output**: Exported `.csv` of forecasts merged with actuals
- **Visualization**: Dashboard in Power BI with slicers, KPI cards, forecast tooltips

---

## 🔮 Machine Learning Models

### 📦 1. Shipment Delay Prediction  
- **Type**: Regression  
- **Algorithm**: Random Forest Regressor  
- **Inputs**: Shipping mode, quantity, product category, distance  
- **Target**: Delay duration (in days)  

### 📈 2. Demand Forecasting  
- **Type**: Classification  
- **Algorithm**: Decision Tree Classifier  
- **Inputs**: Product ID, month, past volume  
- **Target**: Demand Level (High / Medium / Low)  
- **Integration**: Tooltip-enabled line chart in Power BI (Actual vs Forecast Demand)

> *ML models are planned for full automation in future iterations.*

---

## 📊 Dashboard Highlights

| Page         | Key Visuals                                                                 |
|--------------|------------------------------------------------------------------------------|
| Overview     | Total Orders, Shipment KPIs, Delay %, Top Products, Forecast Tooltip Chart  |
| Operations   | In-Transit Status Cards, Risk Alerts, Monthly Delays                        |
| Analytics    | Order Trends, Category Breakdown, Segment-wise Sales                        |
| Suppliers    | Supplier Scorecard, Delay by Region, Pie of Supplier Ratings                 |
| Live Tracking| Status Filter, Hover Effects, Shipment Distribution                         |
| Forecast     | Forecast vs Actual Chart, Post-Cutoff Tooltip, Category Predictions          |

> Enhanced with hover tooltips, smooth slicers, pastel UI theme, and icon-based tabs.

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

---

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

💡 Future Enhancements

Automate ETL pipeline using Azure Data Factory

Deploy model inference API with Azure Functions

Enable Power BI live connection to Azure Synapse

👩‍💻 Contributors
Name	Role
Sneha Gurung	Azure Solution Architect Lead
Srishti Poudel  	Data Analyst
🪄 How to Run (Free Simulation)

Clone this repo

Open Notebook/01_EDA.ipynb and 02_ML.ipynb in Google Colab

Run all cells → cleaned data saved in /Data/clean/

Open PowerBi/SCV_Report.pbix → update file path to local /Data/clean/

Explore visuals using slicers and filters

🧾 License

MIT License — Free to use for learning and academic purposes.

🌟 Let’s Connect

Author: Sneha Gurung

GitHub: github.com/snehagurung12

LinkedIn: linkedin.com/in/SnehaGurung

💬 This project is part of a portfolio demonstrating Azure Solution Architect and Data Analytics capabilities using cost-free, scalable alternatives.


---

## 🔧 Recommended Enhancements
In your GitHub:
1. Replace current `README.md` with the above version.  
2. Add a **hero image or architecture diagram** at the top:
   ```markdown
   ![Project Architecture](Architecture/SCV_Architecture.png)



![Python](https://img.shields.io/badge/Python-3.10-blue)
![Power BI](https://img.shields.io/badge/Power%20BI-Visualization-yellow)
![Azure](https://img.shields.io/badge/Azure-Ready-blue)
![License](https://img.shields.io/badge/License-MIT-green)

