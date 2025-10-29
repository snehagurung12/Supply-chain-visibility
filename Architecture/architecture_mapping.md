# Architecture Mapping — Free Tools → Azure

**Purpose:** Map the current free-tool stack to Azure, with exact names, folders, pipelines, connectivity, security, and cost guardrails.  
**Project mode:** Free simulation now (GitHub + Colab + Power BI) → Azure-ready later.

---

## 1) Capability mapping

| Capability         | Free tools now                            | Azure later (planned)                  |
|-------------------|--------------------------------------------|----------------------------------------|
| Object storage     | GitHub repo `/Data` (CSVs)                | **Azure Blob Storage** (ADLS Gen2)     |
| Orchestration      | Manual steps in **Google Colab**          | **Azure Data Factory**                 |
| Transform / SQL    | **Pandas** in Colab                       | **Synapse Serverless / Dedicated SQL** |
| ML training/infer  | **scikit-learn** in Colab                 | **Azure ML** or **Synapse Spark/ML**   |
| BI / reporting     | **Power BI Desktop**                      | **Power BI Service / Fabric**          |

---

## 2) Resource naming & region

Use short, lowercase names (no underscores). Replace `<env>` with `dev/test/prod`.

- **Resource Group:** `rg-scv-<env>`
- **Storage (ADLS Gen2):** `stscv<env>`
- **Data Factory:** `adf-scv-<env>`
- **Synapse workspace:** `syn-scv-<env>`
- **Key Vault:** `kv-scv-<env>`
- **Power BI workspace:** `SCV <ENV>` (e.g., `SCV DEV`)
- **Region:** `australiaeast` (keep consistent across services)

---

## 3) Data zones & folder layout (Blob)

Store **raw CSV**, write **clean Parquet** (cheaper/faster queries), and export ML outputs.
/raw/orders/YYYY=2025/MM=10/.csv
/raw/shipments/YYYY=2025/MM=10/.csv
/raw/suppliers/*.csv

/clean/fact_orders/YYYY=2025/MM=10/.parquet
/clean/fact_shipments/YYYY=2025/MM=10/.parquet
/clean/dim_suppliers/.parquet
/clean/dim_calendar/.parquet

/ml-outputs/forecast_fact/.csv
/ml-outputs/shipment_delay_pred/.csv


