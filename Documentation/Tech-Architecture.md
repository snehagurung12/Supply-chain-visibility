# 🏗️ Technical Architecture

The project follows a modular, Azure-inspired design with five key layers:

| Layer | Description | Tools |
|-------|--------------|-------|
| Data Ingestion | CSVs sourced & versioned via GitHub | GitHub / Blob |
| Data Processing | Cleaning, transformation, and feature engineering | Google Colab (Pandas) |
| ML Analytics | Shipment delay prediction & demand forecasting | Scikit-Learn |
| Visualization | KPI dashboards, forecasting insights | Power BI |
| Orchestration | Manual simulation of pipelines | Jupyter/Colab + future ADF |

<p align="center">
  <img src="../Architecture/SCV_Architecture.png" width="90%" alt="Architecture Diagram">
</p>

### Azure-equivalent Flow
Blob → Data Factory → Synapse → Power BI → Azure ML  
(Currently simulated with free equivalents)
