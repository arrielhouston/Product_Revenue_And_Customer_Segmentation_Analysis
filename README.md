# 🎧 Product Revenue & Customer Segmentation Dashboard

## Overview
This project is an interactive Power BI dashboard designed to analyze product revenue, customer segmentation, and discount performance across multiple regions and time periods. SQL was used to prepare and transform the data before importing it into Power BI, enabling accurate reporting and scalable analysis.

The dashboard transforms raw product and sales data into actionable business insights to support pricing strategy, customer analysis, and performance tracking.

---

## Key Features
- Interactive slicers for Product, Customer Type, Country, Discount Band, and Year
- Year-over-year revenue and performance trend analysis
- Product-level revenue and profitability insights
- Customer segmentation analysis by customer type
- Discount band analysis to evaluate pricing and promotional impact
- Custom tooltips for enhanced context without cluttering visuals

---

## Key Insights
- Revenue is not evenly distributed across products, highlighting clear top performers and underperformers
- Government and Enterprise customer segments generate the highest revenue, indicating strong demand from organizational customers
- Higher discount bands drive significant revenue volume, though they may impact profit margins
- Revenue performance varies by country, revealing markets with stronger sales potential
- Monthly revenue trends show seasonality, reinforcing the importance of trend monitoring and forecasting

---

## Skills Demonstrated
- SQL (CTEs, joins, calculated fields)
- Power BI (data modeling, DAX, interactive visuals)
- Star Schema Data Modeling
- Time Intelligence & YoY Analysis
- Product & Customer Segmentation Analysis
- Business-Focused Data Storytelling

---

## SQL Data Preparation
SQL was used to join product, sales, and discount data into a single analysis-ready dataset prior to loading it into Power BI. This approach ensured clean modeling, consistent calculations, and efficient dashboard performance.

### Key SQL Tasks
- Joined product master data with transactional sales data
- Calculated revenue and total cost at the transaction level
- Created month and year fields for time-based analysis
- Applied discount logic based on discount band and month
- Generated discount-adjusted revenue for pricing analysis

### SQL Query Used
```sql
WITH cte AS (
    SELECT 
        a.Product,
        a.Category,
        a.Brand,
        a.Description,
        a.Sale_Price,
        a.Cost_Price,
        a.Image_url,
        b.Date,
        b.Customer_Type,
        b.Discount_Band,
        b.Country,
        b.Units_Sold,
        (Sale_Price * Units_Sold) AS revenue,
        (Cost_Price * Units_Sold) AS total_cost,
        FORMAT(Date, 'MMMM') AS month,
        FORMAT(Date, 'yyyy') AS year
    FROM product_data a
    JOIN product_sales b
        ON a.Product_ID = b.Product
)

SELECT 
    *,
    (1 - discount * 1.0 / 100) * revenue AS discount_revenue
FROM cte a
JOIN discount_data b
    ON a.Discount_Band = b.Discount_Band
   AND a.month = b.Month;

## How to Use
1. Download the Power BI file  
2. Open the file in Power BI Desktop  
3. Use slicers to filter by product, customer type, country, discount band, or year  
4. Hover over visuals to explore additional context using tooltips  

---

## 📸 Dashboard Preview
<img width="866" height="486" alt="Dashboard_Overview1" src="https://github.com/user-attachments/assets/b68773c5-63a0-481c-bc8a-dd00dc2e8ada" />
<img width="598" height="225" alt="Customer_segmentation" src="https://github.com/user-attachments/assets/e1233af1-98d1-4ff4-8705-1c9d48a2ab81" />
<img width="867" height="487" alt="Tootlips" src="https://github.com/user-attachments/assets/232f173c-a135-4a41-b13c-22979c4129a3" />



## Project Value
This project demonstrates how SQL and Power BI can be used together to build business-ready analytics solutions. It highlights my ability to prepare data, design interactive dashboards, analyze product and customer performance, and clearly communicate insights to both technical and non-technical stakeholders.

