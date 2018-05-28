```
SequentialDayNumber = 
COUNTROWS ( 
    FILTER ( 
        ALL ( 'Date' ),
        'Date'[Date] <= EARLIER ( 'Date'[Date] ) &&
        NOT ( MONTH ( 'Date'[Date] ) = 2 && DAY ( 'Date'[Date] ) = 29 )
    )
)
```



