# 📊 Data Dictionary

| Dataset | Field | Description | Example |
|----------|--------|-------------|----------|
| **Orders** | OrderID | Unique identifier for each order | O1001 |
|  | OrderDate | Date order was placed | 2023-04-12 |
|  | ProductCategory | Product group name | Electronics |
|  | Quantity | Quantity ordered | 5 |
|  | TotalAmount | Total sales amount | 520.50 |
| **Shipments** | ShipmentID | Unique shipment code | S458 |
|  | ShipDate | Shipment date | 2023-04-15 |
|  | DeliveredDate | Actual delivery date | 2023-04-19 |
|  | Route | Region or delivery path | Adelaide → Sydney |
|  | Carrier | Transport company | FedEx |
| **Suppliers** | SupplierID | Supplier code | SUP01 |
|  | SupplierName | Supplier name | Global Freight |
|  | LeadTimeDays | Avg days to deliver | 5 |
|  | Rating | Internal score (1–5) | 4 |
| **Forecast_Fact** | Date | Monthly date | 2023-05-01 |
|  | Forecast | Predicted demand | 5200 |
|  | Actual | Actual demand | 4970 |

