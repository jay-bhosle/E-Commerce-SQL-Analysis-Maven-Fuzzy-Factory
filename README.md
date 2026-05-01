# Maven Fuzzy Factory – E‑Commerce Marketing Analytics  
**SQL‑driven analysis of traffic sources, conversion rates, and revenue growth**

## Project Overview
Analysed 1+ year of website data for Maven Fuzzy Factory, an online teddy bear retailer. I cleaned raw data, built a reliable database, and ran layered SQL queries to uncover how marketing channels perform, how conversion rates evolve, and where to double down for scalable revenue.

## Tools & Technologies
- **SQL (MySQL Workbench)** – Data loading, cleaning, quality checks, and all business‑critical analysis  
- **Excel** – Quick charting and final summary (optional)

## Data Pipeline

### 1. Database & Raw Data
Created schema and loaded four CSV files (sessions, pageviews, orders, order items) using `LOAD DATA INFILE`.  
<img width="1920" height="1080" alt="Screenshot (103)" src="https://github.com/user-attachments/assets/54997c38-ca31-4ca0-ae8b-9fa987366865" />  
<img width="1920" height="1080" alt="Screenshot (104)" src="https://github.com/user-attachments/assets/7849fdcd-5e72-44d2-a244-57b86e5146d0" />

### 2. Data Quality Checks
Ran NULL checks and duplicate detection on key fields (session ID, user ID, order ID, price). No critical issues found.  
<img width="1920" height="1080" alt="Screenshot (106)" src="https://github.com/user-attachments/assets/7a9f607b-3839-404c-8f9f-e3be5c829560" />

### 3. Data Cleaning
Created clean tables: removed rows with NULL keys, invalid prices, and orphaned pageviews or order items.  
<img width="1920" height="1080" alt="Screenshot (107)" src="https://github.com/user-attachments/assets/6a1295eb-3453-4165-90e9-d607a336e5c8" />

## Key Insights (All SQL‑Generated)

### 📈 Sessions & Orders Growth
Sessions grew from 1,879 (Mar 2012) to 14,032 (Nov 2013) – a 7.5× increase. Orders scaled proportionally, showing strong demand.  
<img width="1920" height="1080" alt="Screenshot (109)" src="https://github.com/user-attachments/assets/091541e8-7c91-41ae-b31f-72d9845cfcbb" />  
<img width="1920" height="1080" alt="Screenshot (110)" src="https://github.com/user-attachments/assets/1079a360-e531-450c-96fa-d89c9c464ed4" />

### 🔁 Conversion Rate Trend
Session‑to‑order conversion rate improved from **3.2% to 7.1%** – more than doubling over the period. Consistent optimization is paying off.  
<img width="1920" height="1080" alt="Screenshot (112)" src="https://github.com/user-attachments/assets/e8fed89a-8680-41d7-ad7e-1369fb01bf86" />

### 📣 Most Successful Channels
- **Organic Search** drove 394k sessions (83% of total) with a 6.6% conversion rate.  
- **Paid / Tagged Traffic** delivered 78k sessions with a higher conversion rate of **7.8%**.  
Both channels are efficient; Organic is the scalable backbone.  
<img width="1920" height="1080" alt="Screenshot (116)" src="https://github.com/user-attachments/assets/ab51e179-1d28-4821-8844-409f6ba0e5e5" />

### 💰 Revenue per Session
Revenue per session rose from **$1.60 to $3.70** – a 2.3× uplift. This reflects both higher conversion and increased order value.  
<img width="1920" height="1080" alt="Screenshot (123)" src="https://github.com/user-attachments/assets/cf66d968-004e-4a6f-a79c-37d9dbfedb86" />

### 📊 Final Channel Economics
Summarised each channel’s sessions, orders, total revenue, revenue per order, and revenue per session to prioritize investment.  
<img width="1920" height="1080" alt="Screenshot (125)" src="https://github.com/user-attachments/assets/9f789ae9-76ed-4356-814c-1efb5e9a6801" />

## Recommendations (Directly from Analysis)
- **Keep investing in SEO** – it fuels 83% of sessions and delivers strong, growing revenue.  
- **Scale paid campaigns cautiously** – 7.8% conversion rate proves efficiency; test budget increases.  
- **Continue UX/checkout optimization** – conversion rate has doubled already; further gains compound quickly.  
- **Focus on revenue per session** – add cross‑sells, bundles, and personalised offers to push beyond $3.70.  
- **Pricing & product strategy** – sustained revenue per order growth indicates customers are willing to buy higher‑value items.
