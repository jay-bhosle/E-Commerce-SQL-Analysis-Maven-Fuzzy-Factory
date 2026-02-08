# E-Commerce SQL Analysis – Maven Fuzzy Factory

This project analyzes the full e-commerce customer journey for Maven Fuzzy Factory, a fictional online retailer specializing in teddy bears. Using SQL, the project explores website traffic, conversion performance, marketing effectiveness, revenue efficiency, and refund behavior to generate actionable business insights.

---

## 🎯 Business Objective

The goal of this analysis is to:
- Understand website traffic growth and seasonality
- Measure session-to-order conversion performance
- Evaluate marketing channel effectiveness
- Analyze revenue efficiency and average order value
- Identify refund anomalies and data quality issues
- Provide actionable recommendations to optimize marketing spend and website performance

---

## 🗂 Database Overview

The database captures the complete customer funnel:
- Website sessions and pageviews
- Orders and order line items
- Product data
- Refund transactions

This structure enables analysis from first website visit through purchase and post-purchase behavior.

---

## 🛠 Tools & Technologies

- **SQL (MySQL syntax)**
- **Relational Database Design**
- **Data Cleaning & Validation**
- **Analytical Querying**

---

## 🧱 Database Schema

Key tables used in the analysis:
- `website_sessions`
- `website_pageviews`
- `orders`
- `order_items`
- `order_item_refunds`
- `products`

Cleaned versions of each table were created to ensure accurate and reliable analysis.

---

## 🧹 Data Cleaning & Quality Checks

Before analysis, extensive validation and cleaning were performed:
- Removed records with null or invalid identifiers
- Eliminated duplicate sessions and orders
- Removed zero or negative revenue orders
- Ensured referential integrity between sessions, orders, and pageviews
- Flagged refund records where refund amounts exceeded item prices
- Standardized UTM and referral logic for channel analysis

These steps ensured all KPIs and trends were trustworthy.

---

## 📊 Key Analyses Performed

### Traffic & Order Trends
- Monthly and quarterly website session trends
- Order volume trends over time
- Session vs. order comparison

### Conversion Performance
- Overall session-to-order conversion rate
- Monthly and quarterly conversion trends

### Marketing Channel Analysis
- Channel-level sessions, orders, and conversion rates
- Revenue per order and revenue per session by channel
- Comparison of paid, organic, and direct traffic performance

### Revenue Efficiency
- Average Order Value (AOV)
- Revenue per session
- Revenue trends over time

### Refund Analysis
- Identification of refund anomalies
- Summary of refunds exceeding original item price

---

## 🔍 Key Insights

- Conversion rates fluctuate significantly over time, indicating optimization opportunities
- Some marketing channels generate higher revenue efficiency despite lower traffic
- Revenue per session highlights opportunities to increase monetization without increasing traffic
- Refund anomalies reveal potential data integrity or process issues

---

## 💡 Business Recommendations

- Reallocate marketing spend toward high-efficiency channels
- Focus CRO efforts during historically low-conversion periods
- Increase revenue per session through bundling and upselling
- Investigate and prevent over-refund scenarios
- Improve UTM tagging and attribution logic for more accurate channel reporting

---

## 📂 Project Structure

