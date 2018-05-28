```
ISO YTD Sales = 
IF ( 
	HASONEVALUE ( Date[ISO Year Number] ),
	CALCULATE (
		[Sales Amount],
		FILTER (
			ALL ( Date ),
			AND (
				Date[ISO Year Number] = VALUES ( Date[ISO Year Number] ),
				Date[Date] <= MAX ( Date[Date] )
			)
		)
	)
)
```

