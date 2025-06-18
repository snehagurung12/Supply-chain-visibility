# Azure Architecture Explanation – Supply Chain Visibility & Predictive Analysis

## 📊 Overview
This architecture diagram represents the end-to-end flow of supply chain data through Azure services. The solution is designed to simulate a modern, cloud-based analytics system using scalable, modular components.

![Architecture Diagram](AzureArchitecture_SupplyChain.png)

---

## 🔁 Data Flow Breakdown

1. *Data Source*  
   Raw CSV files (e.g., from GitHub) serve as the source of product, warehouse, and delay data.

2. *Azure Blob Storage*  
   Stores the raw data files securely in the cloud.

3. *Azure Data Factory*  
   Orchestrates the ETL process — extracting data from Blob, cleaning it, and moving it to Synapse.

4. *Azure Synapse Analytics*  
   Acts as a centralized data warehouse where structured data is stored and queried using SQL.

5. *Power BI*  
   Connects to Synapse to visualize data in the form of charts, KPIs, and dashboards.

6. *Dashboard Output*  
   Displays insights such as shipment delays, inventory levels, and cost trends to help decision-makers optimize supply chain operations.

---

## 🧠 Why This Architecture?

- *Modular*: Each service handles one dedicated function (storage, ETL, warehousing, visualization)
- *Scalable*: Can handle growing data volume without re-architecture
- *Realistic*: Simulates real Azure enterprise design even without paid resources

---

## 🔐 Optional Enhancements

If extended with budget or credits:
- Add Azure Key Vault for secure access management
- Use Azure Monitor for performance alerts
- Automate ETL triggers using Logic Apps
