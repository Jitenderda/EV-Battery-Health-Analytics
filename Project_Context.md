# EV Battery Health Analytics — Project Context

## About Me
- Name: Jitender Maan
- GitHub: github.com/Jitenderda
- Daily project time: 1-2 hours

## Skill Level (Honest)
- Python: Beginner
- SQL: Beginner
- Power BI: Intermediate, needs depth

## Project Details
- **Title:** Predictive Battery Health Analytics for Electric Vehicles
- **Repo:** https://github.com/Jitenderda/EV-Battery-Health-Analytics-
- **Dataset:** EV Battery Degradation & Charge (Kaggle)
- **Rows:** 10,000
- **Columns:** 13
- **Target Variable:** SoH_Percent (regression, not classification)
- **Why regression:** Battery_Status is 99.96% "Healthy" — too imbalanced for classification

## Dataset Columns
- Vehicle_ID, Car_Model, Battery_Type, Battery_Capacity_kWh
- Vehicle_Age_Months, Total_Charging_Cycles
- Avg_Temperature_C, Fast_Charge_Ratio, Avg_Discharge_Rate_C
- Driving_Style, Internal_Resistance_Ohm
- SoH_Percent, Battery_Status

## 4-Phase Project Plan
1. **Phase 1: SQL** (current) — Database design + analytical queries in SSMS
2. **Phase 2: Python EDA** — Cleaning, visualization, feature importance
3. **Phase 3: Power BI** — 3-page dashboard with DAX measures
4. **Phase 4: Documentation** — GitHub + LinkedIn portfolio post

## Working Rules (NON-NEGOTIABLE)
- ✅ One question at a time, wait for my answer
- ✅ Confirm correct answers, then move forward
- ✅ I write my own code and notes (no copy-paste)
- ✅ No Google, no ChatGPT shortcuts
- ✅ Explain concepts BEFORE I apply them
- ✅ Wrong answers = learning opportunities
- ❌ No giving me ready-made solutions
- ❌ No information overload

## Tool Stack
- **Database:** Microsoft SQL Server (SSMS) — work PC
- **Notes:** sql_notes.md on GitHub (Markdown format)
- **Python:** Google Colab (when Phase 2 starts)
- **Dashboard:** Power BI (Phase 3)

## SQL Bootcamp Progress

### ✅ Day 1 — Aggregate Functions (COMPLETE)
- Learned: COUNT, SUM, AVG, MIN, MAX
- Key rule: Aggregates work on numbers only (except COUNT)
- Query practiced: SELECT COUNT(*) FROM ev_battery_data;
- Notes committed to sql_notes.md

### 🎯 Day 2 — GROUP BY (NEXT)
- Topic: How to slice data by category
- Example: Average SoH per Car_Model
- Status: Ready to start

## Pending Setup Tasks
- [ ] Confirm CSV imported successfully into SSMS
- [ ] Verify ev_battery_project database exists
- [ ] Test SELECT TOP 10 query in SSMS

## Today's Date Context
Day 1 was completed on 18-05-2026

Progress Report
Current Phase: Phase 1 (SQL)
Completed:
Day 1: Aggregate Functions (COUNT, AVG, SUM, etc.)
Day 2: GROUP BY, ORDER BY, and ROUND().
Database: EV_Projects
Table: ev_battery_data (10,000 rows verified).
Latest Insight: Identified NMC as the battery type with the highest internal resistance (~0.0349).
Next Topic: Day 3 — The HAVING Clause
Objective: Learning how to filter groups (not just rows).
Problem to solve: "How do I filter the results of an aggregate function?" (e.g., Show me only battery types where the average resistance is greater than X).
Why it matters: In your EV project, you’ll need this to isolate "problematic" car models or battery batches that fall below specific health thresholds.
See you tomorrow, Jitender. Great work today.
## Today's Date Context
Day 2 was completed on 19-05-2026

EV Battery Project — SQL Bootcamp Progress
User: Jitender Maan
Database: EV_Projects | Table: ev_battery_data (10,000 rows verified)
Phase: 1 (SQL in SSMS)

