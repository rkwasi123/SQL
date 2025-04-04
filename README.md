# Superstore SQL Query Project

This project demonstrates how SQL can be used to extract meaningful insights from a database. The dataset used for this project is the **Superstore** database, which contains information about items sold at the store, including their names, categories, and prices.

## Overview

The purpose of this project is to:
1. Extract and sort information about item prices.
2. Calculate meaningful statistics related to item prices.
3. Focus on specific categories within the dataset, such as "Kitchen Supplies" and "Electronics."

## Queries

### 1. Order Items by Price
This query retrieves the names and prices of items and orders them by price in ascending order.

```sql
SELECT 
    item_name
    , price
FROM superstore
ORDER BY price;

### 2. General Statistics on Item Prices
These queries calculate the total and average prices of all items in the database:
Total Price of All Items:

```sql
SELECT
    SUM(price) AS total_price
FROM superstore;

Average Price of All Items:
```sql
SELECT 
    ROUND(AVG(price), 2) AS average_price
FROM superstore;

### 3. Statistics on "Kitchen Supplies"
This query calculates the total price of items categorized as "Kitchen Supplies."

```sql
SELECT 
    ROUND(SUM(price), 2) AS total_price
FROM superstore
WHERE category = 'Kitchen Supplies';

### 4. Cheapest Item in "Electronics"
This query retrieves the details of the cheapest item in the "Electronics" category.

```sql
SELECT *
FROM superstore
WHERE category = 'Electronics'
ORDER BY price ASC;

# Fortune Companies SQL Queries

Queries
1. Retrieve Company Details with Health Benefits Indicator
This query selects the company name, industry, and a new column Health_benefit that indicates if a company offers healthcare benefits. It uses a CASE statement to map a binary value to 'Yes' or 'NO', and filters companies that provide more than 20 paid time off days.

```sql
SELECT
    company_name, -- Name of the company
    industry, -- Industry in which the company operates
    CASE
        WHEN healthcare_benefits = 1 THEN 'Yes' -- If healthcare benefits is marked as 1, display 'Yes'
        ELSE 'NO' -- Otherwise, display 'NO'
    END AS Health_benefit
FROM fortune_companies
WHERE paid_time_off_days > 20; -- Only include companies with more than 20 paid time off days


Queries
1. Retrieve Company Details with Health Benefits Indicator
This query selects the company name, industry, and a new column Health_benefit that indicates if a company offers healthcare benefits. It uses a CASE statement to map a binary value to 'Yes' or 'NO', and filters companies that provide more than 20 paid time off days.

```sql
SELECT
    company_name, -- Name of the company
    industry, -- Industry in which the company operates
    CASE
        WHEN healthcare_benefits = 1 THEN 'Yes' -- If healthcare benefits is marked as 1, display 'Yes'
        ELSE 'NO' -- Otherwise, display 'NO'
    END AS Health_benefit
FROM fortune_companies
WHERE paid_time_off_days > 20; -- Only include companies with more than 20 paid time off days


 #Identify the Retail Company with the Least Revenue
This query identifies the company within the Retail industry that has the lowest revenue.


-- Which company in the Retail industry has the least revenue, and what's their revenue?
```sql
SELECT 
    company_name, -- Name of the company
    min(revenue) -- Minimum revenue value among Retail companies
FROM fortune_companies
WHERE industry = 'Retail'; -- Filter for the Retail industry


-- Categorize Healthcare Companies by Maternity Leave Policy
This query assigns a categorization to companies in the Healthcare industry based on the weeks of maternity leave they offer. Companies are labeled as "mother friendly workplace", "acceptable", or "abysmal" based on the following criteria:

mother friendly workplace: 10 or more weeks of maternity leave

acceptable: 8 or more weeks (but less than 10)

abysmal: less than 8 weeks

```sql
SELECT
    company_name, -- Name of the company
    CASE 
        WHEN maternity_leave_weeks >= 10 THEN 'mother friendly workplace' -- 10 or more weeks is considered very supportive
        WHEN maternity_leave_weeks >= 8 THEN 'acceptable' -- Between 8 and 9 weeks is acceptable
        ELSE 'abysmal' -- Less than 8 weeks is considered abysmal
    END AS mother_friendliness -- New column indicating the maternity leave rating
FROM fortune_companies
WHERE industry = 'Healthcare'; -- Only include companies in the Healthcare industry
