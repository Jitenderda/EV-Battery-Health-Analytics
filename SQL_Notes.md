# SQL Learning Notes — EV Battery Project

---
## Day 1 — Aggregate Functions

**Date:** 19-05-2026

### 1. What I Learned Today
Today, I learned about Aggregate functions in SQL
I learned Average which finds average, SUM do the addition, Count just count the rows, MIN gets minimum value, MAX finds maximum value

### 2. Key Rules / Points
- Rule 1 Aggregate Functions works with Numbers
- Rule 2 Except, Count which count total no. of Rows
- Rule 3 Avg(Ram, Raman, Deeraj) gives error due to the concept of aggregate functions which is stated as they only calculate numbers not text.

### 3. Example Query I Wrote
```sql
Select Count(*) from ev_battery_Data;
```
Result: 10000

### 4. What Confused Me
First of all I'm a bit confused about aggregate functions but after a bit learning, i clear all my doubts 

### 5. How It Got Cleared
Let's take an example of average aggregate function, it works only on nos. but i found text out there, when I learned again then i find aggregate functions only works on numbers not on text.

### 6. Real-World Use In My Project
I use Count(*) to count total rows to confirm that the data imported properly.
___________________________________________________________________

## Day 2 — Aggregation and Sorting
**Date:** 19-02-2026

### 1. What I Learned Today
Today i learned Group By & Order By Clauses, Also pactice on AVG, Count Functions.
Group By is used to Group certain column for clearer picture.
Order By is used to order the result in ascending & descending order.
Also learned about Round Function which round off to n number of decimals 

### 2. Key Rules / Points
- Use DESC for descending & ASC for ascending durng filtering using ORDER BY.
- Use Round function with aggrigate functions to get a good result.
- First use Group By then use Order By in the Query

### 3. Example Query I Wrote
```sql
SELECT Battery_Type, ROUND(AVG(Internal_Resistance_Ohm), 4)
FROM dbo.ev_battery_data
GROUP BY Battery_Type
ORDER BY ROUND(AVG(Internal_Resistance_Ohm), 4) DESC;
```
Result: NMC	0.0349 
        LFP	0.0261

### 4. What Confused Me
   I confused in ordering result by average of SoH_Percent Column.
### 5. How It Got Cleared
   I'll try to write te query & got 1-2 errors, then got the understanding how to use it. & Result Confirmed all.  
### 6. Real-World Use In My Project
   Round Function used with Internal_Resistance_Ohm Column in this project.

___________________________________________________________________

## Day 3 — HAVING v/s WHERE

**Date:** 20-05-2026

### 1. What I Learned Today
Today I Learned "Where to use Having & Where in SQL Queries & There Sequence"
Both used for filtering the output.

### 2. Key Rules / Points
- Where works before group by to filter column data
- Having works on group set cuz it wait for grouping then filtering data 
- Where used before group by & having used after groupby

### 3. Example Query I Wrote
```sql
USE EV_Projects;
SELECT Car_Model, ROUND(AVG(SoH_Percent),2)
FROM dbo.ev_battery_data
WHERE Fast_Charge_Ratio > 0.5
GROUP BY Car_Model
Having AVG(SoH_Percent) < 95;
```
Result:
Ford Mustang Mach-E	94.71
Hyundai Ioniq 5	94.5
Tesla Model 3	94.52

### 4. What Confused Me
       I Confused here with having sequence
### 5. How It Got Cleared
       When i try to put having below groupby & got result then confusion cleared
### 6. Real-World Use In My Project
       When ever we group our result in query & want to filter that we use having in the project
___________________________________________________________________

## Day 4 — Operators(AND / OR)

**Date:** 21-05-2026

### 1. What I Learned Today
Today I Learned about operators
First I learn about AND operator which give result when both conditions are true
Then learnt about OR Operater which give result when one of the condition is True.
Lastly learned about mixed operation like we use AND, OR & Parentheses in a single query

### 2. Key Rules / Points
- For AND Operator Both conditions Should be True
- For OR Operator one of the condition to be True
- Using Both Operators in a Query, Parentheses makes a real difference in result

### 3. Example Query I Wrote
```sql
SELECT COUNT(Vehicle_ID) AS V_ID
FROM dbo.ev_battery_data
WHERE Car_Model = 'Tesla Model 3' AND (Vehicle_Age_Months > 60 OR Total_Charging_Cycles > 800);
```
Result: 778

### 4. What Confused Me
       Confused in using both operator in a single query
### 5. How It Got Cleared
       Using Parentheses 
### 6. Real-World Use In My Project
       When ever we have more than one condition we use operators in the project     
   
___________________________________________________________________

## Day 5 — CASE WHEN

**Date:** 22-05-2026

### 1. What I Learned Today
Today I learned a very intersting topic which is called CASE WHEN Switch Statement.
This Case When statement is helpful when you have more than one Statement