Completed Days:
Day 1: Aggregate Functions (COUNT, AVG, SUM, MIN, MAX)
Day 2: GROUP BY + ORDER BY + ROUND
Day 3: HAVING vs WHERE (filter rows vs filter groups)
Day 4: Logical Operators (AND, OR, Parentheses priority)
Key Insights Discovered:
Wuling Air EV has the highest average SoH (96.99%)
NMC battery type has the highest internal resistance (0.0349)
267 vehicles are in the "stressed" group (high temp + high discharge)
778 Tesla Model 3s are at risk (age > 60 months OR cycles > 800)
Next Topic: Day 5 — CASE WHEN
Creating custom categories (e.g., "Healthy", "Warning", "Critical")
Conditional logic in SELECT statements
Will feed directly into Power BI dashboard (Phase 3)
Working Rules (CRITICAL):
✅ One question at a time, wait for answer
✅ Explain concept BEFORE applying
❌ NEVER give ready-made queries or code
❌ No insights/comparisons unless asked
✅ User writes own code and notes
✅ Notes follow fixed template in sql_notes.md

## Today's Date Context
Day 3 & 4 was completed on 21-05-2026

EV Battery Project — SQL Bootcamp Progress
User: Jitender Maan
Database: EV_Projects | Table: ev_battery_data (10,000 rows verified)
Phase: 1 (SQL in SSMS) | Schedule: 9–11 AM, Mon–Sat

Completed Days:
Day 1: Aggregate Functions (COUNT, AVG, SUM, MIN, MAX)
Day 2: GROUP BY + ORDER BY + ROUND
Day 3: HAVING vs WHERE
Day 4: AND / OR / Parentheses
Day 5: CASE WHEN (Single + Combined categories)
Key Insights Discovered So Far:
Wuling Air EV = highest avg SoH (96.99%)
NMC battery = highest internal resistance (0.0349)
267 vehicles = stressed group (high temp + discharge)
778 Tesla Model 3s = at-risk (age OR cycles)
Battery Health distribution: 9,390 Healthy / 609 Warning / 1 Critical
Usage Level: 5,003 Light / 3,375 Moderate / 1,622 Heavy
Critical battery is in Heavy usage segment → confirms heavy usage = risk
Next Topic: Day 6 — JOINS (INNER JOIN)
Date: 23-05-2026 (Saturday)
Will introduce concept of joining tables
May need to create a second small lookup table for practice
Working Rules (CRITICAL — DO NOT BREAK):
✅ One question at a time, wait for answer
✅ Explain concept BEFORE applying
❌ NEVER give ready-made queries or full code
❌ No insights/comparisons unless asked
✅ User writes own code and notes
✅ Notes follow fixed template in sql_notes.md
✅ Step back immediately if user says "don't help me"

## Today's Date Context
Day 5 was completed on 22-05-2026

EV Battery Health Analytics — New Chat Summary
User: Jitender Maan
Repo: EV-Battery-Health-Analytics-
Current Phase: Phase 1 — SQL
Tool: SSMS
Database: EV_Projects
Main Table: dbo.ev_battery_data
Extra Table Created: dbo.car_info
Rows in main table: 10,000 verified

Project Context
Project Title: Predictive Battery Health Analytics for Electric Vehicles
Dataset: EV Battery Degradation & Charge (Kaggle)
Target Variable: SoH_Percent
Problem Type: Regression
Reason: Battery_Status is too imbalanced for classification
User Skill Level
Python: Beginner
SQL: Beginner
Power BI: Intermediate
Working Rules (IMPORTANT)
Ask one question at a time
Wait for my answer before moving forward
Explain concept before I apply it
I write my own code and notes
Do not give ready-made queries/full solutions
Do not overload
Wrong answers = learning opportunity
If I say “don’t help me,” step back immediately
SQL Bootcamp Progress
Day 1 — Aggregate Functions ✅
Learned:

COUNT, SUM, AVG, MIN, MAX
Day 2 — GROUP BY / ORDER BY / ROUND ✅
Learned:

Grouping by category
Sorting results
Rounding aggregated output
Day 3 — HAVING vs WHERE ✅
Learned:

WHERE filters rows
HAVING filters grouped/aggregated results
Day 4 — AND / OR / Parentheses ✅
Learned:

Multiple conditions
Parentheses change logic and results
Day 5 — CASE WHEN ✅
Learned:

Creating custom categories
Using multiple CASE blocks in one query
Repeating CASE logic in GROUP BY
Day 6 — INNER JOIN ✅
Learned:

Joining 2 tables on matching column
ON clause
Table aliases
Combined JOIN with WHERE + GROUP BY + ORDER BY
Tables Available
1. dbo.ev_battery_data
Columns include:

Vehicle_ID
Car_Model
Battery_Type
Battery_Capacity_kWh
Vehicle_Age_Months
Total_Charging_Cycles
Avg_Temperature_C
Fast_Charge_Ratio
Avg_Discharge_Rate_C
Driving_Style
Internal_Resistance_Ohm
SoH_Percent
Battery_Status
2. dbo.car_info
Created for JOIN practice:

