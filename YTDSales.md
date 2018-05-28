```
YTDSales = 
	CALCULATE ( 
		[Sales], 
		FILTER (
			ALL ( Date ),
			Date[Year] = MAX ( Date[Year] ) &&
			Date[Date] <= MAX ( Date[Date] )
		)
     )
```

