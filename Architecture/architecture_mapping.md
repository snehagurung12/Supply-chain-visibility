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

**Notes**
- Partition by `YYYY/MM` for incremental refresh.
- Prefer Parquet in **clean/** to reduce Synapse scanned bytes.

---

## 4) Pipeline mapping (step-by-step)

| Step | Today (free simulation)                            | Azure (later)                                  | Output |
|-----:|----------------------------------------------------|-------------------------------------------------|--------|
| 0    | Commit CSVs under GitHub `Data/raw`                | **ADF Copy** from GitHub/HTTP → Blob **raw/**   | Raw CSV |
| 1    | Colab: clean, type-correct, normalize              | **ADF Mapping Data Flow** (or Synapse Spark)    | **clean/** Parquet |
| 2    | Colab: feature engineering (LateFlag, DelayDays)   | **Data Flow** / **Notebook** activity           | Enriched **clean/** |
| 3    | Colab: train RF/DT models                          | **Azure ML** (training pipeline)                | Model + metrics |
| 4    | Colab: export predictions                          | **Notebook/Copy** to **ml-outputs/**            | Forecast CSV |
| 5    | Power BI reads cleaned & ML outputs                | **Power BI Service/Fabric** dataset refresh     | Reports |

**Feature examples**  
- `LateFlag = 1` if `DeliveredDate > ExpectedDate`  
- `DelayDays = DATEDIFF(ShipDate, DeliveredDate)`  
- `OnTimeRate` by route/supplier for risk visuals

---

## 5) Synapse Serverless — quick templates

Use **external data source** + `OPENROWSET` or define external tables over **Parquet**.

```sql
-- Data source to ADLS Gen2 (clean zone)
CREATE EXTERNAL DATA SOURCE eds_scv
WITH ( LOCATION = 'https://stscvdev.dfs.core.windows.net/' );

-- File formats
CREATE EXTERNAL FILE FORMAT eff_parquet WITH ( FORMAT_TYPE = PARQUET );
CREATE EXTERNAL FILE FORMAT eff_csv WITH ( FORMAT_TYPE = DELIMITEDTEXT, FORMAT_OPTIONS ( FIELD_TERMINATOR = ',', STRING_DELIMITER = '\"', FIRST_ROW = 2 ) );

-- Query Parquet on the fly (fast & cheap)
SELECT *
FROM OPENROWSET(
  BULK 'clean/fact_shipments/**/*.parquet',
  DATA_SOURCE = 'eds_scv',
  FORMAT = 'PARQUET'
) AS rows;

-- Optional: external table over clean/
CREATE EXTERNAL TABLE dbo.fact_shipments
WITH (
  LOCATION = 'clean/fact_shipments/',
  DATA_SOURCE = eds_scv,
  FILE_FORMAT = eff_parquet
)
AS
SELECT *
FROM OPENROWSET(
  BULK 'clean/fact_shipments/**/*.parquet',
  DATA_SOURCE = 'eds_scv',
  FORMAT = 'PARQUET'
) AS src;
6) Power BI connectivity
Parameters in the PBIX:
BlobAccountUrl, ContainerName, CleanFolder, MLOutputsFolder

Dev→Prod: swap parameters or use Deployment Pipelines.

Incremental refresh: enable on large facts (Orders/Shipments) keyed by Date.

Gateway: not required if sourcing from Synapse Serverless or public Blob with SAS.

7) Security, identity, and access
Principle: least privilege.

Key Vault: store SAS tokens / secrets used by ADF and Synapse.

RBAC (examples):

Data Engineer: Contributor on RG, Storage Blob Data Owner on Storage

Analyst (PBI): Storage Blob Data Reader, PBI Workspace Member

Viewer: PBI App Viewer only

Managed identities: enable for ADF/Synapse to access Storage/Key Vault.

Networking (future): Private Endpoints for Storage & Synapse; restrict public access.

8) Observability & cost guardrails
ADF: send pipeline logs/metrics to Log Analytics.

Synapse Serverless: query Parquet; push filters; monitor scanned bytes.

Lifecycle policies:

raw/ → archive after 30–90 days

clean/ retain 180+ days

ml-outputs/ retain 90 days

Budgets: set cost alerts at RG (e.g., notify at $20 and $35).

9) Environments & branching

| Env  | Resource Group | Data scope        | Power BI workspace |
| ---- | -------------- | ----------------- | ------------------ |
| DEV  | `rg-scv-dev`   | samples/subsets   | `SCV DEV`          |
| TEST | `rg-scv-test`  | anonymized subset | `SCV TEST`         |
| PROD | `rg-scv-prod`  | full production   | `SCV PROD`         |

it strategy: dev branch → PR → main.
Data contracts: update Data-Dictionary.md when schemas change.

10) ER model (for visuals & DAX)

Core tables

Orders(OrderID, OrderDate, CustomerSegment, Product, Quantity, TotalAmount, SupplierID)

Shipments(ShipmentID, OrderID, ShipDate, DeliveredDate, Route, Carrier, Mode, DistanceKM)

Suppliers(SupplierID, SupplierName, Rating, LeadTimeDays)

Calendar(Date, Year, MonthNum, YearMonth, YearMonthSort)

Relationships

Orders 1—* Shipments (OrderID)

Suppliers 1—* Orders (SupplierID)

Calendar 1—* Orders/Shipments (Date keys)

11) Diagram guidance (how to draw each PNG)

01_system-overview:
Left→Right: GitHub (Data/raw) → Colab (Clean/Feature/ML) → Outputs (clean/, ml-outputs/) → Power BI.
Add a dashed track below showing Azure equivalent boxes.

02_dataflow-layers:
Three zones raw / clean / ml-outputs with example partitioned paths and refresh cadence (daily/weekly).

03_deployment-topology:
One resource group box containing Storage, ADF, Synapse, Key Vault; outside Power BI Service.
Arrows: ADF ↔ Storage, Synapse ↔ Storage, PBI ↔ Synapse/Storage.

12) Quick checklist

 Diagrams exported as .png and editable .drawio

 Names match this document

 Folders/partitions reflect raw/clean/ml-outputs

 PBIX parameters created for storage paths

 Data-Dictionary updated after any schema change

---



