
# Uber Analysis — Short Project Overview

Project: Analysis of Uber trip data (bookings, fares, distances, pickup/drop patterns).

Data sources: `Uber Trip Details.xlsx` (trip-level) and `Location Table.xlsx` (location lookup).

Semantic model (key tables): `Trip Details`, `Location Table`, `Calendar Table`, multiple `LocalDateTable_*` helpers, and a `Dynamic Measure` table for selectable measures.

Primary DAX patterns used:
- aggregations: `SUM`, `DISTINCTCOUNT`, `AVERAGE`, `DIVIDE`;
- row/context functions: `AVERAGEX`, `DATEDIFF`, `SELECTEDVALUE`, `LOOKUPVALUE`;
- table functions: `SUMMARIZE`, `ADDCOLUMNS`, `TOPN`, `RANKX`;
- formatting/strings: `FORMAT`, `CONCATENATE`, `CONCATENATEX`;
- relationship control: `USERELATIONSHIP`.

Notable model features:
- calculated columns for `Pickup Date`, `Pickup Hour`, and `Trip Type (Day/Night)`;
- several hidden measures for cards/headers (Total Bookings, Total Bookings Value, Avg Trip Time, Total Trip Distance, etc.);
- `Dynamic Measure` table provides a parameterized selector used to change displayed metrics and titles.

How to open:
1. Open `uber_Analysis.pbip` with Power BI Desktop.
2. Source files and exported JSON are under `uber_Analysis.Report/` and `uber_Analysis.SemanticModel/`.

If you want this even shorter or want a separate `DAX.md` listing each measure and its formula, tell me and I'll add it.

