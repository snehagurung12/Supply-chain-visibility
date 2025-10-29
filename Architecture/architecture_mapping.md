# Architecture — Supply Chain Visibility & Predictive Analysis

This folder contains the **visual blueprints** for the project and the mapping needed to lift the current **free-tools simulation** (GitHub + Colab + Power BI) into an **Azure-native** solution.

## Files in this folder

- `01_system-overview.png` (and `.drawio`)  
  High-level end-to-end flow: **Ingest → Process/ML → Outputs → BI**.

- `02_dataflow-layers.png` (and `.drawio`)  
  Storage zones and cadence: **raw/**, **clean/**, **ml-outputs/**, with example folder paths.

- `03_deployment-topology.png` (and `.drawio`)  
  Azure resources in one view: **Resource Group, Storage (ADLS Gen2), ADF, Synapse, Key Vault, Power BI Service/Fabric**.

- *(Optional)* `04_security-boundaries.png`  
  RBAC roles, identities, and private endpoints (future).

- *(Optional)* `05_er-model.png`  
  Entity relationships: **Orders, Shipments, Suppliers, Calendar**.

- `Architecture-Mapping.md`  
  The **single source of truth** for naming, folders, pipelines, SQL templates, Power BI connectivity, security, cost, and environments.

> Keep both the **PNG/SVG** and the **editable `.drawio`** for every diagram so others can update them.
