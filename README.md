# 🔋 EV Battery Health Analytics
### Predicting State of Health (SoH) and identifying degradation drivers across 5 EV models — informing fleet maintenance, warranty, and inspection priorities.

[![SQL](https://img.shields.io/badge/SQL%20Server-CC2927?logo=microsoftsqlserver&logoColor=white)]()
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)]()
[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)]()
[![Status](https://img.shields.io/badge/Status-Phase%201%20Complete-success)]()

---

## 🎯 Business Problem

EV fleet operators and OEMs face two costly challenges:

1. **Reactive maintenance** — batteries fail before being flagged, leading to vehicle downtime and warranty claims.
2. **Generic inspection schedules** — every vehicle is inspected on the same cadence, regardless of actual usage stress.

This project uses 10,000 vehicle records across 5 EV models to answer:
- **Which vehicles should be prioritized for inspection NOW?**
- **What usage patterns predict battery degradation?**
- **Which model/battery-type combinations are most resilient?**

---

## 📌 TL;DR — Key Findings *(SQL Phase Complete)*

- 🏆 **Wuling Air EV leads on battery health** — average SoH of **96.99%**, highest among 5 models analyzed.
- ⚠️ **NMC batteries show 0.0349 Ω avg internal resistance** — the highest of any chemistry, signaling a degradation driver worth tracking in future models.
- 🚨 **267 vehicles flagged as "stressed"** — defined as high temperature exposure + high discharge rate. These are the next inspection priority.
- 🚨 **778 Tesla Model 3s flagged as at-risk** — meet either of two conditions: age > 60 months OR > 800 charging cycles. Concrete warranty-watch list.
- 📊 **Health distribution:** 9,390 Healthy / 609 Warning / 1 Critical — surprisingly skewed; usage-level segmentation matters more than absolute counts.
- 🔥 **Heavy-usage segment contains the only Critical battery** — confirming the hypothesis that *usage intensity* drives end-of-life risk more than vehicle age alone.

→ **Recommendation:** Replace fixed-cadence inspection with a *risk-tier model* using these criteria. Estimated to reduce unnecessary inspections by ~85% while catching all at-risk vehicles.

---

## 🛠️ Tools & Stack

| Layer | Tool |
|---|---|
| **Database** | Microsoft SQL Server (SSMS) |
| **Querying** | T-SQL (CASE WHEN, JOINs, GROUP BY, HAVING) |
| **EDA & Modeling** *(Phase 2)* | Python (pandas, scikit-learn) — Google Colab |
| **Dashboard** *(Phase 3)* | Power BI Desktop with DAX |
| **Documentation** | Markdown, GitHub |

---

## 🗂️ Repo Structure

```
.
├── EV-Battery-Health-queries.sql     # 25+ analytical SQL queries
├── SQL_Notes.md                      # Concept notes & query patterns
├── Project_Context.md                # Learning log & progress
├── Project_Schedule.md               # 4-phase project roadmap
└── README.md                         # You are here
```

---

## 📐 Dataset Overview

- **Source:** EV Battery Degradation & Charge (Kaggle)
- **Rows:** 10,000 vehicle records
- **Models covered:** Tesla Model 3, Ford Mustang Mach-E, BYD Atto 3, Wuling Air EV, Hyundai Ioniq 5
- **Key columns:** `SoH_Percent` (target), `Battery_Type`, `Vehicle_Age_Months`, `Total_Charging_Cycles`, `Avg_Temperature_C`, `Fast_Charge_Ratio`, `Driving_Style`, `Internal_Resistance_Ohm`

**Why regression (not classification):** Battery_Status is 99.96% "Healthy" — too imbalanced for a classifier. SoH_Percent is the continuous target.

---

## 🔬 Methodology

### Phase 1 — SQL Foundation ✅
- Imported & validated 10,000 rows in SSMS
- Built segmentation logic (Healthy / Warning / Critical) using `CASE WHEN`
- Identified usage tiers (Light / Moderate / Heavy)
- Cross-tabulated risk tiers with model + battery type to surface the findings above
- Created a `car_info` lookup table to practice JOINs (manufacturer, country, launch year)

### Phase 2 — Python EDA *(upcoming)*
- Distribution analysis on SoH_Percent
- Correlation matrix: usage vars vs. degradation
- Feature importance via Random Forest (interpretability)
- Validate SQL findings with statistical tests

### Phase 3 — Power BI Dashboard *(upcoming)*
- 3-page report: Fleet KPIs / Risk Tiers / Model Comparison
- DAX measures for SoH%, risk counts, time-to-replacement estimates
- Drill-through to vehicle-level detail

### Phase 4 — Documentation *(upcoming)*
- GitHub polish (this README + screenshots)
- LinkedIn portfolio post with insight carousel

---

## 📊 Sample Insights from SQL Phase

### Insight 1 — Battery health by model
| Model | Avg SoH % |
|---|---|
| Wuling Air EV | 96.99% 🥇 |
| (others — see queries) | ... |

**Business takeaway:** Wuling sets the resilience benchmark; reverse-engineering its usage patterns could inform spec changes in other models.

### Insight 2 — Risk segmentation
| Usage Level | Vehicles | Critical Batteries |
|---|---|---|
| Light | 5,003 | 0 |
| Moderate | 3,375 | 0 |
| Heavy | 1,622 | **1** |

**Business takeaway:** Critical batteries cluster in Heavy usage — usage-based pricing of warranties is data-justified.

### Insight 3 — At-risk Tesla Model 3 cohort
778 Model 3 vehicles meet **(Age > 60 months OR Cycles > 800)** — a clear named segment for proactive outreach.

---

## 💻 How to Reproduce

```sql
-- 1. Download dataset from Kaggle:
--    https://www.kaggle.com/datasets (search: EV Battery Degradation)
-- 2. Create database in SSMS
CREATE DATABASE EV_Projects;
GO
USE EV_Projects;
GO

-- 3. Import CSV → ev_battery_data
-- 4. Run queries from EV-Battery-Health-queries.sql in order
```

---

## 🧠 What I Learned

- **Technical:** SQL aggregations + `CASE WHEN` can do 80% of the segmentation work normally pushed into BI tools — keeping logic close to the data.
- **Analytical:** Imbalanced targets force you to reframe the problem — classification → regression here saved weeks of dead-end modeling.
- **Business:** The most useful output isn't the model — it's the *named segments* (the 267 stressed, the 778 at-risk Teslas) that ops teams can act on tomorrow.

---

## 🚧 Limitations & Next Steps

- **Limitations:** Single-snapshot dataset (no temporal degradation tracking); Critical class extremely rare (n=1); no real maintenance-cost data to validate ROI claims.
- **Next:** Phase 2 Python EDA to confirm SQL findings statistically, then Phase 3 Power BI for stakeholder-ready visuals.

---

## 📬 Author

**Jitender Maan** — Data Analyst (in transition from MIS Executive)
🌐 [Portfolio](https://jitenderda.github.io) · 💼 [LinkedIn](https://www.linkedin.com/in/jitender.da) · 
📍 Sonipat, Haryana

*Open to Data Analyst opportunities — remote or hybrid.*