### 2. Key Rules / Points
- Statement Starts With CASE Then Conditions & Then Ends with END Statement
- We also can use CASE WHEN Switch Statements more than one time.
- WE Use Aggregate Functions after CASE WHEN END

### 3. Example Query I Wrote
```sql
SELECT
CASE 
	WHEN SoH_Percent > 90 THEN 'Healthy'
	WHEN SoH_Percent > 75 THEN 'Warning'
	ELSE 'Critical' 
END
AS Battery_Health_Status,
CASE 
	WHEN Total_Charging_Cycles > 800 THEN 'Heavy'
	WHEN Total_Charging_Cycles > 400 THEN 'Moderate'
	ELSE 'Light' 
END
AS Total_Charging_Cycles,
COUNT(*) AS Total_Vehicles
FROM dbo.ev_battery_data
GROUP BY CASE 
	WHEN SoH_Percent > 90 THEN 'Healthy'
	WHEN SoH_Percent > 75 THEN 'Warning'
	ELSE 'Critical' 
END,
CASE 
	WHEN Total_Charging_Cycles > 800 THEN 'Heavy'
	WHEN Total_Charging_Cycles > 400 THEN 'Moderate'
	ELSE 'Light' 
END;

```
Result:
Healthy	Moderate	3299
Healthy	Heavy	1088
Warning	Moderate	76
Healthy	Light	5003
Critical	Heavy	1
Warning	Heavy	533

### 4. What Confused Me
       I try 2 CASE WHEN in Same Query without understanding the logic, that Confuse me a a lot.
### 5. How It Got Cleared
       First i Understand how to use more than 1 CASE WHEN, Then i Feel Confident & the Results Cleared all the Confussion.
### 6. Real-World Use In My Project
       When using more than one condition to get the desired result like the query i used today.

___________________________________________________________________

## Day 6 — INNER JOIN

**Date:** 23-05-2026

### 1. What I Learned Today
Today I learned INNER JOIN which join two tables in a manner that we got output from both the tables, But there is a condition in INNER JOIN that it shows rows from table 2 only when matched with table 1. 

### 2. Key Rules / Points
- Join 2 Tables
- Shows matching data
- USE ON for defining commom column from both the Table

### 3. Example Query I Wrote
```sql
SELECT  t1.Car_Model,
ROUND(AVG(t1.SoH_Percent), 2) AS Avg_SoH_Percent
FROM dbo.ev_battery_data AS t1
INNER JOIN dbo.car_info AS t2
ON t1.Car_Model = t2.Car_Model
WHERE t2.Launch_Year >= 2020
GROUP BY t1.Car_Model
ORDER BY Avg_SoH_Percent DESC;
```
Result:
		BYD Atto 3	96.92
		Ford Mustang Mach-E	95.07
		Hyundai Ioniq 5	95.04

### 4. What Confused Me
       I Confused when I run Query & a column gives error.
### 5. How It Got Cleared
       Then I realize I forget to include Group By Clause, then I GROUP BY that Column & the error & my confussion cleared.  
### 6. Real-World Use In My Project
       When ever working with two Tables to get the desired Results from them.

___________________________________________________________________

## Day 7 — LEFT, RIGHT & FULL JOIN

**Date:** 25-05-2026

### 1. What I Learned Today
Today i learnt about joins.
First i learn about left join which gives you all rows from left table & matching rows from Right table.
Left join also shows null for values not matching.
Then i learn about Right join which gives you all rows from Right table & matching rows from Left table.
Right join also shows null for values not matching.
Lastly i learn about FULL outer join which gives you all rows from Both Right & Left Table.
Shows null for values not matching.

### 2. Key Rules / Points
- LEFT join shows Null for not matching values from right table. 
- RIGHT join shows Null for not matching values from left table.
- FULL outer Join Shows all values from both table. shows null for not matching values. 

### 3. Example Query I Wrote
```sql
SELECT DISTINCT
t1.Car_Model,
t2.Car_Model,
t2.Manufacturer_Country
FROM dbo.ev_battery_data AS t1
FULL OUTER JOIN dbo.car_info AS t2
ON t1.Car_Model = t2.Car_Model;

```
Result:
NULL	Nissan Leaf	Japan
NULL	Rivian R1T	USA
BYD Atto 3	BYD Atto 3	China
Ford Mustang Mach-E	Ford Mustang Mach-E	USA
Hyundai Ioniq 5	Hyundai Ioniq 5	South Korea
Kia EV6	NULL	NULL
Tesla Model 3	Tesla Model 3	USA
Wuling Air EV	Wuling Air EV	China

### 4. What Confused Me
	   NONE
### 5. How It Got Cleared
	   N/A	
