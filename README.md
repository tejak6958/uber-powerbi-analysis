
# Uber Analytics & Ride Insights Dashboard
An end-to-end Power BI project analyzing Uber trip data to identify ride demand patterns, peak booking hours, revenue trends, and spatial pickup/drop-off behavior.

Key Features & Insights
Ride Trend Analysis: Tracks total bookings, trip distances, and average duration across different times of day.

Geographic Mapping: Connects pickup and drop-off location IDs to real-world zones and boroughs for spatial visualization.

Dynamic Metric Selection: Uses a parameter-driven measure table to allow interactive switching between key KPIs on visuals.

Revenue & Surge Tracking: Analyzes base fares, surge pricing patterns, and payment preferences (Cash vs. Card).

Project Structure
uber_Analysis.pbip: Main Power BI Project file.

uber_Analysis.Report/: Visual layout, canvas pages, and formatting JSON files.

uber_Analysis.SemanticModel/: Data model, relationships, and DAX calculations (TMDL).

Data Modeling.png: Screenshot of the data model schema.

Data Sources & Model
Trip Details (Uber Trip Details.xlsx): Fact table containing trip IDs, timestamps, passenger counts, distance, payment types, and fare breakdown.

Location Lookup (Location Table.xlsx): Dimension table mapping LocationID to Borough, Zone, and Service Zone.

Relationships: Star-schema model linked via PULocationID / DOLocationID to LocationID, integrated with custom Calendar and Dynamic Measure tables.