Car_Model
Manufacturer_Country
Launch_Year
Inserted rows for:

Ford Mustang Mach-E
BYD Atto 3
Wuling Air EV
Hyundai Ioniq 5
Tesla Model 3
Key Findings So Far
Wuling Air EV has highest average SoH: 96.99
NMC has highest average internal resistance: 0.0349
267 vehicles matched stressed condition:
high temperature
high discharge rate
778 Tesla Model 3 matched age/cycle risk logic
Battery health categories:
Healthy: 9390
Warning: 609
Critical: 1
Usage levels:
Light: 5003
Moderate: 3375
Heavy: 1622
Critical + Heavy exists: 1
Average SoH by manufacturer country via JOIN:
China highest: 96.95
For models launched in 2020 or later, BYD Atto 3 had highest average SoH
Notes System
User maintains notes in sql_notes.md using this template:

Markdown

## Day [X] — [Topic]
**Date:** DD-MM-YYYY

### 1. What I Learned Today
### 2. Key Rules / Points
### 3. Example Query I Wrote
### 4. What Confused Me
### 5. How It Got Cleared
### 6. Real-World Use In My Project
Day 1 to Day 6 notes are completed.

Current Schedule Context
Working time for project: 9 AM – 11 AM
Working days: Monday to Saturday
Sunday off
Bootcamp schedule started from 18-05-2026
Next Topic
Day 7 — LEFT JOIN / RIGHT JOIN / FULL JOIN
Goal:

Understand what happens when rows do not match
Learn difference between INNER JOIN and other joins
## Today's Date Context
Day 6 was completed on 23-05-2026

EV Battery Health Analytics — New Chat Summary
User: Jitender Maan
Repo: EV-Battery-Health-Analytics-
Current Phase: Phase 1 — SQL
Tool: SSMS
Database: EV_Projects
Main Table: dbo.ev_battery_data
Extra Table Created: dbo.car_info
Rows in main table: 10,000 verified

Project Context
Project Title: Predictive Battery Health Analytics for Electric Vehicles
Dataset: EV Battery Degradation & Charge (Kaggle)
Target Variable: SoH_Percent
Problem Type: Regression (Battery_Status is too imbalanced for classification)
User Skill Level
Python: Beginner
SQL: Beginner
Power BI: Intermediate
Working Rules (IMPORTANT)
Ask one question at a time
Wait for my answer before moving forward
Explain concept before I apply it
I write my own code and notes (No copy-pasting code/notes from assistant)
Do not give ready-made queries/full solutions
Do not overload
Wrong answers = learning opportunity
If I say “don’t help me,” step back immediately
SQL Bootcamp Progress
Day 1 — Aggregate Functions ✅
COUNT, SUM, AVG, MIN, MAX
Day 2 — GROUP BY / ORDER BY / ROUND ✅
Grouping by category, sorting, and rounding results
Day 3 — HAVING vs WHERE ✅
WHERE filters rows, HAVING filters grouped/aggregated results
Day 4 — AND / OR / Parentheses ✅
Multiple conditions and how parentheses change logic and results
Day 5 — CASE WHEN ✅
Custom categories and repeating CASE logic in GROUP BY
Day 6 — INNER JOIN ✅
Joining 2 tables on a matching column, ON clause, and aliases
Day 7 — LEFT JOIN / RIGHT JOIN / FULL JOIN ✅ (Completed: 26-05-2026)
Kept unmatched rows, used IS NULL to find missing reference data (e.g., Kia EV6 has no lookup country, while Nissan Leaf and Rivian R1T are in lookup but not in test data).
Tables Available
dbo.ev_battery_data (10,000 rows. Columns: Vehicle_ID, Car_Model, Battery_Type, Battery_Capacity_kWh, Vehicle_Age_Months, Total_Charging_Cycles, Avg_Temperature_C, Fast_Charge_Ratio, Avg_Discharge_Rate_C, Driving_Style, Internal_Resistance_Ohm, SoH_Percent, Battery_Status)
dbo.car_info (Lookup table. Columns: Car_Model, Manufacturer_Country, Launch_Year. Contains: Ford Mustang Mach-E, BYD Atto 3, Wuling Air EV, Hyundai Ioniq 5, Tesla Model 3, Nissan Leaf, Rivian R1T)
Key Findings So Far
Wuling Air EV has highest average SoH: 96.99
NMC has highest average internal resistance: 0.0349
267 vehicles matched stressed condition: high temperature + high discharge rate
778 Tesla Model 3 matched age/cycle risk logic
Battery health categories: Healthy (9390), Warning (609), Critical (1)
Usage levels: Light (5003), Moderate (3375), Heavy (1622) (Critical + Heavy exists: 1)
Average SoH by manufacturer country via JOIN: China highest: 96.95
For models launched in 2020 or later, BYD Atto 3 had highest average SoH
Day 7 Joins Finding: Found that Kia EV6 exists in the battery data but has no matching row in car_info (returns NULL on join). Nissan Leaf and Rivian R1T exist in car_info but have no test vehicles in ev_battery_data.
Notes System
User maintains notes in sql_notes.md manually. Day 1 to Day 7 notes are completed.
Current Schedule Context
Working time for project: 9 AM – 11 AM (Monday to Saturday, Sunday off)
Bootcamp schedule started from 18-05-2026 (Today is Tuesday, 26-05-2026)
Next Topic
Day 8 — Handling NULL Values (ISNULL / COALESCE)
Goal: Learn how to clean up NULL values generated by outer joins and replace them with custom text like 'Unknown' or default numbers.
## Today's Date Context
Day 7 was completed on 25-05-2026

