```
ISO FY Sales: = 
IF (
	HASONEVALUES ( Date[ISO Year Number] ),
	CALCULATE (
		[Sale Amount],
		FILTER (
			All ( Date ),
			AND (
				Date[ISO Year Number] = VALUES ( Date[ISO Year Number] ),
				CONTAINS (
					VALUES ( Date[ISO Year Day Number] ),
					Date[ISO Year Day Number],
					Date[ISO Year Day Number]
				)
			)
		)
	)
)
```

