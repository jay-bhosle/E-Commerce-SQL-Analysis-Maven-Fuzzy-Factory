📊 Maven Fuzzy Factory – SQL Data Analysis Project
📄 Pages 1–5: Project Overview & Database Setup
📌 Project Overview

This project analyzes the Maven Fuzzy Factory e-commerce dataset using MySQL.
The objective is to:

Build a relational database

Load raw CSV data

Perform data validation & cleaning

Analyze sessions, orders, conversion rates

Evaluate channel performance & revenue metrics

🗂 Database Creation
CREATE DATABASE maven_fuzzy_factory;
USE maven_fuzzy_factory;

🏗 Raw Tables Created
1️⃣ website_sessions

Stores visitor session data.

website_session_id

created_at

user_id

utm_source

utm_campaign

utm_content

device_type

http_referer

2️⃣ website_pageviews

Tracks page-level activity.

website_pageview_id

created_at

website_session_id

pageview_url

3️⃣ orders

Stores completed purchase data.

order_id

created_at

website_session_id

user_id

primary_product_id

price_usd

4️⃣ order_items

Contains item-level purchase data.

5️⃣ order_item_refunds

Tracks refunded items.

📥 Data Loading

Enabled local file loading:

SET GLOBAL local_infile = 1;


Loaded CSV files using:

LOAD DATA LOCAL INFILE 'file_path'
INTO TABLE table_name
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
<img width="1920" height="1080" alt="Screenshot (103)" src="https://github.com/user-attachments/assets/f5f4fd2e-0fc2-48ac-9109-337b56c55534" />
103
<img width="1920" height="1080" alt="Screenshot (104)" src="https://github.com/user-attachments/assets/04d66b15-582f-4b3c-a6bc-57adbc25d229" />
104
<img width="1920" height="1080" alt="Screenshot (105)" src="https://github.com/user-attachments/assets/baf708e4-c567-49da-96a6-c69a961f22e4" />
105
<img width="1920" height="1080" alt="Screenshot (106)" src="https://github.com/user-attachments/assets/77a70f28-66c5-4b60-b479-70d46599a152" />
106
<img width="1920" height="1080" alt="Screenshot (107)" src="https://github.com/user-attachments/assets/8f0aa042-d60d-4db2-a5b5-6a37639280f8" />
107

📄 Pages 6–10: Data Validation & Cleaning
🔎 Row Count Validation

Verified row counts across all tables:

SELECT COUNT(*) FROM website_sessions;
SELECT COUNT(*) FROM website_pageviews;
SELECT COUNT(*) FROM orders;
SELECT COUNT(*) FROM order_items;
SELECT COUNT(*) FROM order_item_refunds;

🚫 Null Checks

Validated key fields:

SELECT
COUNT(*) AS total_rows,
SUM(website_session_id IS NULL) AS null_session_id,
SUM(created_at IS NULL) AS null_created_at,
SUM(user_id IS NULL) AS null_user_id
FROM website_sessions;


Confirmed:

No null primary identifiers

Clean timestamps

Valid user data

🧹 Data Cleaning
Clean website sessions
CREATE TABLE website_sessions_clean AS
SELECT *
FROM website_sessions
WHERE website_session_id IS NOT NULL
AND created_at IS NOT NULL;

Clean orders
CREATE TABLE orders_clean AS
SELECT DISTINCT *
FROM orders
WHERE order_id IS NOT NULL
AND price_usd > 0;

Clean pageviews (valid sessions only)

Joined pageviews with cleaned sessions.

Clean order items

Joined order_items with valid orders.
<img width="1920" height="1080" alt="Screenshot (108)" src="https://github.com/user-attachments/assets/6fa16d23-2450-42d3-a06d-d3ee479ccc03" />
108
<img width="1920" height="1080" alt="Screenshot (109)" src="https://github.com/user-attachments/assets/42c2c691-a3c7-4c5d-bb9e-26e847332f8a" />
109
<img width="1920" height="1080" alt="Screenshot (110)" src="https://github.com/user-attachments/assets/95248840-5927-43bd-a739-0df13d492683" />
110
<img width="1920" height="1080" alt="Screenshot (111)" src="https://github.com/user-attachments/assets/98cc6dd0-e6e2-42a3-91ad-2ecee76c2698" />
111
<img width="1920" height="1080" alt="Screenshot (112)" src="https://github.com/user-attachments/assets/3c27b32e-b8a6-4350-997a-a90c74b258e3" />
112

📄 Pages 11–15: Core Performance Analysis
📅 Monthly Sessions
SELECT
YEAR(created_at) AS yr,
MONTH(created_at) AS mo,
COUNT(*) AS sessions
FROM website_sessions_clean
GROUP BY 1,2
ORDER BY 1,2;


