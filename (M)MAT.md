```
MAT = 
CALCULATE(
    [Sales],
    FILTER (
        ALL ( 'Date' ),
        'Date'[SequentialDayNumber] > MAX ( 'Date'[SequentialDayNumber] ) -365 &&
        'Date'[SequentialDayNumber] <= MAX ( 'Date'[SequentialDayNumber] )
    )
)    
```

