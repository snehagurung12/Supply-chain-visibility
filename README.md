
# Supply Chain Visibility & Predictive Analysis

## 🔍 Objective
This project aims to simulate a supply chain analytics system using Azure architecture (Blob Storage, Data Factory, Synapse) and build actionable dashboards using Power BI.

## 👤 Roles
- *Azure Solution Architect (Sneha Gurung)*: Designed the cloud pipeline, simulated Synapse analytics in Python
- *Data Analyst (Srishti Poudel)*: Created Power BI dashboards and extracted insights

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

## 🧰 Tech Stack

| Component        | Technology Used             |
|------------------|-----------------------------|
| Cloud Storage    | Azure Blob Storage          |
| Processing       | Python in Google Colab      |
| Visualization    | Power BI                    |
| Data Handling    | Pandas, NumPy               |
| Collaboration    | Git + GitHub                |
| Documentation    | Markdown + Architecture Diagrams |

---

## ✨ Features

- 📥 Upload and store raw datasets in Azure
- 🧪 Clean, transform, and model data using Python
- 📈 Visualize predictions and KPIs in Power BI
- 🧩 Modular codebase for easy collaboration

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

## 🚀 Get Started
```bash
git clone https://github.com/<yourusername>/Supply-chain-project.git
cd Supply-chain-project

•	Run /pipeline/simulate_pipeline.ipynb to process data.
	•	Open /powerbi to explore dashboard .pbix files.
	•	Review /documentation/EDA_Report.pdf for detailed insights.


