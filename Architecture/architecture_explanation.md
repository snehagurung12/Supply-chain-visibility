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

---

## 🏗 Key Components and Their Roles

| Component                     | Description |
|--------------------------------|-------------|
| *User Uploads CSV*           | The starting point of the data pipeline. Users provide the raw supply chain data file. |
| *GitHub Repository*          | Simulates Azure Blob Storage by storing raw and processed CSV files. Acts as centralized data storage. |
| *Google Colab + Pandas*      | Simulates Azure Data Factory (ADF). Ingests data, performs cleaning, filtering, and prepares it for downstream usage. |
| *Pandas DataFrame*           | Simulates Azure SQL Database. Holds cleaned, structured data temporarily for processing. |
| *Power BI Dashboard*         | Built by teammate. Visualizes the cleaned dataset to deliver actionable insights. |

---

## 🔁 Data Flow

1. *CSV Upload:*
   - The raw supply chain CSV is manually uploaded into Google Colab or stored in GitHub.
2. *Data Processing:*
   - Pandas handles ETL tasks: removing nulls, filtering delivered shipments, transforming dates, sorting.
3. *Data Storage:*
   - Processed data is saved locally as CSV and HTML, mimicking writing back to Blob Storage or a database.
4. *Visualization:*
   - The cleaned dataset is fed into Power BI by the data analyst teammate to create dashboards and predictive charts.

---

## 📈 Deployment Diagram

![Deployment Architecture](deployment_architecture.png)

---

## 🚀 Why This Architecture?

- Mimics best practices from Azure’s recommended data processing pipelines.
- Demonstrates separation of concerns:
  - Storage (GitHub)
  - Processing (Colab + Pandas)
  - Visualization (Power BI)
- Enables future upgrades:
  - Replace Colab with actual Azure Data Factory.
  - Use Azure SQL Database for scalable data storage.
  - Automate with Azure Logic Apps or Functions.

---

## ✅ Conclusion

This architecture shows how cloud principles can be simulated effectively using free tools, preserving the logical flow and making it easy to migrate to Azure when resources allow. It also demonstrates practical, teamwork-based division of responsibilities in a real cloud solution.
