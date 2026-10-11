# EV Battery Health Analytics — Project Context

> **Current-state file.** Replaces the stacked chat summaries (all historical blocks removed).
> **Last updated:** 12-10-2026
> **Current position:** Phase 1 — Day 13, Query 4 (in progress)

---

## 1. About Me

- **Name:** Jitender Maan
- **GitHub:** github.com/Jitenderda
- **LinkedIn:** linkedin.com/in/jitender-da
- **Repo:** https://github.com/Jitenderda/EV-Battery-Health-Analytics
- **Daily project slot:** 9:30 AM – 11:30 AM (Mon–Sat) | Sundays off

---

## 2. Skill Level (Honest)

- SQL: Beginner
- Python: Beginner
- Power BI: Intermediate, needs depth

---

## 3. Project Details

- **Title:** Predictive Battery Health Analytics for Electric Vehicles
- **Dataset:** EV Battery Degradation & Charge (Kaggle)
- **Rows:** 10,000 | **Columns:** 13
- **Target Variable:** SoH_Percent
- **Problem Type:** Regression
- **Why regression:** Battery_Status is 99.96% "Healthy" — too imbalanced for classification

---

## 4. Database & Tables

**Tool:** SSMS | **Database:** EV_Projects

### dbo.ev_battery_data (main table, 10,000 rows)
Vehicle_ID, Car_Model, Battery_Type, Battery_Capacity_kWh, Vehicle_Age_Months,
Total_Charging_Cycles, Avg_Temperature_C, Fast_Charge_Ratio, Avg_Discharge_Rate_C,
Driving_Style, Internal_Resistance_Ohm, SoH_Percent, Battery_Status

### dbo.car_info (lookup table)
Car_Model, Manufacturer_Country, Launch_Year

Contains: Ford Mustang Mach-E, BYD Atto 3, Wuling Air EV, Hyundai Ioniq 5,
Tesla Model 3, Nissan Leaf, Rivian R1T

### Known join findings
- 6 models appear in the battery data (5 with country lookup + Kia EV6)
- **Kia EV6** exists in the battery data but has no matching row in car_info → labelled `'UNKNOWN'`
- **Nissan Leaf** and **Rivian R1T** exist in car_info but have no vehicles in the battery data

---

## 5. Tool Stack

- **Database:** Microsoft SQL Server (SSMS) — work PC
- **Notes:** SQL_Notes.md on GitHub (Markdown)
- **Python:** Google Colab (Phase 2)
- **Dashboard:** Power BI (Phase 3)

---

## 6. 4-Phase Project Plan

1. **Phase 1: SQL** (CURRENT) — database design + analytical queries in SSMS
2. **Phase 2: Python EDA** — cleaning, visualization, feature importance
3. **Phase 3: Power BI** — 3-page dashboard with DAX measures
4. **Phase 4: Documentation** — README polish + LinkedIn portfolio post

---

## 7. Working Rules (NON-NEGOTIABLE)

- ✅ One question at a time, wait for my answer
- ✅ Confirm correct answers, then move forward
- ✅ Explain concepts BEFORE I apply them
- ✅ **Before EVERY task: first clarify what real-world problem we are solving and what pattern we are identifying**
- ✅ I write my own code and notes — no copy-paste (assistant must not write my notes)
- ✅ **Do not give examples until I ask for them**
- ❌ No ready-made queries or full solutions
- ❌ No information overload
- ✅ Wrong answers = learning opportunities
- ✅ Step back immediately if I say "don't help me"

---

## 8. SQL Bootcamp — Completed (Days 1–11)

| Day | Topic | Status |
|---|---|---|
| 1 | Aggregate functions — COUNT, SUM, AVG, MIN, MAX | ✅ |
| 2 | GROUP BY / ORDER BY / ROUND | ✅ |
| 3 | HAVING vs WHERE (filter groups vs filter rows) | ✅ |
| 4 | AND / OR / Parentheses | ✅ |
| 5 | CASE WHEN (categories + repeating logic in GROUP BY) | ✅ |
| 6 | INNER JOIN (ON clause, table aliases) | ✅ |
| 7 | LEFT / RIGHT / FULL JOIN (kept unmatched rows, IS NULL) | ✅ |
| 8 | NULL handling — ISNULL / COALESCE | ✅ |
| 9 | Subqueries Part 1 (single-value operators, IN) | ✅ |
| 10 | Subqueries Part 2 (scalar + correlated) | ✅ |
| 11 | Window functions — ROW_NUMBER, RANK, DENSE_RANK | ✅ |

Day-by-day detail lives in **SQL_Notes.md**.

---

## 9. Phase 1 — Project Queries (`EV-Battery-Health-queries.sql`)

