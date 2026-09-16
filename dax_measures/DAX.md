# DAX Reference (brief)

Project: Uber trip analysis — key measures, calculated columns, and DAX patterns.

Data sources:
- `Uber Trip Details.xlsx` (trip-level)
- `Location Table.xlsx` (lookup)

Measures (from `Trip Details` table):
- `Total Bookings` = DISTINCTCOUNT('Trip Details'[Trip ID])
- `Total Bookings Value` = SUM('Trip Details'[fare_amount]) + SUM('Trip Details'[Surge Fee])
- `Avg Booking Value` = DIVIDE([Total Bookings Value], [Total Bookings], BLANK())
- `Avg Trip Time` =
  VAR avgtime = ROUND(AVERAGEX('Trip Details', DATEDIFF('Trip Details'[Pickup Time], 'Trip Details'[Drop Off Time], MINUTE)), 0)
  RETURN CONCATENATE(avgtime, " min")
- `Total Trip Distance` (formatted) =
  VAR totalmiles = SUM('Trip Details'[trip_distance]) / 1000
  RETURN CONCATENATE(FORMAT(totalmiles, "0"), "K miles")
- `Total Trip Distance Measure` = SUM('Trip Details'[trip_distance])
- `Avg Trip Distance` =
  VAR avgmiles = ROUND(AVERAGE('Trip Details'[trip_distance]), 0)
  RETURN CONCATENATE(avgmiles, " miles")
- `Most Frequent Pickup Point` uses TOPN + SUMMARIZE and CONCATENATEX to return the top `Location` by count.
- `Most Frequent Dropoff Point` builds DropoffCounts with `ADDCOLUMNS` + `SUMMARIZE`, ranks with `RANKX`, then `CONCATENATEX` of top rows (uses `USERELATIONSHIP` for inactive relationship).
- `Farthest Trip` finds MAX distance and LOOKUPVALUE to get pickup/drop locations, returns formatted string.
- Title measures: `Title for pickup time`, `Title for Day Name`, `Title for Hour & Day` use `SELECTEDVALUE('Dynamic Measure'[Dynamic Title])` to create dynamic headers.

Dynamic Measure table:
- Partitioned calculated table with rows mapping display names to measure names and an order value.
- Columns: `Dynamic Measure`, `Dynamic Measure Fields`, `Dynamic Measure Order`, and calculated `Dynamic Title` (IF on order to produce readable titles).

Calculated columns (examples):
- `Pickup Date` = DATE(YEAR([Pickup Time]), MONTH([Pickup Time]), DAY([Pickup Time]))
- `Pickup Hour` = HOUR([Pickup Time])
- `Trip Type(Day/Night)` = IF(HOUR([Pickup Time]) >= 18 || HOUR([Pickup Time]) < 6, "Night_Shift", "Day Shift")
- `Pickup Time(HH MM SS) (bins)` = binning expression to group time into 10-minute bins.
- `Dropoff Location` uses LOOKUPVALUE against `Location Table` and the `DOLocationID` column.

Common DAX patterns used across the model:
- Aggregations: `SUM`, `DISTINCTCOUNT`, `AVERAGE`, `DIVIDE`.
- Iterators & row context: `AVERAGEX`, `SUMX`, `SELECTEDVALUE`.
- Table manipulation: `SUMMARIZE`, `ADDCOLUMNS`, `TOPN`, `RANKX`.
- Relationship control: `USERELATIONSHIP` for alternate join paths.
- Text & formatting: `FORMAT`, `CONCATENATE`, `CONCATENATEX`.
