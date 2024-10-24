---

# SQL Project: RFM Analysis for Customer Segmentation

## Overview
This project uses SQL to conduct **RFM Analysis** (Recency, Frequency, Monetary) on a Superstore dataset to segment customers based on their purchasing behavior. It helps businesses identify high-value customers, optimize marketing efforts, and enhance customer retention strategies.

## Key Insights
- **Recency**: How recently a customer made a purchase.
- **Frequency**: How often they buy.
- **Monetary**: How much they spend.

**Goal**: Understand and segment customers to improve targeted marketing and drive higher revenue.

## Who Needs This?
- **Retailers and E-commerce**: To identify top customers, re-engage at-risk customers, and boost overall sales.
- **Marketing Teams**: To craft personalized campaigns and loyalty programs.
- **Business Executives**: To make data-driven decisions that maximize ROI on customer retention and acquisition strategies.

## My Role
As a **Data Analyst**, I bring expertise in using SQL to process large datasets, derive actionable insights, and support business growth by focusing on key customer segments. This analysis directly contributes to better decision-making, enabling companies to focus on **the right customers** at the **right time**.

## SQL Code Highlights
### RFM Analysis
```sql
WITH rfm AS (
    SELECT Customer_ID,
           MAX(Order_Date) AS last_purchase,
           COUNT(Order_ID) AS frequency,
           SUM(Sales) AS monetary
    FROM dataset_superstore
    GROUP BY Customer_ID
)
SELECT Customer_ID,
       DATEDIFF(CURDATE(), last_purchase) AS recency,
       frequency,
       monetary
FROM rfm
ORDER BY recency, frequency DESC, monetary DESC;
```
- **Purpose**: Segment customers by how recently they purchased, how often they buy, and their spending.
  
### High-Value Customers
```sql
WITH rfm AS (
    SELECT Customer_ID,
           MAX(Order_Date) AS last_purchase,
           COUNT(Order_ID) AS frequency,
           SUM(Sales) AS monetary
    FROM dataset_superstore
    GROUP BY Customer_ID
)
SELECT Customer_ID,
       DATEDIFF(CURDATE(), last_purchase) AS recency,
       frequency,
       monetary
FROM rfm
WHERE monetary > (SELECT AVG(monetary) FROM rfm)
ORDER BY monetary DESC;
```
- **Purpose**: Identify the top customers whose spending exceeds the average, allowing businesses to focus on those who drive the most revenue.

## Real-World Impact
By using this RFM analysis, businesses can:
- **Boost revenue** by focusing on high-value customers.
- **Reduce churn** by targeting at-risk customers who haven’t bought recently.
- **Increase efficiency** by prioritizing marketing resources to segments that matter.

## Why It Matters
In today’s competitive landscape, customer retention and targeted marketing are critical. This analysis allows businesses to segment customers in a meaningful way, offering clear insights that translate into real, actionable strategies.

## Where I Add Value
I specialize in translating raw data into business intelligence. My SQL expertise allows me to handle complex datasets, identify key customer segments, and provide insights that **drive growth**. This project showcases how I can help businesses improve customer engagement and boost sales by making **data-driven decisions**.

---

**Summary**:  
I’m passionate about using data to solve business problems. This RFM analysis is a snapshot of how I can help businesses maximize value from their customer base. By applying advanced SQL techniques, I ensure that businesses not only understand their customers better but can also take actionable steps toward improving their bottom line.

---
