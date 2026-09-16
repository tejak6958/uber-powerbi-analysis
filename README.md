
# Uber Analytics & Ride Insights Dashboard
Problem Statement & Objective

Analyze Uber trip data to uncover demand patterns, evaluate fare dynamics, optimize route efficiency, and deliver actionable insights for pricing and resource allocation.

![Dashboard Overview](overview_sc.png)
![Time Insights](Time%20Sc.png)
![Dashboard Info](Details.png)

Technical Approach & Methodology
Data Modeling: Built a Star-Schema model connecting the Trip Details fact table to Location Lookup and dynamic Calendar dimension tables via PULocationID / DOLocationID.

DAX & Dynamic Analytics: Developed custom DAX measures and field parameters to enable dynamic KPI switching across visual charts.

Spatial & Temporal Analysis: Mapped numerical location IDs to actual boroughs and zones, analyzing booking trends across peak and off-peak hours.

UI/UX Navigation: Designed an interactive canvas with page navigators, dynamic bookmarks, and URL action buttons linking to source documentation.

Key Solutions Delivered
Demand Identification: Pinpointed peak ride hours and high-volume pickup/drop-off zones for strategic driver placement.

Revenue Breakdown: Evaluated base fare vs. surge pricing trends and analyzed payment mode distributions (Cash vs. Card).

Repository Structure
uber_Analysis.pbip: Main Power BI Project file.

uber_Analysis.Report/: Page layouts, visual configs, and visual theme settings.

uber_Analysis.SemanticModel/: Data schema, table relationships, and DAX calculations.