### 6. Real-World Use In My Project
	   When Eevr working with more then one table & want to find missing values we use join.
___________________________________________________________________

## Day 8 — NULL Values (ISNULL / COALESCE) 

**Date:** 26-05-2026

### 1. What I Learned Today
Today i learned how to handle NULL values.
ISNULL works with column having null & a new value on the place of null.
COALESCE works same but it is a ANSI-standard SQL. works fine when you migrate your project from SSMS to another database engine (like PostgreSQL, Snowflake, or BigQuery)

### 2. Key Rules / Points
- When using IS NULL function in select clause must be one word with no space like ISNULL.
- COALESCE is ANSI Standard SQL easy to migrate project to another DB engine.  
- COALESCE look at more that 2 columns & return first non null value & finds from left to right.

### 3. Example Query I Wrote
```sql
SELECT DISTINCT
COALESCE(t1.Car_Model, t2.Car_Model) AS Car_Model,
COALESCE(t2.Manufacturer_Country, 'Unknown') AS Manufacturer_Country
FROM dbo.ev_battery_data AS t1
FULL OUTER JOIN dbo.car_info AS t2
ON t1.Car_Model = t2.Car_Model;
```
Result:
		Nissan Leaf	Japan
		Hyundai Ioniq 5	South Korea
		Wuling Air EV	China
		Rivian R1T	USA
		BYD Atto 3	China
		Tesla Model 3	USA
		Ford Mustang Mach-E	USA
		Kia EV6	Unknown

### 4. What Confused Me
   	I confused using IS NULL in select clause
### 5. How It Got Cleared
   	i forgot using ISNULL without space as a single word, then i remove space & result of query cleared the confussion.
### 6. Real-World Use In My Project
   	We Use ISNULL & COALESCE while handling null values in sql queries in our project.
___________________________________________________________________

## Day 9 — Subqueries (Part 1)

**Date:** 27-05-2026

### 1. What I Learned Today
Today I Learned about Subquery which is Query in Query
like we filter our result of a query by writing another query within that.

### 2. Key Rules / Points
- we use operators while using subqueries if the result is a single value.
- USE IN when subquery result in multiple values.
- Subquery is good option for joins.
### 3. Example Query I Wrote
```sql
SELECT TOP 10
Vehicle_ID, Car_Model, SoH_Percent 
from dbo.ev_battery_data
where Car_Model IN (SELECT Car_Model FROM dbo.car_info WHERE Manufacturer_Country = 'USA');
```
Result: 
		001f6ebb	Tesla Model 3	100
		003b6c06	Tesla Model 3	96.3300018310547
		005b98a6	Ford Mustang Mach-E	97.75
		006a15a1	Ford Mustang Mach-E	99.0500030517578
		007cc32f	Tesla Model 3	88.2600021362305
		009ed9aa	Ford Mustang Mach-E	97.4400024414063
		00a093a9	Ford Mustang Mach-E	97.2699966430664
		00a50f31	Ford Mustang Mach-E	99.6900024414063
		00a78e6e	Ford Mustang Mach-E	97.6999969482422
		00a83afc	Ford Mustang Mach-E	90.8499984741211

### 4. What Confused Me
	   No Confussion today
### 5. How It Got Cleared
	   N/A	
### 6. Real-World Use In My Project
	   When use two or more tables & want to filter result accourding to another column condition we use subqueries.
___________________________________________________________________

## Day 10 — Subqueries (Part 2)

**Date:** 28-05-2026

### 1. What I Learned Today
Today i learned about a next level of subqueries.
I learned how to use subqueries in to select clause.
one more thing i learned here how to use two instances of same table.

### 2. Key Rules / Points
- USE subqueries in SELECT Clause by using Where Clause
- We can use 2 instances of same table while using subquery, one for main 
- When subquery return multiple value then sql server threw error, reason behind it is sql cofused which one he use.  
### 3. Example Query I Wrote
```sql
SELECT TOP 10
Vehicle_ID, Battery_Type, Internal_Resistance_Ohm
FROM dbo.ev_battery_data as t1
WHERE Internal_Resistance_Ohm > (SELECT AVG(Internal_Resistance_Ohm) FROM dbo.ev_battery_data as t2 WHERE t1.Battery_Type = t2.Battery_Type);
```
Result:
		003cf549	NMC	0.035300001502037
		003dd4ca	NMC	0.0366000011563301
		007cc32f	NMC	0.0548000000417233
		00a83afc	NMC	0.0472000017762184
		00b1a4ab	NMC	0.0575999990105629
		00ea140c	NMC	0.0390999987721443
		00ea4f2f	NMC	0.0390000008046627
		00fd9ae7	NMC	0.0428999997675419
		010b09fe	NMC	0.0595000013709068
		014a258c	NMC	0.0359999984502792

