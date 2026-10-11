# 🔋 EV Battery Health Analytics

### Predicting State of Health (SoH) and identifying degradation drivers across 6 EV models — informing fleet maintenance, warranty, and inspection priorities.

[![SQL](https://img.shields.io/badge/SQL%20Server-CC2927?logo=microsoftsqlserver&logoColor=white)]()
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)]()
[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)]()
[![Status](https://img.shields.io/badge/Status-Phase%201%20In%20Progress-yellow)]()

---

## 🎯 Business Problem

EV fleet operators and OEMs face two costly challenges:

1. **Reactive maintenance** — batteries fail before being flagged, leading to vehicle downtime and warranty claims.
2. **Generic inspection schedules** — every vehicle is inspected on the same cadence, regardless of actual usage stress.

This project uses 10,000 vehicle records across 6 EV models to answer:

- **Which vehicles should be prioritized for inspection NOW?**
- **What usage patterns predict battery degradation?**
- **Which model/battery-type combinations are most resilient?**

---

## 📌 Project Status

| Phase | Focus | Status |
|---|---|---|
| **1. SQL Foundation** | Database design + analytical queries in SSMS | 🔨 **In progress — Day 13 of 14** |
| 2. Python EDA | Cleaning, visualization, feature importance | ⬜ Upcoming |
| 3. Power BI Dashboard | 3-page interactive report with DAX | ⬜ Upcoming |
| 4. Documentation | README rebuild, screenshots, portfolio post | ⬜ Upcoming |

**Current position:** Phase 1 — queries 1–3 complete, queries 4–12 in progress.

---

## 🛠️ Tools & Stack

| Layer | Tool |
|---|---|
| **Database** | Microsoft SQL Server (SSMS) |
| **Querying** | T-SQL (CASE WHEN, JOINs, GROUP BY, HAVING, subqueries, window functions) |
| **EDA & Modeling** *(Phase 2)* | Python (pandas, scikit-learn) — Google Colab |
| **Dashboard** *(Phase 3)* | Power BI Desktop with DAX |
| **Documentation** | Markdown, GitHub |

---

## 🗂️ Repo Structure

```
.
├── EV-Battery-Health-queries.sql     # Project queries (Phase 1)
├── SQL_Notes.md                      # Concept notes written day by day
├── Project_Context.md                # Project context, skill level, progress
├── Project_Schedule.md               # 4-phase roadmap
├── .gitignore                        # Ignore rules for Python, OS and env files
└── README.md                         # You are here
```

---

## 📐 Dataset Overview

- **Source:** [Electric Vehicle (EV) Battery Degradation & Charge](https://www.kaggle.com/datasets/bertnardomariouskono/electric-vehicle-ev-battery-degradation-and-charge) (Kaggle)
- **Rows:** 10,000 vehicle records | **Columns:** 13
- **Models covered:** Tesla Model 3, Ford Mustang Mach-E, BYD Atto 3, Wuling Air EV, Hyundai Ioniq 5, Kia EV6
- **Chemistries:** LFP (Lithium Iron Phosphate) and NMC (Nickel Manganese Cobalt)
- **Key columns:** `SoH_Percent` (target), `Battery_Type`, `Vehicle_Age_Months`, `Total_Charging_Cycles`, `Avg_Temperature_C`, `Fast_Charge_Ratio`, `Driving_Style`, `Internal_Resistance_Ohm`
- **Lookup table:** `dbo.car_info` — maps `Car_Model` → `Manufacturer_Country`, `Launch_Year`

**Why regression (not classification):** `Battery_Status` is heavily imbalanced — almost every vehicle is labelled Healthy. `SoH_Percent` gives a continuous target instead.

---

## 🔬 Methodology

### Phase 1 — SQL Foundation 🔨 *(in progress)*

- Imported & validated 10,000 rows in SSMS
- Built segmentation logic (Healthy / Warning / Critical) using `CASE WHEN`
- Identified usage tiers (Light / Moderate / Heavy)
- Cross-tabulated risk tiers with model + battery type to surface the findings below
- Created a `car_info` lookup table and joined it to analyse manufacturer country
- Writing business queries to `EV-Battery-Health-queries.sql`

### Phase 2 — Python EDA *(upcoming)*
- Distribution analysis on SoH_Percent
- Correlation matrix: usage variables vs. degradation
- Feature importance via Random Forest (interpretability)
- Validate SQL findings with statistical tests

### Phase 3 — Power BI Dashboard *(upcoming)*
- 3-page report: Fleet KPIs / Risk Tiers / Model Comparison
- DAX measures for SoH%, risk counts, time-to-replacement estimates
- Drill-through to vehicle-level detail

### Phase 4 — Documentation *(upcoming)*
- Rebuild this README with final results and screenshots
- LinkedIn portfolio post with insight carousel

---

## 📊 Findings So Far

### Project queries (saved in `EV-Battery-Health-queries.sql`)

**Query 1 — Battery chemistry performance**

| Battery Type | Vehicles | Avg SoH | Avg Internal Resistance |
|---|---|---|---|
| NMC | 6,021 | 95.05% | 0.0349 Ω |
| LFP | 3,980 | 96.95% | 0.0261 Ω |

*Takeaway: LFP holds health better and runs at lower internal resistance than NMC.*

**Query 2 — Manufacturer country** *(FULL OUTER JOIN + ISNULL)*

| Country | Vehicles | Avg SoH |
|---|---|---|
| China | 3,980 | 96.95% |
| USA | 4,017 | 95.05% |
| South Korea | 2,003 | 95.04% |
| UNKNOWN | 1 | 95.00% |
| Japan | 0 | — |

*Data-quality finding: Kia EV6 exists in the battery data but has no matching row in the country lookup — labelled `UNKNOWN`. Nissan Leaf and Rivian R1T exist in the lookup but have no vehicles in the data.*

**Query 3 — High-risk vehicles for inspection**
- Rule: `(SoH_Percent < 90 AND Vehicle_Age_Months > 24) OR Battery_Status IN ('Critical','Warning')`
- Result: **605 priority rows**, sorted by lowest health first

### Exploratory findings (from SQL practice sessions)

- 🏆 **Wuling Air EV leads on battery health** — average SoH of **96.99%**, highest of the models analysed
- 🚨 **267 vehicles flagged "stressed"** — high temperature exposure + high discharge rate. Next inspection priority.
- 🚨 **778 Tesla Model 3s at risk** — meet either condition: age > 60 months OR > 800 charging cycles. A concrete warranty-watch list.
- 📊 **SoH-based segmentation:** 9,390 Healthy / 609 Warning / 1 Critical
- 🔥 **The only Critical battery sits in the Heavy-usage segment** — usage intensity drives end-of-life risk more than age alone
- 🔬 **182 LFP vehicles tie at exactly 100% SoH** — a clean real-world case of `RANK()` skipping 1 → 183 while `DENSE_RANK()` moves 1 → 2

---

## 💻 How to Reproduce

```sql
-- 1. Download the dataset from Kaggle:
--    https://www.kaggle.com/datasets/bertnardomariouskono/electric-vehicle-ev-battery-degradation-and-charge

-- 2. Create the database in SSMS
CREATE DATABASE EV_Projects;
GO
USE EV_Projects;
GO

-- 3. Import the CSV → dbo.ev_battery_data
-- 4. Create dbo.car_info (Car_Model, Manufacturer_Country, Launch_Year)
-- 5. Run the queries in EV-Battery-Health-queries.sql in order
```

---

## 🧠 What I Learned

- **Technical:** SQL aggregations + `CASE WHEN` handle most segmentation work normally pushed into BI tools — keeping logic close to the data.
- **Analytical:** Imbalanced targets force you to reframe the problem — switching from classification to regression was the right call here.
- **Data quality:** Outer joins are how you *find* broken reference data, not just avoid it. The Kia EV6 gap only became visible through a FULL OUTER JOIN.
- **Business:** The most useful output isn't a model — it's *named segments* (the 267 stressed vehicles, the 778 at-risk Teslas) that an ops team can act on tomorrow.

---

## 🚧 Limitations & Next Steps

- **Limitations:** Single-snapshot dataset (no temporal degradation tracking); the Critical class is extremely rare (n=1); no maintenance-cost data, so no ROI claims are made.
- **Next:** Finish Phase 1 queries, then Phase 2 Python EDA to confirm the SQL findings statistically, then Phase 3 Power BI for stakeholder-ready visuals.

---

## 📬 Author

**Jitender Maan** — Data Analyst (in transition from MIS Executive)
🌐 [Portfolio](https://jitenderda.github.io) · 💼 [LinkedIn](https://www.linkedin.com/in/jitender-da) ·
📍 Sonipat, Haryana

*Open to Data Analyst opportunities — remote or hybrid.*
