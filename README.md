# DATA-ANALYST-INTERNSHIP-TASK-4
■ Coffee Sales Analysis (SQL Project)
■ Project Overview
This project demonstrates the use of SQL queries to analyze coffee sales data stored in an
 database. It covers data cleaning, transformation, revenue analysis, profit calculation,
joins, subqueries, and views to extract business insights.
■■ Database & Tables
- Database: ecommerce
- Tables Used:
• mytable → contains sales transactions (date, coffee_name, price, card)
• mytable1 → additional data (for practice queries)
• make_cost → contains cost price for each coffee
■ Key SQL Queries
1. Get All Data from Tables
SELECT * FROM mytable;
SELECT * FROM mytable1;
2. Data Cleaning: Replace NULL with 'cash'
UPDATE mytable
SET card = 'cash'
WHERE card IS NULL;
3. Retrieve Date & Coffee Name
SELECT date, coffee_name FROM mytable;
4. Rename Column
ALTER TABLE mytable
RENAME COLUMN money TO price;
5. Revenue by Coffee
SELECT coffee_name, SUM(price) AS revenue
FROM mytable
GROUP BY coffee_name;
6. Unique Coffee Types with Prices
SELECT DISTINCT coffee_name, price FROM mytable;
7. Average Sales per Day
SELECT date, AVG(price) AS avg_revenue
FROM mytable
GROUP BY date;
8. Highest Revenue Day
SELECT date, SUM(price) AS highest_revenue
FROM mytable
GROUP BY date
ORDER BY highest_revenue DESC
LIMIT 1;
9. Top 5 Best-Selling Coffees
SELECT coffee_name, COUNT(coffee_name) AS top_5_coffee
FROM mytable
GROUP BY coffee_name
ORDER BY top_5_coffee DESC
LIMIT 5;
10. Join Sales with Cost Table
SELECT *
FROM mytable mt
JOIN make_cost mc
ON mt.coffee_name = mc.coffee_name;
11. Profit by Coffee
SELECT mt.coffee_name,
 SUM(mt.price - mc.coffee_cost) AS profit
FROM mytable mt
JOIN make_cost mc
 ON mt.coffee_name = mc.coffee_name
GROUP BY mt.coffee_name
ORDER BY profit DESC;
12. Create and Use a View (Daily Revenue)
CREATE VIEW daily_revenue AS
SELECT date, SUM(price) AS revenue
FROM mytable
GROUP BY date;
SELECT * FROM daily_revenue ORDER BY revenue DESC;
■ Insights Gained
- Identified top-selling coffee types.
- Found the highest revenue-generating day.
- Calculated profit margins by comparing price vs. cost.
- Cleaned sales data by handling NULL values.
- Created a daily revenue view for easier analysis.
■ Features Demonstrated
✔■ Data Cleaning (UPDATE ... WHERE IS NULL)
✔■ Schema Modification (ALTER TABLE ... RENAME COLUMN)
✔■ Aggregation (SUM, AVG, COUNT)
✔■ Filtering & Ordering (WHERE, ORDER BY, LIMIT)
✔■ Joins (to combine sales & cost data)
✔■ Views (for reusable queries)
