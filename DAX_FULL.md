# DAX Full — verbatim measures and calculated columns

This file contains the exact DAX/formulas extracted from the semantic model (`Trip Details` and `Dynamic Measure`). Use as a reference.

## Measures (Trip Details)

- Total Bookings
```
DISTINCTCOUNT('Trip Details'[Trip ID] )
```

- Total Bookings Value
```
sum('Trip Details'[fare_amount]) + SUM('Trip Details'[Surge Fee])
```

- Avg Booking Value
```
divide([Total Bookings Value], [Total Bookings],BLANK())
```

- Avg Trip Time
```
var avgtime = round(AVERAGEX('Trip Details',DATEDIFF('Trip Details'[Pickup Time],'Trip Details'[Drop Off Time],MINUTE) ),0)
return 
CONCATENATE(avgtime," min")
```

- Total Trip Distance
```
 
 VAR totalmiles =  SUM('Trip Details'[trip_distance]) / 1000
  RETURN
  CONCATENATE(FORMAT(totalmiles,"0"),"K miles")
```

- Avg Trip Distance
```
Var avgmiles = round(AVERAGE('Trip Details'[trip_distance]),0.0)

return 
CONCATENATE(avgmiles," miles")
```

- Total Trip Distance Measure
```
SUM('Trip Details'[trip_distance])
```

- Title for Grid
```
"Vehicle Type Analysis"
```

- Most Frequent Pickup Point
```
VAR Pickpoint = TOPN(1, 
                     SUMMARIZE('Trip Details','Location Table'[Location], "Pick Point", COUNT('Trip Details'[Trip ID]))
                     ,[Pick Point],DESC)

RETURN CONCATENATEX(Pickpoint,'Location Table'[Location], ",")
```

- Most Frequent Dropoff Point
```
// Step 1: Create a grouped table with dropoff counts using the inactive relationship
VAR DropoffCounts = 
ADDCOLUMNS(
    SUMMARIZE('Trip Details', 'Location Table'[Location]),
    "Dropoffcount",
    CALCULATE(COUNT('Trip Details'[Trip ID]),
            USERELATIONSHIP('Trip Details'[DOLocationID],'Location Table'[LocationID]))
    )
 /* Step 2: Rank the locations by count. 
   Using DENSE ensures ties share the same rank. */
  VAR RankedDropOff = 
                ADDCOLUMNS
                (
                DropoffCounts, "Rank",
                RANKX(DropoffCounts,[Dropoffcount],,DESC,Dense)
                )
// Step 3: Filter for top ranked location(s) and combine as a string                
VAR TopDropOff = 
        FILTER(RankedDropOff, [Rank] = 1)

Return CONCATENATEX(TopDropOff, 'Location Table'[Location],",")
```

- Farthest Trip
```
VAR MaxDistance = MAX('Trip Details'[trip_distance])

VAR PickupLocation =
   LOOKUPVALUE('Location Table'[Location],
                'Location Table'[LocationID],
                CALCULATE(
                    SELECTEDVALUE('Trip Details'[PULocationID]),
                                  'Trip Details'[trip_distance] = MaxDistance
                                  )
        )
   

VAR DropoffLocation = 
 LOOKUPVALUE('Location Table'[Location],
                'Location Table'[LocationID],
                CALCULATE(
                    SELECTEDVALUE('Trip Details'[DOLocationID]),
                                  'Trip Details'[trip_distance] = MaxDistance
                                  )
        )
   

return "Pickup: " & PickupLocation & " → Drop-Off: " & DropoffLocation & " (" & FORMAT(MaxDistance, "0.0") & "Miles)" 
```

- Title for Location
```
"Location Analysis"
```

- Title for pickup time
```
SELECTEDVALUE('Dynamic Measure'[Dynamic Title]) & " by Pickup Time"
```

- Title for Day Name
```
SELECTEDVALUE('Dynamic Measure'[Dynamic Title]) & " by Day Name"
```

- Title for Hour & Day
```
SELECTEDVALUE('Dynamic Measure'[Dynamic Title]) & " by Hour & Day"
```

## Calculated columns (Trip Details)

- Pickup Date
```
DATE(YEAR('Trip Details'[Pickup Time]),MONTH('Trip Details'[Pickup Time]),DAY('Trip Details'[Pickup Time]))
```

- Trip Type(Day/Night)
```
VAR HourOfDay = HOUR('Trip Details'[Pickup Time])

RETURN
if (HourOfDay >= 18 || HourOfDay < 6,  "Night_Shift" , "Day Shift")
```

- Pickup Time(HH MM SS)
```
TIME(HOUR('Trip Details'[Pickup Time]),MINUTE('Trip Details'[Pickup Time]),SECOND('Trip Details'[Pickup Time]))
```

- Pickup Time(HH MM SS) (bins)
```
IF(
    ISBLANK('Trip Details'[Pickup Time(HH MM SS)]),
    BLANK(),
    (INT(('Trip Details'[Pickup Time(HH MM SS)] * 1440) / 10) * 10) / 1440
)
```

- Pickup Hour
```
HOUR('Trip Details'[Pickup Time])
```

- Dropoff Location
```
var currentDO = 'Trip Details'[DOLocationID]

RETURN
LOOKUPVALUE('Location Table'[Location],'Location Table'[LocationID],currentDO)
```

## Dynamic Measure table details

- Partition source (calculated table rows):
```
{
    ("Total Bookings", NAMEOF('Trip Details'[Total Bookings]), 0),
    ("Total Bookings Value", NAMEOF('Trip Details'[Total Bookings Value]), 1),
    ("Total Trip Distance", NAMEOF('Trip Details'[Total Trip Distance Measure]), 2)
}
```

- Dynamic Title (calculated column)
```
if( 'Dynamic Measure'[Dynamic Measure Order] = 0, "Total Bookings",
if( 'Dynamic Measure'[Dynamic Measure Order] = 1, "Total Bookings Value",
if( 'Dynamic Measure'[Dynamic Measure Order] = 2, "Total Trip Distance",
"others"
)
)
)
```

---
