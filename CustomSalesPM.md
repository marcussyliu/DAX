```
SalesPM =
SUMX (
    VALUES ( 'Date'[Month Sequential Number] ),
    IF (
        CALCULATE ( COUNTROWS ( VALUES ( 'Date'[Date] ) ) )
            = CALCULATE ( VALUES ( 'Date'[Days in Month] ) ),
        CALCULATE (
            [Sales Amount],
            ALL ( 'Date' ),
            FILTER (
                ALL ( 'Date'[Month Sequential Number] ),
                'Date'[Month Sequential Number]
                    = EARLIER ( 'Date'[Month Sequential Number] ) - 1
            )
        ),
        CALCULATE (
            [Sales Amount],
            ALL ( 'Date' ),
            CALCULATETABLE ( VALUES ( 'Date'[Day of Month] ) ),
            FILTER (
                ALL ( 'Date'[Month Sequential Number] ),
                'Date'[Month Sequential Number]
                    = EARLIER ( 'Date'[Month Sequential Number] ) - 1
            )
        )
    )
)
```

Using the same formulas, you can implement a comparison over the previous quarter or year by
simply subtracting 3 or 12 instead of 1 from the Month Sequential Number



```
PYSalesAmount =
CALCULATE (
    [Sales Amount],
    FILTER (
        ALL ( Date ),
        CONTAINS (
            VALUES ( Date[Date Previous Year] ),
            Date[Date Previous Year], Date[Date]
        )
    )
)

```

This is on the assumption that the corresponding date in previous year for each date selected can be defined as a calculated column in the Date table.  There is a limit in this approach, because it can only apply to comparison with the previous year result. It is unwise to add additional calculated columns in the data model for calculation of corresponding dates in other periods. Anyway, you have no idea how uses are gonna use the measure you have created.