📈 Observed steady growth from 2012–2014.

🛒 Monthly Orders
SELECT
YEAR(created_at) AS yr,
MONTH(created_at) AS mo,
COUNT(*) AS orders
FROM orders_clean
GROUP BY 1,2
ORDER BY 1,2;


Orders increased proportionally with sessions.

🔄 Sessions vs Orders
SELECT
YEAR(ws.created_at) AS yr,
MONTH(ws.created_at) AS mo,
COUNT(DISTINCT ws.website_session_id) AS sessions,
COUNT(DISTINCT o.order_id) AS orders
FROM website_sessions_clean ws
LEFT JOIN orders_clean o
ON ws.website_session_id = o.website_session_id
GROUP BY 1,2;

📊 Conversion Rate
Monthly Conversion Rate
COUNT(DISTINCT o.order_id) * 1.0 /
COUNT(DISTINCT ws.website_session_id)

📌 Overall Conversion Rate

6.83%
<img width="1920" height="1080" alt="Screenshot (113)" src="https://github.com/user-attachments/assets/1344574d-5799-4aef-b332-5e0e72fcf6bd" />
113
<img width="1920" height="1080" alt="Screenshot (114)" src="https://github.com/user-attachments/assets/3cabb950-2473-4eb6-8905-e18c24b64334" />
114
<img width="1920" height="1080" alt="Screenshot (115)" src="https://github.com/user-attachments/assets/cda6db7f-2487-4770-a157-cac6bcab87db" />
115
<img width="1920" height="1080" alt="Screenshot (116)" src="https://github.com/user-attachments/assets/984a77d0-b9e7-441b-a0ab-f11b4fe74ebb" />
116
<img width="1920" height="1080" alt="Screenshot (117)" src="https://github.com/user-attachments/assets/5a0d2c64-755d-4207-b59f-fc16afe19e83" />
117

📄 Pages 16–20: Revenue & Channel Analysis
💰 Average Order Value (AOV)
SELECT
SUM(price_usd) / COUNT(DISTINCT order_id) AS avg_order_value
FROM orders_clean;


📌 Overall AOV ≈ $59.99

📈 Monthly AOV

Tracked AOV growth over time.

💵 Revenue per Session
SUM(price_usd) / COUNT(DISTINCT website_session_id)


📌 Revenue per session ≈ $4.10

📢 Channel Performance Analysis
Channel Classification Logic
CASE
WHEN utm_source = 1 THEN 'Paid / Tagged Traffic'
WHEN utm_source = 0 AND http_referer IS NOT NULL THEN 'Organic Search'
WHEN utm_source = 0 AND http_referer IS NULL THEN 'Direct'
ELSE 'Other'
END

📊 Conversion by Channel
Channel	Sessions	Orders	Conversion Rate
Organic Search	39,438	2,614	6.63%
Paid / Tagged Traffic	78,553	6,149	7.83%

👉 Paid traffic converts better.

💰 Revenue by Channel
Channel	Revenue	Revenue per Order	Revenue per Session
Organic Search	$156,674	$59.86	$3.97
Paid / Tagged	$372,234	$60.53	$4.74

📌 Paid traffic drives higher revenue efficiency.

🧠 Key Insights

📈 Strong session & order growth over time

🔄 Overall conversion rate: 6.83%

💰 Stable AOV around $60

🚀 Paid traffic outperforms organic in:

Conversion rate

Revenue per session

Total revenue

🛠 Tech Stack

MySQL

SQL (Joins, Aggregations, CASE statements)

Data Cleaning Techniques

E-commerce Analytics

📂 How to Run

Clone repository

Create database

Load CSV files

Execute cleaning scripts

Run analysis queries
<img width="1920" height="1080" alt="Screenshot (119)" src="https://github.com/user-attachments/assets/8edf9e5f-30e9-44c5-91f9-c48c78f5b29a" />
119
<img width="1920" height="1080" alt="Screenshot (121)" src="https://github.com/user-attachments/assets/16b68f38-95c5-4601-9e25-f6b18edcf403" />
121
<img width="1920" height="1080" alt="Screenshot (122)" src="https://github.com/user-attachments/assets/fd945570-18f6-4d88-983f-02dd6d54c564" />
122
<img width="1920" height="1080" alt="Screenshot (123)" src="https://github.com/user-attachments/assets/dce73f28-11ee-4bbe-b5ec-352483b09592" />
123
<img width="1920" height="1080" alt="Screenshot (124)" src="https://github.com/user-attachments/assets/e4282ebc-c895-4752-9602-a3da50848687" />
124
<img width="1920" height="1080" alt="Screenshot (125)" src="https://github.com/user-attachments/assets/a8144f22-41a4-4543-bac4-38185ea2ba1b" />
125























