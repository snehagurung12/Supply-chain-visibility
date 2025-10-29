# 🎥 Power BI Presentation Guide

*This guide helps presenters or reviewers understand the story behind each Power BI page.*

---

## 🧭 Overview Page
**Purpose:** Provides a top-level snapshot of the entire supply chain.
- **KPIs:** Total Orders, On-Time %, Delay Days, Total Cost
- **Visuals:** Sales trend line, region map, category distribution
- **Interaction:** Change region → all visuals refresh instantly.


“Here we can see our KPIs updating in real time. The slicer on the left helps filter by region or product type.”

---

## ⚙️ Operations Page
**Purpose:** To monitor ongoing shipments and performance.
- **Key Visuals:** Status segmentation, route delays, active vs completed shipments.
- **KPI Cards:** Processing | In-Transit | Delivered | Late %


“This helps the operations team pinpoint late routes and monitor daily delivery performance.”

---

## 🏢 Suppliers Page
**Purpose:** Analyze supplier efficiency and reliability.
- **Metrics:** Avg. delay, on-time rate, total orders
- **Visuals:** Supplier ranking bar chart, conditional color alerts


“Red bars highlight suppliers exceeding our delay threshold.”

---

## 🛰️ Live Tracking Page
**Purpose:** Simulates a control tower view.
- **Visuals:** Map with shipment pins
- **Status Filters:** Delivered | Processing | In Transit

“Selecting a status updates both the map and the performance summary dynamically.”

---

## 🔮 Forecast Page
**Purpose:** Compare predicted vs. actual shipment volumes.
- **Visuals:** Actual vs Forecast line chart
- **Model Metrics:** RMSE, MAE, R² (from Colab ML model)
  
“This page shows our ML model’s predictive accuracy and seasonal trends.”

---



