
# 📦 Project Title: Supply Chain Visibility and Predictive Analysis

> 🚀 A cloud-based solution to track, visualize, and predict supply chain movement using Azure and free tools like Google Colab and Power BI.

---

## 📚 Table of Contents

- [Overview](#overview)
- [Project Goals](#project-goals)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Getting Started](#getting-started)
- [Setup Guide](#setup-guide)
- [Usage Guide](#usage-guide)
- [Team Roles](#team-roles)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Changelog](#changelog)
- [License](#license)

---

## 🧭 Overview

This documentation covers the analysis, architecture, and decision rationale behind building a cloud-based system to track and predict supply chain performance. It demonstrates:

- Improved transparency and traceability of supply chain data
- Early prediction of delivery risks or disruptions
- Data-driven decision making via live dashboards
---

## 🎯 Project Goals

- Improve transparency and traceability of supply chain data.
- Predict delays or disruptions before they occur.
- Visualize performance metrics through live dashboards.
- Use fully or mostly free platforms to maximize accessibility.

---

## 🏗 Architecture

![Architecture Diagram](./architecture-diagram/supply_chain_architecture.png)

*Short Description:*  
This architecture includes:
- *Google Colab* for data processing
- *GitHub* for collaboration and version control
- *Azure Blob Storage* for dataset storage
- *Power BI* for interactive dashboards

---

## 🧰 Tech Stack

| Component        | Technology Used             |
|------------------|-----------------------------|
| Cloud Storage    | Azure Blob Storage          |
| Processing       | Python (Google Colab)       |
| Visualization    | Power BI                    |
| Data Handling    | Pandas, NumPy               |
| Collaboration    | Git + GitHub                |
| Documentation    | Markdown, draw.io diagrams  |

---

## ✨ Features

- Upload and manage supply chain datasets in Blob storage
- Run predictive analysis scripts (e.g., demand forecasting, delay prediction)
- Live dashboard for stakeholders using Power BI
- Modular codebase and collaboration through GitHub

---
## 📊 Key Insights from EDA
### Delivery Status
- *Analysis:* A significant portion of orders are late, indicating operational bottlenecks.
- *Recommendation:* Investigate shipping modes, product types, and regional issues. Implement monitoring to proactively identify high-risk orders.

### Order Type
- *Analysis:* Majority are digital transactions (Payments & Expenses), with minimal Cash usage.
- *Recommendation:* Support digital-first operations and explore additional digital payment options.

### Shipping Method
- *Analysis:* Standard Class dominates, suggesting cost-focused shipping; 1st/2nd class used mainly for urgency.
- *Recommendation:* Review shipping policies to balance speed vs cost.

### Customer Segments
- *Analysis:* Split mainly between Consumers & Corporate, with a smaller Home Office segment.
- *Recommendation:* Continue focus on major segments, explore campaigns for Home Office customers.

### Correlations
- *Analysis:* Delivery time, risk, and discounts show correlated patterns.
- *Recommendation:* Use regression or ML models to predict delays & optimize pricing.

### Seasonality
- *Analysis:* Sales volume fluctuates monthly, indicating seasonal patterns.
- *Recommendation:* Align inventory and staffing plans to demand cycles.

---


## 📂 Folder Overview
/data          → Raw and cleaned CSV datasets
/pipeline      → Simulated pipeline (notebook, cleaned CSV, HTML output)
/notebooks     → EDA and transformation notebooks
/architecture  → Architecture diagrams (Azure-focused)
/powerbi       → Power BI dashboards and KPIs
/documentation → This README, EDA PDF, findings

## 📚 Related Docs
- /documentation/EDA_Report.pdf — full exploratory data analysis
- /architecture/AzureArchitecture_SupplyChain.png — data pipeline diagram

