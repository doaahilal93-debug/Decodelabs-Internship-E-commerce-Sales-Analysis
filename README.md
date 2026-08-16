# Decodelabs Internship – E-commerce Sales Analysis

## Project Overview
This project was completed as part of the Decodelabs Internship task.
The goal was to analyze e-commerce order data and turn raw data into meaningful business insights using Python, SQL, and Power BI.
The analysis covers sales, customers, products, orders, payment methods, coupons, referral sources, cancellations, and returns.

## Dataset
The dataset contains:
- 1,200 orders
- 1,189 unique customers

### Main Columns
`OrderID` · `OrderDate` · `CustomerID` · `Product` · `Quantity` · `UnitPrice` · `TotalPrice` · `ItemsInCart` · `PaymentMethod` · `OrderStatus` · `CouponCode` · `ReferralSource`

---

## 1. Python – Data Cleaning & Exploratory Analysis
Python was used to understand the dataset, check data quality, and prepare the data for further analysis.

### Data Inspection
python
df.info()
df.describe()

These checks were used to review data types, dataset structure, basic statistics, and numeric distributions.

### Data Quality Checks

Missing values were checked using:

python
df.isna().sum()

Missing CouponCode values were replaced with a meaningful category:

python
df['CouponCode'] = df['CouponCode'].fillna('No Coupon')

Duplicate rows were checked using:

python
df.duplicated().sum()

Categorical columns were also reviewed using `value_counts()`.

### Statistical Analysis

Calculated:

* Range
* Q1
* Median
* Q3
* IQR
* Lower and Upper Bounds

Potential outliers were identified using the 1.5 × IQR rule.

### Visualization

Created boxplots for:

* Quantity
* UnitPrice
* ItemsInCart
* TotalPrice

### Export

The cleaned dataset was exported for SQL analysis:

```python
df.to_csv('cleaned_data.csv', index=False)

```

---

## 2. SQL – Business Analysis

SQL was used to validate the data, answer business questions, and calculate key metrics.

### Customer Analysis

* Total unique customers
* Orders per customer
* Cancelled orders per customer
* Returned orders per customer

### Product Analysis

* Units sold by product
* Orders by product
* Most cancelled products
* Most returned products

### Payment & Marketing Analysis

* Orders by payment method
* Customers by referral source
* Coupon performance

### Sales Metrics

* **Gross Revenue:** Total TotalPrice across all orders.
* **Revenue:** Revenue from Shipped and Delivered orders in the final Power BI dashboard.
* **Average Order Value (AOV):** Average value of completed orders.
* **Cancellation Rate:** Percentage of orders with Cancelled status.

---

## 3. Power BI – Data Modeling & Dashboard

Power BI was used to create the final interactive dashboard.

### Data Model

The main sales table was kept as one table because the dataset is relatively small.
A separate Date table was created for time-based analysis:

* Date
* Year
* Quarter
* Month
* Month Number

The Date table was connected to the Sales table using a 1-to-many relationship.

### Key Measures

* Gross Revenue
* Revenue
* AOV
* Total Orders
* Total Customers
* Units Sold
* Cancellation Rate
* Return Rate
* Pending Rate
* Average Orders per Customer

### Dashboard Pages

#### Sales

Focuses on overall sales performance.
**KPIs**

* Gross Revenue
* Revenue
* AOV
* Total Orders

**Visualizations**

* Revenue Trend
* Orders by Product
* Revenue by Payment Method
* Revenue by Coupon Code

#### Customers

Focuses on customer behavior and acquisition.
**KPIs**

* Total Customers
* Average Orders per Customer
* Units Sold

**Visualizations**

* Customers by Referral Source
* Unique Customers by Product
* Orders by Order Status

#### Order Issues

Focuses on cancellations, returns, and pending orders.
**KPIs**

* Cancellation Rate
* Return Rate
* Pending Rate

**Visualizations**

* Cancellation Rate Trend
* Cancellation Rate by Product
* Return Rate by Product

---

## Key Insights

### 1. High Cancellation Rate

The cancellation rate is 20.83%, meaning approximately 1 in every 5 orders was cancelled.
This makes cancellations an important area for further investigation, especially for products with high cancellation rates.

### 2. Low Repeat Purchasing

The dataset contains 1,189 customers and 1,200 orders, resulting in an average of 1.01 orders per customer.
This indicates that most customers placed only one order and highlights an opportunity to improve repeat purchases and retention.

### 3. Gap Between Gross Revenue and Realized Revenue

Gross Revenue is approximately 1.26M, while Revenue from shipped and delivered orders is approximately 489K.
This highlights the importance of monitoring cancelled, returned, and pending orders to understand the gap between recorded order value and realized revenue.

---

## Business Recommendations

* Investigate the main reasons behind cancellations and returns.
* Review products with unusually high cancellation or return rates.
* Develop strategies to encourage repeat purchases and improve customer retention.
* Monitor cancelled, returned, and pending orders to better understand realized revenue.

---

## Skills Demonstrated

* **Python:** Pandas, NumPy, Matplotlib, Seaborn
* **Data Analysis:** Data cleaning, EDA, descriptive statistics, IQR and outlier analysis
* **SQL:** Filtering, aggregation, GROUP BY, COUNT, SUM, AVG, DISTINCT, CASE
* **Power BI:** Data modeling, DAX, KPI development, interactive dashboards
* **Business Analysis:** KPI selection, business questions, insights, and recommendations

---

## Project Workflow

> Raw Data → Python Cleaning & EDA → SQL Business Analysis → Power BI Dashboard → Business Insights
