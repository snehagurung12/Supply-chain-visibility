# 📊 Power BI DAX Measures  
**Project:** Supply Chain Visibility & Predictive Analysis  
**Author:** Team Supply Chain (Azure Solution Architect Lead & Data Analyst)  
**Purpose:** This document lists all DAX measures used to build KPIs, dashboards, and predictive analytics visuals in Power BI.

---

```DAX

 🧩 1) Core Aggregates

Total Orders =
COUNTROWS ( Orders )

Total Quantity =
SUM ( Orders[Quantity] )

Total Sales =
SUM ( Orders[Sales] )   -- or Orders[Amount]

Total Cost =
SUM ( Orders[Cost] )

Total Profit =
SUM ( Orders[Profit] )

Gross Margin % =
DIVIDE ( [Total Profit], [Total Sales] )

Total Shipments =
COUNTROWS ( Shipments )

⏱️ 2) Shipment Timeliness & Delay

Delay Days =
VAR _ship = Shipments[ShipDate]
VAR _del  = Shipments[DeliveredDate]
RETURN
    IF (
        NOT ISBLANK ( _ship ) && NOT ISBLANK ( _del ),
        DATEDIFF ( _ship, _del, DAY ),
        BLANK ()
    )

Late Flag =
IF ( [Delay Days] > 0, 1, 0 )

On-Time Shipments =
CALCULATE ( [Total Shipments], FILTER ( Shipments, [Late Flag] = 0 ) )

Late Shipments =
CALCULATE ( [Total Shipments], FILTER ( Shipments, [Late Flag] = 1 ) )

On-Time % =
DIVIDE ( [On-Time Shipments], [Total Shipments] )

Late % =
DIVIDE ( [Late Shipments], [Total Shipments] )

Average Delay (Days) =
AVERAGE ( Shipments[Delay Days] )

Median Delay (Days) =
MEDIAN ( Shipments[Delay Days] )

P95 Delay (Days) =
PERCENTILEX.INC ( Shipments, Shipments[Delay Days], 0.95 )


🚚 3) Shipment Status (Control Tower)

Processing Shipments =
CALCULATE ( [Total Shipments], Shipments[Status] = "Processing" )

In Transit Shipments =
CALCULATE ( [Total Shipments], Shipments[Status] = "In Transit" )

Delivered Shipments =
CALCULATE ( [Total Shipments], Shipments[Status] = "Delivered" )

Active Shipments =
[Processing Shipments] + [In Transit Shipments]


💰 4) Cost & Efficiency

Total Shipping Cost =
SUM ( Shipments[ShippingCost] )

Avg Shipping Cost / Shipment =
DIVIDE ( [Total Shipping Cost], [Total Shipments] )

Shipping Cost % of Sales =
DIVIDE ( [Total Shipping Cost], [Total Sales] )


🏭 5) Supplier Scorecard & Ranking

Supplier Late Shipments =
CALCULATE ( [Late Shipments], ALLEXCEPT ( Shipments, Shipments[Supplier] ) )

Supplier On-Time % =
CALCULATE ( [On-Time %], ALLEXCEPT ( Shipments, Shipments[Supplier] ) )

Supplier Fulfilled Qty =
SUMX ( FILTER ( Suppliers, NOT ISBLANK ( Suppliers[Supplier] ) ), Suppliers[FulfilledQty] )

Supplier Score =
-- Simple composite score (tune weights as needed)
VAR wOnTime   = 0.7
VAR wVolume   = 0.3
VAR _score =
    ( wOnTime * [Supplier On-Time %] )
    + ( wVolume * DIVIDE ( [Supplier Fulfilled Qty], CALCULATE ( [Supplier Fulfilled Qty], ALL ( Suppliers ) ) ) )
RETURN _score

Supplier Rank (By Score) =
RANKX ( ALL ( Shipments[Supplier] ), [Supplier Score], , DESC, DENSE )


⚠️ 6) Risk / Alerts

Late Rate (Context) =
AVERAGEX ( VALUES ( Shipments[OrderID] ), [Late Flag] )

Risk Alert (High/Normal) =
VAR threshold = 0.20   -- 20% late rate; adjust as needed
RETURN
    IF ( [Late Rate (Context)] > threshold, "⚠️ High", "✅ Normal" )

Late Route Risk =
CALCULATE ( [Late Rate (Context)], ALLEXCEPT ( Shipments, Shipments[Route] ) )


🤖 7) Forecast / ML Metrics (Actual vs Predicted)

Total Actual =
SUM ( Forecast[Actual] )

Total Predicted =
SUM ( Forecast[Predicted] )

Error (Absolute) =
SUMX ( Forecast, ABS ( Forecast[Actual] - Forecast[Predicted] ) )

Error^2 =
SUMX ( Forecast, POWER ( Forecast[Actual] - Forecast[Predicted], 2 ) )

MAE =
DIVIDE ( [Error (Absolute)], COUNTROWS ( Forecast ) )

RMSE =
SQRT ( DIVIDE ( [Error^2], COUNTROWS ( Forecast ) ) )

R² =
VAR _avgA = AVERAGE ( Forecast[Actual] )
VAR _ssTot =
    SUMX ( Forecast, POWER ( Forecast[Actual] - _avgA, 2 ) )
VAR _ssRes =
    SUMX ( Forecast, POWER ( Forecast[Actual] - Forecast[Predicted], 2 ) )
RETURN
    IF ( _ssTot = 0, BLANK (), 1 - DIVIDE ( _ssRes, _ssTot ) )

Forecast Bias =
AVERAGEX ( Forecast, Forecast[Predicted] - Forecast[Actual] )

MAPE % =
VAR _mape =
    AVERAGEX (
        FILTER ( Forecast, Forecast[Actual] <> 0 ),
        ABS ( ( Forecast[Actual] - Forecast[Predicted] ) / Forecast[Actual] )
    )
RETURN _mape


📅 8) Date Intelligence (YTD / MTD)

Total Sales YTD =
CALCULATE ( [Total Sales], DATESYTD ( Calendar[Date] ) )

Total Sales MTD =
CALCULATE ( [Total Sales], DATESMTD ( Calendar[Date] ) )

Late % YTD =
CALCULATE ( [Late %], DATESYTD ( Calendar[Date] ) )

On-Time % MTD =
CALCULATE ( [On-Time %], DATESMTD ( Calendar[Date] ) )



🏆 9) Top-N Helpers (Ranked Visuals)


Top N (Parameter) = 5   -- If using a What-If parameter, reference that table instead.

Is In TopN Supplier =
VAR _top =
    TOPN ( [Top N (Parameter)], ALL ( Shipments[Supplier] ), [Supplier Score], DESC )
RETURN
    IF ( CONTAINS ( _top, Shipments[Supplier], SELECTEDVALUE ( Shipments[Supplier] ) ), 1, 0 )


🏷️ 10) Label / UX Helpers


Selected Status (Label) =
VAR s = SELECTEDVALUE ( Shipments[Status], "All Statuses" )
RETURN
    "Status: " & s

Selected Period (Label) =
VAR _min = MIN ( Calendar[Date] )
VAR _max = MAX ( Calendar[Date] )
RETURN
    "Period: " & FORMAT ( _min, "dd MMM yyyy" ) & " → " & FORMAT ( _max, "dd MMM yyyy" )


🧮 11) Data Quality Checks

Missing Delivered Date (Cnt) =
COUNTROWS (
    FILTER (
        Shipments,
        ISBLANK ( Shipments[DeliveredDate] ) && Shipments[Status] = "Delivered"
    )
)

Outlier Delay (>|21| days) =
COUNTROWS ( FILTER ( Shipments, ABS ( [Delay Days] ) > 21 ) )