EV Battery Health Analytics — New Chat Summary
User: Jitender Maan
Repo: EV-Battery-Health-Analytics-
Current Phase: Phase 1 — SQL
Tool: SSMS
Database: EV_Projects
Main Table: dbo.ev_battery_data
Extra Table Created: dbo.car_info
Rows in main table: 10,000 verified

Project Context
Project Title: Predictive Battery Health Analytics for Electric Vehicles
Dataset: EV Battery Degradation & Charge (Kaggle)
Target Variable: SoH_Percent
Problem Type: Regression (Battery_Status is too imbalanced for classification)
User Skill Level
Python: Beginner
SQL: Beginner
Power BI: Intermediate
Working Rules (IMPORTANT)
Ask one question at a time
Wait for my answer before moving forward
Explain concept before I apply it
I write my own code and notes (No copy-pasting code/notes from assistant)
Do not give ready-made queries/full solutions
Do not overload
Wrong answers = learning opportunity
If I say “don’t help me,” step back immediately
SQL Bootcamp Progress
Day 1 — Aggregate Functions ✅ (COUNT, SUM, AVG, MIN, MAX)
Day 2 — GROUP BY / ORDER BY / ROUND ✅ (Grouping, sorting, and rounding results)
Day 3 — HAVING vs WHERE ✅ (WHERE filters rows, HAVING filters grouped/aggregated results)
Day 4 — AND / OR / Parentheses ✅ (Multiple conditions and logic precedence)
Day 5 — CASE WHEN ✅ (Custom categories and repeating CASE logic in GROUP BY)
Day 6 — INNER JOIN ✅ (Joining tables, ON clause, and aliases)
Day 7 — LEFT JOIN / RIGHT JOIN / FULL JOIN ✅ (Kept unmatched rows, used IS NULL to find missing reference data)
Day 8 — Handling NULL Values (ISNULL / COALESCE) ✅ (Completed: 26-05-2026)
Learned to replace NULLs in SELECT statements. Fixed space issues in ISNULL(). Mastered using COALESCE as ANSI-standard SQL to check multiple fallback columns and return the first non-NULL value.
Tables Available
dbo.ev_battery_data (10,000 rows. Columns: Vehicle_ID, Car_Model, Battery_Type, Battery_Capacity_kWh, Vehicle_Age_Months, Total_Charging_Cycles, Avg_Temperature_C, Fast_Charge_Ratio, Avg_Discharge_Rate_C, Driving_Style, Internal_Resistance_Ohm, SoH_Percent, Battery_Status)
dbo.car_info (Lookup table. Columns: Car_Model, Manufacturer_Country, Launch_Year. Contains: Ford Mustang Mach-E, BYD Atto 3, Wuling Air EV, Hyundai Ioniq 5, Tesla Model 3, Nissan Leaf, Rivian R1T)
Key Findings So Far
Wuling Air EV has highest average SoH: 96.99
NMC has highest average internal resistance: 0.0349
267 vehicles matched stressed condition: high temp + high discharge rate
778 Tesla Model 3 matched age/cycle risk logic
Battery health categories: Healthy (9390), Warning (609), Critical (1)
Usage levels: Light (5003), Moderate (3375), Heavy (1622) (Critical + Heavy exists: 1)
Average SoH by country via JOIN: China highest: 96.95
For models launched in 2020 or later, BYD Atto 3 had highest average SoH
Joins Finding: Found that Kia EV6 exists in the battery data but has no matching row in car_info (returns NULL on join). Nissan Leaf and Rivian R1T exist in car_info but have no test vehicles in ev_battery_data.
Cleaned up the FULL OUTER JOIN query so that all models are unified under a single Car_Model column, and any NULL country is replaced with 'Unknown'.
Notes System
User maintains notes in sql_notes.md manually. Day 1 to Day 8 notes are completed.
Revised SQL Bootcamp Schedule (Confirmed)
Day 8 (Tue, 26-05-2026) — Handling NULL Values (ISNULL / COALESCE) ✅
Day 9 (Wed, 27-05-2026) — Subqueries / Nested Queries (Practice + Notes) 🕒 Next Topic
Day 10 (Thu, 28-05-2026) — Window Functions (ROW_NUMBER, RANK) (Practice + Notes)
Day 11 (Fri, 29-05-2026) — Project Query 1–3 (Business questions on SoH)
Day 12 (Sat, 30-05-2026) — Project Query 4–7 (Charging behavior analysis)
Sunday (31-05-2026) — OFF 🛌
Day 13 (Mon, 01-06-2026) — Project Query 8–12 (Final SQL analysis & commit to GitHub)
Day 14 (Tue, 02-06-2026) — Phase 2 — Python EDA starts (All Python dates shifted 1 day)

