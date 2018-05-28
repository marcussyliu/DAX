#standard time intelligence function

```
[YTD Sales]:=
CALCULATE (
	[Sales Amount],
	DATESYTD ( Date[Date] )
)
```

```
[YTD Sales]:=
TOTALYTD ( [Sales Amount], Date[Date] )
```



#customized expression for regular ( Gregorian) calendar

```
[YTD Sales]:=
CALCULATE (
	[Sales Amount],
	FILTER (
		ALL ( Date[Date] ),
		AND (
			Date[Date] <= MAX ( Date[Date] ),
			YEAR ( Date[Date] ) = YEAR ( MAX ( Date[Date] ) )
		)
	)
)
```



# customized expression for both custom and standard calendars

```
[YTD Sales]:=
CALCULATE (
	[Sales Amount],
	FILTER (
		ALL ( Date ),
		AND (
			Date[Date] <= MAX ( Date[Date] ),
			Date[Calendar Year Number] = MAX ( Date[Calendar Year Number] )
		)
	)
)
```

