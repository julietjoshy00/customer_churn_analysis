# E-Commerce Customer Churn Analysis (MySQL)

SQL analysis of an e-commerce customer dataset to understand why customers churn, covering data cleaning, transformation and 17 business questions.

## Objective
Use historical customer data (tenure, payment mode, satisfaction score, purchase behaviour and more) to uncover patterns behind customer churn, so that targeted retention strategies can be planned.

## Tools
- MySQL 8
- MySQL Workbench

## Dataset
E-commerce customer churn dataset (5,630 customer records) loaded into a table named `customer_churn` in the `ecomm` database.

## What I did

### 1. Data cleaning
- Filled missing values with the **mean** (rounded) for `WarehouseToHome`, `HourSpendOnApp`, `OrderAmountHikeFromlastYear`, `DaySinceLastOrder`
- Filled missing values with the **mode** for `Tenure`, `CouponUsed`, `OrderCount`
- Removed outliers: rows where `WarehouseToHome` > 100
- Standardised inconsistent text (`Phone` / `Mobile` to `Mobile Phone`, `COD` to `Cash on Delivery`, `CC` to `Credit Card`)

### 2. Data transformation
- Renamed `PreferedOrderCat` to `PreferredOrderCat` and `HourSpendOnApp` to `HoursSpentOnApp`
- Created `ComplaintReceived` (Yes/No) and `ChurnStatus` (Churned/Active) using `CASE WHEN`
- Dropped the original `Churn` and `Complain` columns

### 3. Analysis (17 questions)
Churn and active counts, churn rate among complainers, city-tier and payment-mode patterns, coupon and cashback behaviour, distance-from-warehouse segments, and a `customer_returns` table joined to the customer data.

## SQL concepts used
`UPDATE`, `DELETE`, `ALTER TABLE`, `CASE WHEN`, `GROUP BY`, `HAVING`, `ORDER BY`, `LIMIT`, aggregate functions (`COUNT`, `SUM`, `AVG`, `MAX`), subqueries, `JOIN`, `CREATE TABLE` and `INSERT`.

## Files
- `ecommerce_churn_analysis.sql`: the full script, in the order of the assignment

## How to run
1. Create the database: `CREATE DATABASE ecomm;`
2. Load the dataset into a table called `customer_churn`
3. Run `ecommerce_churn_analysis.sql` in MySQL Workbench
