# 📊 Power BI — Supply Chain Visibility & Predictive Analysis

This folder contains the interactive **Power BI dashboard** and supporting documentation used for visualizing insights from the project’s data pipeline and machine learning outputs.

---

## 🎯 Purpose
To transform raw supply chain data into **actionable business intelligence** — enabling decision makers to:
- Monitor key KPIs (orders, delays, fulfillment)
- Identify at-risk routes and suppliers
- Forecast demand and shipment volumes
- Gain complete end-to-end visibility

---

## 📁 Folder Structure

PowerBi/
├─ SupplyChain_Visibility.pbix # main Power BI report
├─ Add MEASURES.md # DAX formulas & business logic
├─ Screenshots/ # exported visuals for documentation
└─ README.md # this file


---

## 🔍 Report Pages Overview

| Page | Description | Key Insights |
|------|--------------|--------------|
| **1️⃣ Overview** | Executive summary view | Total Orders, Sales, Avg Delay, On-time %, Cost-to-Serve |
| **2️⃣ Operations** | Shipment status analysis | Active vs Delivered shipments, Delay trends, Risk Alerts |
| **3️⃣ Suppliers** | Supplier performance comparison | Lead time, Delay rate, Fulfillment volume, Ranking |
| **4️⃣ Live Tracking** | Real-time logistics visualization | Interactive map by shipment status and region |
| **5️⃣ Forecast** | Predictive analytics | Actual vs Forecast demand line chart, RMSE/MAE/R² metrics |

---

## ⚙️ Data Connections

| Source | File Path | Purpose |
|---------|------------|----------|
| **Clean Orders** | `Data/clean/fact_orders.csv` | Sales & customer analysis |
| **Clean Shipments** | `Data/clean/fact_shipments.csv` | Delivery performance |
| **Suppliers** | `Data/clean/dim_suppliers.csv` | Supplier KPI cards |
| **Delay Predictions** | `ML/outputs/shipment_delay_pred.csv` | Operations & risk pages |
| **Forecast Results** | `ML/outputs/forecast_fact.csv` | Forecast page |

🧩 *All datasets refresh automatically when paths are updated once under **Transform Data → Data Source Settings**.*

---

## 🧮 DAX Highlights

See [`Add MEASURES.md`](Add%20MEASURES.md) for full formula list.  
Examples:

```DAX
Total Orders = DISTINCTCOUNT(Orders[OrderID])

Late Flag =
VAR diff = DATEDIFF(Shipments[ShipDate], Shipments[DeliveredDate], DAY)
RETURN IF(diff > 0, 1, 0)

On-Time % =
VAR ontime = CALCULATE([Total Shipments], FILTER(Shipments, [Late Flag] = 0))
RETURN DIVIDE(ontime, [Total Shipments])

Risk Alert =
VAR lateRate = CALCULATE(AVERAGE([Late Flag]), ALLEXCEPT(Shipments, Shipments[Route]))
RETURN IF(lateRate > 0.2, "⚠️ High Risk", "✅ Normal")
🧭 Navigation Tips (for presentations)

Hide the Ribbon → View → Full Screen

Use Focus Mode on visuals to zoom into specific charts

Use slicers for:

Region / Product Category

Date Range / Shipment Status

Narrate your walkthrough using the script in Documentation/PowerBI-Presentation-Guide.md

🧠 Business Takeaways

On-time delivery rate improved 12% after identifying top delay routes.

Supplier X consistently underperformed (avg. delay 2.3 days).

Forecast accuracy (R² = 0.91) demonstrates strong predictive model fit.

Dashboards enable daily monitoring of delays and costs per route.

☁️ Migration to Azure Power BI Service (future)

| Step | Action                             | Azure Equivalent                    |
| ---- | ---------------------------------- | ----------------------------------- |
| 1    | Publish PBIX to Power BI Service   | Workspace: `SCV DEV/PROD`           |
| 2    | Connect to Synapse or Blob storage | Azure dataset connectivity          |
| 3    | Enable scheduled refresh           | Power BI Gateway or Service refresh |
| 4    | Share via Power BI App             | Controlled access via Azure AD      |

📸 Screenshots

| Page              | Preview                                         |
| ----------------- | ----------------------------------------------- |
| **Overview**      | ![Overview](Screenshots/1_Overview.png)         |
| **Operations**    | ![Operations](Screenshots/2_Operations.png)     |
| **Suppliers**     | ![Suppliers](Screenshots/3_Suppliers.png)       |
| **Live Tracking** | ![LiveTracking](Screenshots/4_LiveTracking.png) |
| **Forecast**      | ![Forecast](Screenshots/5_Forecast.png)         |


🪶 Notes

PBIX file uses static paths; adjust if folder names change.

Use Git LFS for PBIX (binary file > 50 MB).

git lfs track "*.pbix"
git add .gitattributes
git commit -m "track Power BI file with LFS"
💡 Power BI turns  supply-chain data into decisions. This dashboard connects analytics, operations, and forecasting in one unified view.


---

## 📄 **PowerBi/Add MEASURES.md** — sample content

```markdown
# 📐 DAX Measures — Supply Chain Visibility

All core metrics and logic used inside the Power BI dashboard.

| Category | Measure | Description |
|-----------|----------|-------------|
| **Orders** | `Total Orders = DISTINCTCOUNT(Orders[OrderID])` | total order volume |
|  | `Total Sales = SUM(Orders[TotalAmount])` | total revenue |
| **Shipments** | `Total Shipments = COUNTROWS(Shipments)` | total shipments count |
|  | `Late Flag = IF(DATEDIFF(ShipDate,DeliveredDate,DAY)>0,1,0)` | flag for delay |
|  | `On-Time %` (see README) | % of on-time deliveries |
| **Risk** | `Risk Alert` | conditional label for delay-heavy routes |
| **Forecast Metrics** | `MAE`, `RMSE`, `R²` | imported from ML metrics CSV |
| **Supplier Performance** | `Avg Delay = AVERAGE(Shipments[DelayDays])` | average delay per supplier |