| # | Business Question | Status |
|---|---|---|
| 1 | Battery chemistry performance (LFP vs NMC) | ✅ Complete |
| 2 | Country of origin health (FULL OUTER JOIN + ISNULL) | ✅ Complete |
| 3 | High-risk vehicles for maintenance | ✅ Complete — 605 rows |
| 4 | **Fast charging impact on battery health** | 🕒 **IN PROGRESS** |
| 5 | Temperature stress impact on battery health | ⬜ Pending |
| 6 | Charging cycle bands vs SoH | ⬜ Pending |
| 7 | Combined stress indicators / charging risk profile | ⬜ Pending |
| 8–12 | Final SQL analysis (defined when Day 13 closes) | ⬜ Pending |

**Day 12 completed:** 30-05-2026 | **Day 13 in progress:** Queries 4–7

### Query results so far
**Query 1 — Battery chemistry**

| Battery_Type | Vehicles | Avg SoH | Avg Resistance |
|---|---|---|---|
| NMC | 6021 | 95.05 | 0.0349 |
| LFP | 3980 | 96.95 | 0.0261 |

**Query 2 — Manufacturer country**

| Country | Vehicles | Avg SoH |
|---|---|---|
| China | 3980 | 96.95 |
| USA | 4017 | 95.05 |
| South Korea | 2003 | 95.04 |
| UNKNOWN | 1 | 95 |
| Japan | 0 | NULL |

**Query 3 — High-risk vehicles**
Rule: `(SoH_Percent < 90 AND Vehicle_Age_Months > 24) OR Battery_Status IN ('Critical','Warning')`
Result: **605 priority rows**, sorted by lowest health first.

---

## 10. Key Findings So Far

- LFP batteries hold health better than NMC (96.95 vs 95.05 avg SoH) with lower internal resistance
- NMC shows the highest average internal resistance (0.0349 Ω)
- Wuling Air EV has the highest average SoH of any model (96.99%)
- China is the highest-performing manufacturer country by average SoH (96.95%)
- Battery health distribution: 9,390 Healthy / 609 Warning / 1 Critical
- Usage levels: 5,003 Light / 3,375 Moderate / 1,622 Heavy — the only Critical battery sits in the Heavy segment
- 267 vehicles matched the "stressed" condition (high temperature + high discharge rate)
- 778 Tesla Model 3 vehicles are at risk (age > 60 months OR cycles > 800)
- 182 LFP vehicles tie at exactly 100% SoH — perfect demo of RANK() skipping 1 → 183 while DENSE_RANK() moves 1 → 2

---

## 11. Notes System

**File:** `SQL_Notes.md` — I write these manually, in my own words.

Template per day:

```markdown
## Day [X] — [Topic]
**Date:** DD-MM-YYYY

### 1. What I Learned Today
### 2. Key Rules / Points
### 3. Example Query I Wrote
### 4. What Confused Me
### 5. How It Got Cleared
### 6. Real-World Use In My Project
```

Completed: Day 1 → Day 12. Day 13 notes come after Queries 4–7.

---

## 12. File Map & GitHub Workflow

| File | Purpose |
|---|---|
| `README.md` | Public project overview + major milestones |
| `Project_Context.md` | This file — context, skill level, progress |
| `Project_Schedule.md` | Roadmap + daily schedule |
| `SQL_Notes.md` | Learning notes in my own words |
| `EV-Battery-Health-queries.sql` | Verified project queries |

### Update process after each completed topic
1. Review my answer or code
2. Confirm whether it is correct
3. Identify the exact files to update
4. Give the exact content to append or change
5. Always give the commit message
6. Tell the next single task
7. Wait for my confirmation before continuing

- **Commit message format:** `sql: query 4 - fast charging impact on SoH`
- GitHub shows **phases**, not day numbers. The day-wise syllabus stays out of the public README.
- **Folder rule:** create `notebooks/` when Python starts, `dashboard/` when Power BI starts,
  `reports/` for the business report, `screenshots/` for dashboard images. No premature restructuring.

### Next project (after this one)
`EV-Fleet-Operations-Analytics` — separate public repo, already scaffolded, with a Kanban board.
Its prerequisite card ("Complete prerequisite: EV Battery Health Analytics v1") stays in **Ready**
until this battery project v1 is genuinely complete.

---

## 13. Schedule Context

- **Daily slot:** 9:30 AM – 11:30 AM (Mon–Sat), Sundays off
- **Phase 1 ends at Day 14:** final SQL analysis + commit Phase 1 to GitHub
- **Day 15:** Phase 2 — Python EDA begins
- **Current catch-up plan:** complete Day 13 → Day 14 → Day 15 targets in order, while still
  finishing each day's queries **and** notes before moving to the next day
- Full dated roadmap lives in `Project_Schedule.md`

---

## 14. Next Task

👉 **Day 13 — Query 4: Fast Charging Impact on Battery Health**

- **Business problem:** Is frequent fast charging associated with lower battery SoH?
- **Pattern to identify:** compare average SoH across fast-charge usage bands
- **Output needed:** band label, vehicle count, average SoH (2 decimals)
- **Bands:** High `>= 0.6` | Moderate `>= 0.3 and < 0.6` | Low `< 0.3`
- **I write the query myself** — assistant reviews and interprets, no ready-made SQL.