## Today's Date Context
Day 8 was completed on 26-05-2026

EV Battery Health Analytics — New Chat Summary
User: Jitender Maan
Repo: EV-Battery-Health-Analytics-
Current Phase: Phase 1 — SQL
Tool: SSMS
Database: EV_Projects
Main Table: dbo.ev_battery_data
Extra Table Created: dbo.car_info
Rows in main table: 10,000 verified

Project Context
Project Title: Predictive Battery Health Analytics for Electric Vehicles
Dataset: EV Battery Degradation & Charge (Kaggle)
Target Variable: SoH_Percent
Problem Type: Regression (Battery_Status is too imbalanced for classification)
User Skill Level
Python: Beginner
SQL: Beginner
Power BI: Intermediate
Working Rules (IMPORTANT)
Ask one question at a time
Wait for my answer before moving forward
Explain concept before I apply it
I write my own code and notes (No copy-pasting code/notes from assistant)
Do not give ready-made queries/full solutions
Do not overload
Wrong answers = learning opportunity
If I say “don’t help me,” step back immediately
SQL Bootcamp Progress
Day 1 — Aggregate Functions ✅ (COUNT, SUM, AVG, MIN, MAX)
Day 2 — GROUP BY / ORDER BY / ROUND ✅ (Grouping, sorting, and rounding results)
Day 3 — HAVING vs WHERE ✅ (WHERE filters rows, HAVING filters grouped results)
Day 4 — AND / OR / Parentheses ✅ (Multiple conditions and logic precedence)
Day 5 — CASE WHEN ✅ (Custom categories and repeating CASE logic in GROUP BY)
Day 6 — INNER JOIN ✅ (Joining tables, ON clause, and aliases)
Day 7 — LEFT JOIN / RIGHT JOIN / FULL JOIN ✅ (Kept unmatched rows, used IS NULL to find missing reference data)
Day 8 — Handling NULL Values (ISNULL / COALESCE) ✅ (Replaced NULLs in SELECT statements, fixed space issues in ISNULL(), mastered COALESCE as ANSI-standard SQL fallback)
Day 9 — Subqueries (Part 1) ✅ (Completed: 27-05-2026)
Learned the core concept of nested queries (inner vs. outer). Mastered Single-Value subqueries (using standard operators like >) and Multi-Value subqueries (using IN). Practiced using subqueries as an alternative to JOIN for filtering main table data based on another table's conditions.
Tables Available
dbo.ev_battery_data (10,000 rows. Columns: Vehicle_ID, Car_Model, Battery_Type, Battery_Capacity_kWh, Vehicle_Age_Months, Total_Charging_Cycles, Avg_Temperature_C, Fast_Charge_Ratio, Avg_Discharge_Rate_C, Driving_Style, Internal_Resistance_Ohm, SoH_Percent, Battery_Status)
dbo.car_info (Lookup table. Columns: Car_Model, Manufacturer_Country, Launch_Year)
Key Findings So Far
Wuling Air EV has highest average SoH: 96.99
NMC has highest average internal resistance: 0.0349
267 vehicles matched stressed condition: high temp + high discharge rate
778 Tesla Model 3 matched age/cycle risk logic
Battery health categories: Healthy (9390), Warning (609), Critical (1)
Average SoH by country via JOIN: China highest: 96.95
Day 9 Subqueries Finding: Successfully queried all USA manufactured vehicles (Tesla Model 3 and Ford Mustang Mach-E) using a clean WHERE Car_Model IN (SELECT ...) subquery, returning 4,017 matching rows.
Notes System
User maintains notes in sql_notes.md manually. Day 1 to Day 9 notes are completed.
Revised SQL Bootcamp Schedule (Confirmed)
Day 9 (Wed, 27-05-2026) — Subqueries (Part 1) ✅
Day 10 (Thu, 28-05-2026) — Subqueries (Part 2) 🕒 Next Topic (Practice advanced nested queries)
Day 11 (Fri, 29-05-2026) — Window Functions (ROW_NUMBER, RANK) (Practice + Notes)
Day 12 (Sat, 30-05-2026) — Project Query 1–3 (Business questions on SoH)
Sunday (31-05-2026) — OFF 🛌
Day 13 (Mon, 01-06-2026) — Project Query 4–7 (Charging behavior analysis)
Day 14 (Tue, 02-06-2026) — Project Query 8–12 & Commit Phase 1 to GitHub
## Today's Date Context
Day 9 was completed on 27-05-2026