### 4. What Confused Me
	   Correlate the two tables inside the subquery's WHERE clause on the matching Battery_Type column.
### 6. How It Got Cleared
	   Explore the corelation between tables inside subquery & i understand how to use that using instances. 	
### 7. Real-World Use In My Project
	   When ever we want to get the column data & their avg or other aggrigate functions values shown in the result side by side we use subquery.
___________________________________________________________________

## Day 11 — Window Functions (ROW_NUMBER, RANK, DENSE_RANK)

**Date:** 29-05-2026

### 1. What I Learned Today
Today i learned about windows functions Like ROW_NUMBER, RANK & DENSE_RANK
ROW_NUMBER Assign Unique Sequential values & ignore ties.
RANK Assign a ranking to each row ignore ties, gives same rank to tied rows.
DENSE_RANK Same as rank it gives same rank to tied row same rank. does not skip any numbers.
### 2. Key Rules / Points
- RANK asigns different numbers for tied rows
- The only diffference between RANK & DANSE_RANK is RANK assign same rank to tied rows & skip rank for next, but DANSE_RANK assign same rank to tied rows but not skip rank.
- PARTITION BY & ORDER BY used inside subqueries to group & arrange respectivly.  
### 3. Example Query I Wrote
```sql
SELECT Vehicle_ID, Battery_Type, SoH_Percent,
RANK() OVER (PARTITION BY Battery_Type ORDER BY SoH_Percent DESC) AS SoH_Rank,
DENSE_RANK() OVER (PARTITION BY Battery_Type ORDER BY SoH_Percent DESC) AS SoH_Dense_Rank
FROM dbo.ev_battery_data;
```
Result:
		010f3c9c	LFP	100	1	1
		03c9d3b3	LFP	100	1	1
		03dae574	LFP	100	1	1
		0503f12d	LFP	100	1	1
		0865a965	LFP	100	1	1
		098af993	LFP	100	1	1
		09f3058e	LFP	100	1	1
		0ce9bca1	LFP	100	1	1
		0dc4373b	LFP	100	1	1
		0fc77b1d	LFP	100	1	1

### 4. What Confused Me
	   Where to use window function like RANK in query, before FROM or After From.
### 6. How It Got Cleared
	   I Explore a bit & identify it works when used above FROM Clause. as query runs perfectly the confussion cleared. 	
### 7. Real-World Use In My Project
	   We will use windows function when ever need to rank the result with RANK OR ROW_NUMBER OR DENSE_RANK
___________________________________________________________________
	   
## Day 12 — Business questions on SoH

**Date:** 29-05-2026

### 1. What I Do Today
	   Today i Started phase 1 of the project queries.
	   I work on 3 business queries on SOH(State of Health)
	   In Query 1 I use  aggregate functions like COUNT, AVG, MIN, MAX. & group by to get categorised results by battery type which LFP & NMC
	   In Query 2 I use joins & ISNULL, Group by & order by use get the result grouped by Manufacturer_Country. 
	   IN Query 3 I use logical filtering using where & order by to get result according to our filter like we use in where clause.
### 2. Key Rules / Points
	-  Using USE EV_Projects; and GO at the top of the script so it runs on the correct database automatically.
	-  Adding clean header comments to explain what each business query does. 
	-  The literal rule of SQL logic: having to write out the column name on both sides of an OR operator (like Battery_Status IN ('Critical', 'Warning') and Battery_Status = 'Critical' OR Battery_Status = 'Warning').
	
### 3. Example Query I Wrote
```sql
SELECT
ISNULL(t2.Manufacturer_Country, 'UNKNOWN') AS Manufacturer_Country,
COUNT(t1.Vehicle_ID) AS Vehicle_Count,
ROUND(AVG(t1.SoH_Percent), 2) AS Avg_SoH_Percent
FROM dbo.ev_battery_data t1
FULL OUTER JOIN dbo.car_info AS t2
ON t1.Car_Model = t2.Car_Model
GROUP BY Manufacturer_Country
ORDER BY Avg_SoH_Percent DESC;
```
Result:
		China	3980	96.95
USA	4017	95.05
South Korea	2003	95.04
UNKNOWN	1	95
Japan	0	NULL

### 4. What Confused Me
	   WHERE (SoH_Percent < 90 AND Vehicle_Age_Months > 24) OR (Battery_Status = 'Critical' or 'Warning')
	   I Confused in whare clause where check for battery status is it Critical or Warning, I wrote the query wrong way, that result in a confussion
### 6. How It Got Cleared
	   WHERE (SoH_Percent < 90 AND Vehicle_Age_Months > 24) OR (Battery_Status IN ('Critical', 'Warning'))
	   Learn a more to correct the query & the result clear the confussion.
### 7. Real-World Use In My Project
	   what we wrote in Query 1 helped us prove that LFP batteries hold health better than NMC in the project	   
