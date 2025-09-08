
# Supply Chain Visibility & Predictive Analysis

## 🔍 Objective
This project aims to simulate a supply chain analytics system using Azure architecture (Blob Storage, Data Factory, Synapse) and build actionable dashboards using Power BI.

## 👥 Team & Role Distribution

| Role                     | Responsibilities |
|--------------------------|------------------|
| **Azure Solution Architect** | Designed the system architecture, simulated data pipeline, built machine learning models in Google Colab, managed forecast output integration, and led dashboard structural design. |
| **Data Analyst**             | Performed data profiling, cleaning, and preprocessing; conducted exploratory data analysis; developed slicer logic and insights in Power BI; refined dashboard layout and tooltip interactions. |

> The team collaborated closely to simulate Azure services using open-source tools and divide responsibilities in line with real-world cloud project workflows.

## 🛠 Tools Used
- Google Colab (for data cleaning)
- Azure Synapse (simulated)
- Power BI
- GitHub

## 📁 Structure
- /data – datasets
- /notebooks – Colab notebooks
- /architecture – Azure diagram and design
- /powerbi – dashboards
- /pipeline        → Simulated ETL notebook, cleaned CSV, HTML summary
- /documentation – findings and summaries

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

## 🧰 Tools & Stack

| Component         | Technology Used             |
|------------------|-----------------------------|
| Cloud Storage     | GitHub (simulated Blob Storage)     |
| ETL & ML          | Google Colab, Python        |
| ML Libraries      | Scikit-learn, Pandas, NumPy |
| Visualization     | Power BI Desktop            |
| Version Control   | Git + GitHub                |
| Documentation     | Markdown + Diagrams         |

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

## 📌 ML Pipeline Code (Colab Example)

```python
# Encode shipping mode
df['Shipping_Mode'] = df['Shipping_Mode'].astype('category').cat.codes

# Train Decision Tree for demand forecasting
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier()
model.fit(X_train, y_train)

# Export forecast
forecast_df.to_csv('forecast_output.csv')

•	Run /pipeline/simulate_pipeline.ipynb to process data.
	•	Open /powerbi to explore dashboard .pbix files.
	•	Review /documentation/EDA_Report.pdf for detailed insights.