EV Battery Health Analytics — New Chat Summary
User: Jitender Maan
Repo: EV-Battery-Health-Analytics-
Current Phase: Phase 1 — SQL
Tool: SSMS
Database: EV_Projects
Main Table: dbo.ev_battery_data
Extra Table Created: dbo.car_info
Rows in main table: 10,000 verified

Project Context
Project Title: Predictive Battery Health Analytics for Electric Vehicles
Dataset: EV Battery Degradation & Charge (Kaggle)
Target Variable: SoH_Percent
Problem Type: Regression (Battery_Status is too imbalanced for classification)
User Skill Level
Python: Beginner
SQL: Beginner
Power BI: Intermediate
Working Rules (IMPORTANT)
Ask one question at a time
Wait for my answer before moving forward
Explain concept before I apply it
I write my own code and notes (No copy-pasting code/notes from assistant)
Do not give ready-made queries/full solutions
Do not overload
Wrong answers = learning opportunity
If I say “don’t help me,” step back immediately
SQL Bootcamp Progress
Day 1 — Aggregate Functions ✅ (COUNT, SUM, AVG, MIN, MAX)
Day 2 — GROUP BY / ORDER BY / ROUND ✅ (Grouping, sorting, and rounding results)
Day 3 — HAVING vs WHERE ✅ (WHERE filters rows, HAVING filters grouped results)
Day 4 — AND / OR / Parentheses ✅ (Multiple conditions and logic precedence)
Day 5 — CASE WHEN ✅ (Custom categories and repeating CASE logic in GROUP BY)
Day 6 — INNER JOIN ✅ (Joining tables, ON clause, and aliases)
Day 7 — LEFT JOIN / RIGHT JOIN / FULL JOIN ✅ (Kept unmatched rows, used IS NULL to find missing reference data)
Day 8 — Handling NULL Values (ISNULL / COALESCE) ✅ (Replaced NULLs in SELECT statements, fixed space issues in ISNULL(), mastered COALESCE as ANSI-standard SQL fallback)
Day 9 — Subqueries (Part 1) ✅ (Learned the core concept of nested queries. Mastered Single-Value subqueries and Multi-Value subqueries using IN as a JOIN alternative)
Day 10 — Subqueries (Part 2) ✅ (Completed: 28-05-2026)
Learned to place subqueries in the SELECT clause (Scalar Subqueries) to repeat values side-by-side with individual rows. Mastered Correlated Subqueries inside the WHERE clause, running calculations dynamically based on the active row of the outer table using table instances (t1 and t2).
Tables Available
dbo.ev_battery_data (10,000 rows. Columns: Vehicle_ID, Car_Model, Battery_Type, Battery_Capacity_kWh, Vehicle_Age_Months, Total_Charging_Cycles, Avg_Temperature_C, Fast_Charge_Ratio, Avg_Discharge_Rate_C, Driving_Style, Internal_Resistance_Ohm, SoH_Percent, Battery_Status)
dbo.car_info (Lookup table. Columns: Car_Model, Manufacturer_Country, Launch_Year)
Key Findings So Far
Wuling Air EV has highest average SoH: 96.99
NMC has highest average internal resistance: 0.0349
267 vehicles matched stressed condition: high temp + high discharge rate
778 Tesla Model 3 matched age/cycle risk logic
Battery health categories: Healthy (9390), Warning (609), Critical (1)
Average SoH by country via JOIN: China highest: 96.95
Day 10 Subqueries Finding: Successfully used a correlated subquery to find all 4,314 vehicles with an Internal_Resistance_Ohm greater than the average of their own specific Battery_Type.
Notes System
User maintains notes in sql_notes.md manually. Day 1 to Day 10 notes are completed.
Revised SQL Bootcamp Schedule (Confirmed)
Day 10 (Thu, 28-05-2026) — Subqueries (Part 2) ✅
Day 11 (Fri, 29-05-2026) — Window Functions (ROW_NUMBER, RANK) (Practice + Notes) 🕒 Next Topic
Day 12 (Sat, 30-05-2026) — Project Query 1–3 (Business questions on SoH)
Sunday (31-05-2026) — OFF 🛌
Day 13 (Mon, 01-06-2026) — Project Query 4–7 (Charging behavior analysis)
Day 14 (Tue, 02-06-2026) — Project Query 8–12 & Commit Phase 1 to GitHub
## Today's Date Context
Day 10 was completed on 28-05-2026

