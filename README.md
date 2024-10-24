---

# SQL Project: RFM Analysis on Superstore Dataset

## Introduction
This project demonstrates my ability to perform **RFM analysis** (Recency, Frequency, and Monetary) on a real-world dataset to segment customers and identify high-value clients for a business. The dataset used is the **Superstore sales data** for the years 2015-2018, and the code highlights key steps taken to analyze customer purchasing behavior.

**Key Skills Demonstrated:**
- **SQL Proficiency**: Use of advanced SQL techniques such as `WITH` statements and aggregate functions.
- **Customer Segmentation**: Understanding of RFM analysis for business intelligence and customer segmentation.
- **Data-Driven Insights**: Ability to extract insights and deliver actionable recommendations to stakeholders.
  
## Dataset Description
The dataset used is a sales dataset from a retail store, which includes information on customer purchases, order dates, sales, and other transactional details. Key columns include:
- `Customer_ID`: Unique identifier for each customer.
- `Order_Date`: Date when the order was placed.
- `Order_ID`: Unique identifier for each order.
- `Sales`: Total sales amount for each order.

## Project Goals
The main objective of this project is to:
1. Conduct an RFM analysis to segment customers based on their purchasing behavior.
2. Identify **high-value customers** who contribute significantly to the revenue.
3. Provide actionable insights to improve customer retention and sales strategies.

## SQL Code Breakdown
Below is a summary of the SQL code I used in the project, with explanations to help recruiters understand each part of the analysis.

### 1. **Check the Table**
```sql
-- Check the table to ensure the dataset is loaded correctly.
SELECT * FROM dataset_superstore;
```
This initial step ensures that the table is correctly loaded and allows for a quick inspection of the data structure.

### 2. **RFM Analysis**
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
**Explanation**:  
In this section, I calculated:
- **Recency**: Days since the customer’s last purchase.
- **Frequency**: Number of times a customer made a purchase.
- **Monetary**: Total value of purchases.

This helps categorize customers based on how recent, frequent, and valuable they are to the business.

### 3. **High-Value Customers Identification**
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
       Customer_ID,
       frequency,
       monetary
FROM rfm
WHERE monetary > (SELECT AVG(monetary) FROM rfm)
ORDER BY monetary DESC;
```
**Explanation**:  
This query identifies **high-value customers**, i.e., those whose total spending is higher than the average spending of all customers. This insight can be used for targeted marketing and retention campaigns.

## Insights and Recommendations
Based on the RFM analysis:
- **High Recency, High Frequency, High Monetary**: These are the most valuable customers. Retaining them should be a priority, and personalized promotions can help boost their lifetime value.
- **Low Recency, High Frequency, High Monetary**: These customers were valuable in the past but haven’t made recent purchases. Re-engagement strategies like personalized discounts or product recommendations can help win them back.

## Conclusion
This project highlights my ability to use SQL for advanced customer analytics. I demonstrated:
- Proficiency in writing **clean and efficient SQL code**.
- Use of **RFM analysis** to gain business insights.
- Data-driven approaches to **customer segmentation** and **retention strategies**.

---

## How to Run This Project
1. Clone this repository.
2. Load the dataset into your SQL environment.
3. Run the SQL queries in the provided file to perform the RFM analysis.

---

**Recruiters' Note**: This project showcases my ability to analyze data and derive meaningful insights that directly contribute to business goals. I am confident that my SQL skills and data-driven mindset will be an asset to any data analytics role.

---
