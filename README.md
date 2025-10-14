# Customer-Segmentation-and-Analysis-SQL-Data-Analytics-Project
This project demonstrates an end-to-end SQL Data Analytics pipeline built using Microsoft SQL Server, designed to analyze and segment customers based on their purchasing behavior. It follows a Data Warehouse architecture Bronze → Silver → Gold and integrates raw transactional data, cleaned datasets, and analytical SQL scripts to generate business business insights such as customer segmentation, sales performance, and regional profitability.

**Data Warehouse Architecture**
**Layer	Purpose	Description**
**Bronze Layer:**	Data Ingestion	Stores raw customer and transaction data directly from CSV sources.
**Silver Layer:**	Data Cleansing & Aggregation	Cleans and standardizes data, calculates metrics like total sales, average order value, and recency.
**Gold Layer:**	Analytics & Reporting	Creates analytical views and customer segmentation dashboards.

**Tech Stack & Tools**
**Database:**	Microsoft SQL Server
**Query Language:**	T-SQL
**Data Integration:**	BULK INSERT, Stored Procedures
**Data Visualization:**	Power BI / Tableau
**Version Control:**	GitHub
**Documentation:**	Markdown, PDF Reports


**TL Process Overview:**
**Step 1 — Initialize Database & Schemas**
CREATE DATABASE CustomerAnalytics;
GO

USE CustomerAnalytics;
GO

CREATE SCHEMA bronze;
CREATE SCHEMA silver;
CREATE SCHEMA gold;
GO
🔸 Step 2 — Bronze Layer (Raw Data Load)
CREATE TABLE bronze.customer_orders (
    customer_id INT,
    order_id INT,
    order_date DATE,
    product_id INT,
    quantity INT,
    price DECIMAL(10,2),
    total_sales DECIMAL(10,2),
    region VARCHAR(50),
    channel VARCHAR(50)
);
Load data using BULK INSERT:
BULK INSERT bronze.customer_orders
FROM 'C:\\data\\customer_orders_raw.csv'
WITH (FIRSTROW = 2, FIELDTERMINATOR = ',', ROWTERMINATOR = '\n');
________________________________________
🔸 Step 3 — Silver Layer (Cleansed & Aggregated)
CREATE TABLE silver.customer_summary AS
SELECT 
    customer_id,
    COUNT(order_id) AS total_orders,
    SUM(total_sales) AS total_sales,
    AVG(total_sales) AS avg_order_value,
    DATEDIFF(DAY, MAX(order_date), GETDATE()) AS recency,
    region,
    CASE 
        WHEN SUM(total_sales) > 10000 THEN 'Gold'
        WHEN SUM(total_sales) BETWEEN 5000 AND 10000 THEN 'Silver'
        ELSE 'Bronze'
    END AS customer_segment
FROM bronze.customer_orders
GROUP BY customer_id, region;

Step 4 — Gold Layer (Analytical Views)
CREATE VIEW gold.vw_customer_insights AS
SELECT 
    customer_id,
    customer_segment,
    region,
    total_sales,
    avg_order_value,
    recency,
    CASE 
        WHEN recency <= 30 THEN 'Active'
        WHEN recency BETWEEN 31 AND 60 THEN 'Warm'
        ELSE 'At Risk'
    END AS customer_status
FROM silver.customer_summary;








SELECT TOP 10 customer_id, total_sales
FROM silver.customer_summary
ORDER BY total_sales DESC;
2️⃣ Segment-Wise Average Order Value
sql
Copy code
SELECT customer_segment, AVG(avg_order_value) AS avg_value
FROM silver.customer_summary
GROUP BY customer_segment;

SSMS Output Example:
customer_segment	avg_recency
Gold	21
Silver	34
Bronze	57