EV Battery Health Analytics — New Chat Summary
User: Jitender Maan
Repo: EV-Battery-Health-Analytics-
Current Phase: Phase 1 — SQL
Tool: SSMS
Database: EV_Projects
Main Table: dbo.ev_battery_data
Extra Table Created: dbo.car_info
Rows in main table: 10,000 verified

Project Context
Project Title: Predictive Battery Health Analytics for Electric Vehicles
Dataset: EV Battery Degradation & Charge (Kaggle)
Target Variable: SoH_Percent
Problem Type: Regression (Battery_Status is too imbalanced for classification)
User Skill Level
Python: Beginner
SQL: Beginner
Power BI: Intermediate
Working Rules (IMPORTANT)
Ask one question at a time
Wait for my answer before moving forward
Explain concept before I apply it
I write my own code and notes (No copy-pasting code/notes from assistant)
Do not give ready-made queries/full solutions
Do not overload
Wrong answers = learning opportunity
If I say “don’t help me,” step back immediately
SQL Bootcamp Progress
Day 1 — Aggregate Functions ✅ (COUNT, SUM, AVG, MIN, MAX)
Day 2 — GROUP BY / ORDER BY / ROUND ✅ (Grouping, sorting, and rounding results)
Day 3 — HAVING vs WHERE ✅ (WHERE filters rows, HAVING filters grouped results)
Day 4 — AND / OR / Parentheses ✅ (Multiple conditions and logic precedence)
Day 5 — CASE WHEN ✅ (Custom categories and repeating CASE logic in GROUP BY)
Day 6 — INNER JOIN ✅ (Joining tables, ON clause, and aliases)
Day 7 — LEFT JOIN / RIGHT JOIN / FULL JOIN ✅ (Kept unmatched rows, used IS NULL to find missing reference data)
Day 8 — Handling NULL Values (ISNULL / COALESCE) ✅ (Replaced NULLs in SELECT statements, fixed space issues in ISNULL(), mastered COALESCE fallback)
Day 9 — Subqueries (Part 1) ✅ (Learned core nested queries, Single-Value comparison, and Multi-Value IN filtering)
Day 10 — Subqueries (Part 2) ✅ (Scalar subqueries in SELECT and Correlated Subqueries inside the WHERE clause using table instances)
Day 11 — Window Functions (ROW_NUMBER, RANK, DENSE_RANK) ✅ (Completed: 29-05-2026)
Learned to apply ranking window functions inside the SELECT clause using OVER(), PARTITION BY, and ORDER BY. Discovered how ROW_NUMBER ignores ties, RANK allows ties and skips ranks (e.g., skipping from rank 1 to 183 due to 182 tied 100% SoH vehicles), and DENSE_RANK allows ties without skipping.
Tables Available
dbo.ev_battery_data (10,000 rows)
dbo.car_info (Lookup table)
Key Findings So Far
Wuling Air EV has highest average SoH: 96.99
NMC has highest average internal resistance: 0.0349
267 vehicles matched stressed condition: high temp + high discharge rate
778 Tesla Model 3 matched age/cycle risk logic
Average SoH by country via JOIN: China highest: 96.95
Day 11 Window Functions Finding: Discovered there are exactly 182 vehicles in the database with a perfect SoH_Percent of 100% in the LFP partition, creating a perfect real-world demonstration of RANK() skipping from 1 straight to 183, while DENSE_RANK() moved to 2.
Notes System
User maintains notes in sql_notes.md manually. Day 1 to Day 11 notes are completed.
Master Schedule (Days 12–14)
Day 12 — 30-05-2026 (Sat) | 9:30–10:30 AM: Business questions on SoH | 10:30–11:30 AM: Write to project_queries.sql 🕒 Next Topic
— — 31-05-2026 (Sun) | 🛌 OFF — Rest Day
Day 13 — 01-06-2026 (Mon) | 9:30–10:30 AM: Charging behavior analysis | 10:30–11:30 AM: Write to project_queries.sql
Day 14 — 02-06-2026 (Tue) | 9:30–10:30 AM: Final SQL analysis | 10:30–11:30 AM: Commit Phase 1 to GitHub
## Today's Date Context
Day 11 was completed on 29-05-2026

