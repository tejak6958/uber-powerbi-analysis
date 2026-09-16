# 🚕 Uber Power BI Analysis

An end-to-end **Power BI analytics project** focused on understanding Uber trip demand, revenue patterns, trip behaviour, and operational performance through interactive business intelligence.

The project combines **data modelling, Power Query, DAX, time-based analysis, spatial analysis, and interactive Power BI reporting** to turn raw trip data into business-oriented insights.

## 🎯 Business Objective

The goal of this analysis is to answer questions such as:

* When and where is trip demand highest?
* Which locations generate the most trip activity?
* How do fares and trip characteristics vary over time?
* What patterns can be observed across different payment methods?
* How can trip and location data be used to understand operational demand?

## 🛠️ Tools & Technologies

* **Power BI**
* **Power Query**
* **DAX**
* **Data Modelling**
* **Power BI Project (PBIP)**
* **TMDL / Semantic Model**
* **Excel**

## 📐 Data Modelling

The project uses a **star-schema approach** to organize the analytical model and support efficient reporting.

The model separates transactional trip information from supporting dimensions, enabling analysis across:

* Date and time
* Location
* Trip characteristics
* Fare and payment information

This structure makes it easier to create reusable DAX measures and analyse the data from multiple business perspectives.

## 📊 Dashboard & Analysis

The report provides interactive analysis across several areas:

### Demand Analysis

* Trip volume by time
* Peak-period analysis
* High-volume locations
* Demand patterns across different periods

### Revenue & Fare Analysis

* Fare distribution
* Revenue-related trends
* Fare behaviour across trip characteristics
* Payment-mode analysis

### Location & Spatial Analysis

* Pickup and drop-off patterns
* High-activity locations
* Geographic distribution of trips
* Location-level demand patterns

### Operational Analysis

* Trip behaviour and volume
* Route-related patterns
* Identification of areas with higher demand
* Interactive drill-through analysis

## 🧮 DAX & Analytics

Custom DAX measures are used to calculate and analyse key metrics within the report.

The project also uses **dynamic measure selection** to allow users to switch analytical metrics interactively within the dashboard.

Additional Power BI functionality includes:

* Time-based calculations
* KPI measures
* Dynamic analysis
* Drill-through
* Bookmarks
* Interactive navigation

## 🔍 Key Insights

The dashboard is designed to help identify:

* Peak demand periods
* High-activity pickup and drop-off areas
* Changes in trip behaviour over time
* Fare and payment patterns
* Areas requiring further operational investigation

> **Note:** Specific numerical findings should be added here after validating the final dashboard. This section intentionally avoids inventing business results that are not documented in the project.

## 📸 Dashboard Preview

Add your best dashboard screenshots below.

### Overview

![Uber Power BI Dashboard](screenshots/overview.png)

### Demand Analysis

![Demand Analysis](screenshots/demand-analysis.png)

### Location Analysis

![Location Analysis](screenshots/location-analysis.png)

## 📁 Project Structure

```text
uber-powerbi-analysis/
│
├── Report/
├── SemanticModel/
├── screenshots/
├── data/
├── DAX/
├── README.md
└── ...
```

The repository is maintained as a **Power BI Project (PBIP)** so that the report and semantic-model components can be version-controlled and reviewed through GitHub.

## 💡 What I Learned

This project helped strengthen my practical experience with:

* Building analytical data models
* Creating reusable DAX measures
* Designing interactive Power BI reports
* Analysing time and location-based business data
* Translating raw data into business questions and insights
* Managing Power BI project artifacts through Git/GitHub

## 🚀 Future Improvements

Potential extensions include:

* Adding more advanced time-series analysis
* Building additional geographic analysis
* Adding automated data refresh workflows
* Connecting the reporting layer to a modern data platform such as **Microsoft Fabric**
* Extending the project into an end-to-end analytics engineering pipeline

---

### 👤 About Me

**Teja — Data Analyst | SQL | Power BI | Python | Microsoft Fabric**

I have 3+ years of professional experience as a Data Analyst at Wipro, with experience in SQL analytics, Power BI, automation, experimentation, and statistical validation.

I'm currently expanding my skills toward **Analytics Engineering and Data Engineering**, including hands-on work with Microsoft Fabric.

[LinkedIn](https://www.linkedin.com/in/k-teja/) • [GitHub](https://github.com/tejak6958)
