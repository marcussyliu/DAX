```
FiscalYTDSales =
TOTALYTD ( [Sales Amount], Date[Date], "06-30" )

```

```
FiscalYTDSalesAlt =
CALCULATE ( [Sales Amount], DATESYTD ( Date[Date], "06-30" ) )

```