EV Battery Health Analytics — New Chat Summary
User: Jitender Maan
Repo: EV-Battery-Health-Analytics-
Current Phase: Phase 1 — SQL
Tool: SSMS
Database: EV_Projects
Main Table: dbo.ev_battery_data
Extra Table Created: dbo.car_info
Rows in main table: 10,000 verified

Project Context
Project Title: Predictive Battery Health Analytics for Electric Vehicles
Dataset: EV Battery Degradation & Charge (Kaggle)
Target Variable: SoH_Percent
Problem Type: Regression (Battery_Status is too imbalanced for classification)
User Skill Level
Python: Beginner
SQL: Beginner
Power BI: Intermediate
Working Rules (IMPORTANT)
Ask one question at a time
Wait for my answer before moving forward
Explain concept before I apply it
I write my own code and notes (No copy-pasting code/notes from assistant)
Do not give ready-made queries/full solutions
Do not overload
Wrong answers = learning opportunity
If I say “don’t help me,” step back immediately
SQL Bootcamp Progress
Day 1 — Day 11: Core SQL foundations (Aggregates, Grouping, Having, Joins, NULL handling with ISNULL/COALESCE, Subqueries, and Window Functions like ROW_NUMBER/RANK/DENSE_RANK) completed and documented in sql_notes.md.
Day 12 — Project Queries 1–3 ✅ (Completed: 30-05-2026)
Created the main SQL project script: EV-Battery-Health-queries.sql with professional GitHub headers and batch separators (USE/GO).
Query 1 (Battery Chemistry Analysis): Grouped by Battery_Type to compare LFP and NMC average, min, and max SoH, alongside average internal resistance. NMC showed higher average resistance (0.0349 Ohms) and lower average SoH (95.05%) compared to LFP (0.0261 resistance, 96.95% SoH).
Query 2 (Country Origin Analysis): Performed a FULL OUTER JOIN to group by Manufacturer_Country. Successfully utilized ISNULL to show 'UNKNOWN' for missing lookup models (Kia EV6) and preserved unmatched lookup records like Japan (Nissan Leaf with 0 test vehicles). China has highest average SoH (96.95%).
Query 3 (High-Risk Vehicle Inspection): Combined conditions using explicit OR and IN logic with parentheses: (SoH_Percent < 90 AND Vehicle_Age_Months > 24) OR (Battery_Status IN ('Critical', 'Warning')). Returned exactly 605 priority inspection rows sorted by lowest health first.
Tables Available
dbo.ev_battery_data (10,000 rows)
dbo.car_info (Lookup table)
Notes System
User maintains notes in sql_notes.md manually. Day 1 to Day 11 notes are completed. Day 12 project queries are saved in EV-Battery-Health-queries.sql.
Master Schedule (Days 13–15)
— — 31-05-2026 (Sun) | 🛌 OFF — Rest Day
Day 13 — 01-06-2026 (Mon) | 9:30–10:30 AM: Charging behavior analysis | 10:30–11:30 AM: Write to EV-Battery-Health-queries.sql (Queries 4–7) 🕒 Next Topic
Day 14 — 02-06-2026 (Tue) | 9:30–10:30 AM: Final SQL analysis (Queries 8–12) | 10:30–11:30 AM: Commit Phase 1 to GitHub
Day 15 — 03-06-2026 (Wed) | 9:30 AM: Phase 2 — Python EDA starts!
## Today's Date Context
Day 12 was completed on 30-05-2026
