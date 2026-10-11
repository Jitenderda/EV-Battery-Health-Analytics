# EV Battery Health Analytics

Analysis of 10,000 EV battery records to understand what drives battery degradation, and which vehicles a fleet operator should inspect first.

I built this to practise end-to-end analytics: SQL Server for the analysis, then Python for exploration, then Power BI for the dashboard.

## The problem

EV batteries lose capacity as they age and as they are used. How much they lose depends on how the vehicle is charged and driven: how often it is fast charged, how hot the battery runs, how many charge cycles it has done.

Most fleet operators inspect every vehicle on the same schedule. Vehicles that get used gently get inspected too often, and hard-used ones may not get looked at soon enough. I want to see whether the data can point to the vehicles that are actually at risk, so inspections can be prioritised.

## Tools

- SQL Server (SSMS) - analysis
- Python (pandas, scikit-learn) - exploratory analysis, phase 2
- Power BI - dashboard, phase 3

## The data

Source: EV Battery Degradation & Charge, found on Kaggle.

10,000 rows and 13 columns, covering six EV models: Tesla Model 3, Ford Mustang Mach-E, BYD Atto 3, Wuling Air EV, Hyundai Ioniq 5 and Kia EV6. The batteries are either LFP or NMC chemistry. The column I am working with most is SoH_Percent, the battery's State of Health.

I also created a small lookup table called car_info, which maps each model to its manufacturer country, so I could practise joins.

One decision worth explaining. Battery_Status could be treated as a classification target, but nearly every vehicle in the data is labelled Healthy. The classes are far too imbalanced for that to work, so I am treating this as a regression problem on SoH_Percent instead.

## Progress

Phase 1 started on 18 May and is still running. 3 of 12 queries are written.

| Phase | What | Status |
| --- | --- | --- |
| 1. SQL | Analytical queries in SSMS | In progress |
| 2. Python EDA | Distributions, correlations, feature importance | Not started |
| 3. Power BI | Three page dashboard | Not started |
| 4. Documentation | Report and portfolio write up | Not started |

## What I have found so far

### Battery chemistry

LFP batteries hold their health better than NMC in this data. Average SoH is 96.95% for LFP against 95.05% for NMC. LFP also runs at lower internal resistance, 0.0261 against 0.0349.

### Manufacturer country

China leads on average SoH at 96.95%, followed by the USA at 95.05% and South Korea at 95.04%.

While writing this query I found a data quality problem. Kia EV6 appears in the battery data but has no matching row in the country lookup table, so it comes back as UNKNOWN. Nissan Leaf and Rivian R1T are in the lookup table but have no vehicles in the battery data at all.

### Vehicles needing inspection

I wrote a query to pull out vehicles that look like priority cases: SoH below 90% and older than 24 months, or flagged as Critical or Warning. It returned 605 vehicles, sorted worst first.

### Other things I noticed while practising

- Wuling Air EV has the highest average SoH of any model, at 96.99%
- 267 vehicles show both high temperature exposure and a high discharge rate
- 778 Tesla Model 3s are either older than 60 months or past 800 charge cycles
- Battery health splits 9,390 Healthy, 609 Warning, 1 Critical. The single Critical battery sits in the heavy usage group
- 182 LFP vehicles tie at exactly 100% SoH, which turned out to be a good way to see the difference between RANK and DENSE_RANK

## Running this yourself

1. Download the dataset from Kaggle (link above)
2. Create a database in SSMS called EV_Projects
3. Import the CSV into dbo.ev_battery_data
4. Create dbo.car_info with the columns Car_Model, Manufacturer_Country and Launch_Year
5. Run the queries in EV-Battery-Health-queries.sql in order

## What I learned

SQL aggregations and CASE WHEN do more of the work than I expected. Most of the segmentation I thought I would need Power BI for was fine inside the query.

The imbalanced target also taught me something. My first instinct was to build a classifier, but starting with the data rather than the technique saved me from weeks of dead ends.

## Limitations

The data is a single snapshot, so I cannot track how any individual battery degrades over time. There is only one Critical battery, which is too few to build anything on. There is also no maintenance cost data, so I have not made any claims about savings.

## About me

Jitender Maan, Data Analyst. Based in Sonipat, Haryana.

Portfolio: https://jitenderda.github.io
LinkedIn: https://www.linkedin.com/in/jitender-da

Open to Data Analyst roles, remote or hybrid.
