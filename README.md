
# Uber Analytics & Ride Insights Dashboard

![Dashboard Overview](overview_sc.png)
![Time Insights](Time%20Sc.png)
![Dashboard Info](Details.png)

<p><strong style="color:#0ea5e9; font-size:13px;">Problem Statement & Objective</strong></p>

Analyze Uber trip data to uncover demand patterns, evaluate fare dynamics, optimize route efficiency, and deliver actionable insights for pricing and resource allocation.

<p><strong style="color:#0ea5e9; font-size:13px;">Technical Approach & Methodology</strong></p>

<p><strong style="color:#0ea5e9; font-size:12px;">Data Modeling:</strong> Built a Star-Schema model connecting the `Trip Details` fact table to `Location Table` and calendar/helper tables via `PULocationID` / `DOLocationID`.</p>

<p><strong style="color:#0ea5e9; font-size:12px;">DAX & Dynamic Analytics:</strong> Custom measures and a `Dynamic Measure` parameter enable on-canvas KPI switching and dynamic titles.</p>

<p><strong style="color:#0ea5e9; font-size:12px;">Spatial & Temporal Analysis:</strong> Mapped location IDs to zones and analyzed bookings by hour/day to identify peaks.</p>

<p><strong style="color:#0ea5e9; font-size:12px;">UI/UX Navigation:</strong> Interactive canvas with bookmarks and quick navigation for drill-through and context-aware headers.</p>

<p><strong style="color:#0ea5e9; font-size:13px;">Key Solutions Delivered</strong></p>

<p><strong style="color:#0ea5e9; font-size:12px;">Demand Identification:</strong> Pinpointed peak hours and high-volume zones for driver allocation.</p>

<p><strong style="color:#0ea5e9; font-size:12px;">Revenue Breakdown:</strong> Analysed base fare vs surge, and payment-mode splits.</p>

<p><strong style="color:#0ea5e9; font-size:13px;">Repository Structure</strong></p>

<ul>
	<li><strong>uber_Analysis.pbip</strong> — Power BI project file.</li>
	<li><strong>uber_Analysis.Report/</strong> — Extracted report JSON, visuals, and static resources.</li>
	<li><strong>uber_Analysis.SemanticModel/</strong> — TMDL model artifacts and `definition.pbism`.</li>
	<li><strong>dax_measures/</strong> — DAX reference files (`DAX.md`, `DAX_FULL.md`).</li>
</ul>
