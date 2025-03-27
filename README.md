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

