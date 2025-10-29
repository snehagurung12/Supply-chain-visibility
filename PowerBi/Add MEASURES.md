# DAX Measures
### Total Orders
```DAX
Total Orders = DISTINCTCOUNT(Orders[OrderID])

On-Time % =
VAR ontime = CALCULATE([Total Shipments], FILTER(Shipments, [Late Flag] = 0))
RETURN DIVIDE(ontime, [Total Shipments])


