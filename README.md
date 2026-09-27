SQL_ANALYTICS_REPORT
NovaKart E-Commerce SQL Analytics

📌 Project Overview

This project analyzes NovaKart, a realistic e-commerce dataset containing customers, orders, products, and returns. The analysis was performed primarily in SQL, with a focus on data cleaning, joins, revenue analysis, profitability, delivery performance, returns, and channel-level business diagnosis.

The project contains a 26-query SQL analytics report based on cleaned tables, while the original Excel practice pack contains 40 business questions ranging from beginner to intermediate difficulty.

Business Objective

The goal is to turn raw e-commerce data into actionable business insights around:

Revenue and order performance

Product and category performance

Customer and city performance

Sales channels

Payment methods

Monthly and yearly trends

Profitability and margins

Delivery performance

Product returns and return reasons

Channel-level operational performance

📂 Dataset

The source Excel workbook contains the following sheets:

Sheet

Rows

Purpose

orders

8,853

Order-level transaction data

customers

2,400

Customer master data

products

25

Product, category and cost information

returns

671

Return transactions and reasons

The workbook also includes:

START HERE — project instructions

Data Dictionary — column definitions and data-quality warnings

Questions — 40 business questions

The SQL report works with cleaned versions of the four core tables: orders_cleaned, customers_cleaned, product_cleaned, and returns_cleaned.

🧹 Data Quality & Cleaning

The Excel data contains intentionally messy real-world issues that need to be considered before analysis.

Orders

Exact duplicate rows are present.

order_date is stored as text in two date formats.

Some customer_id values do not match the customer table.

quantity contains impossible/non-positive values.

discount_pct mixes decimal and percentage formats:

0.15

15

Some payment methods are blank.

Some delivery times are missing.

order_status has inconsistent casing such as:

Delivered

DELIVERED

Returned

RETURNED

Cancelled

CANCELLED

Customers

City names contain inconsistent casing and whitespace.

Some customer emails are missing.

Returns

Return data is linked to orders through order_id.

Return reasons and refund status are available for diagnosis.

Products

Product data provides:

Category

Sub-category

Cost price

List price

🔗 Data Model

The main relationships used in the analysis are:

customers │ │ customer_id ▼ orders ────────────────► products │ │ │ order_id │ product_id ▼ │ returns │

Key joins:

orders.customer_id = customers.customer_id

orders.product_id = products.product_id

returns.order_id = orders.order_id

📊 Key Business Findings

Data Coverage & Customer Matching
The SQL report identified 17 unmatched orders when orders were checked against the customer table.

Using an INNER JOIN rather than a LEFT JOIN reduced the revenue included in the analysis because unmatched customer records were excluded.

The report's cleaned analysis produced:

Net revenue: ₹21,048,578.05

Valid orders: 8,005

This demonstrates why join type matters in business reporting.

