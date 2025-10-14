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

**Business Insights**
**Category	Insight**
**Customer Segmentation**	Gold customers account for ~60% of total sales.
**Spending** Patterns	Gold customers spend 2.5× more per order than Bronze.
**Recency**	Customers inactive for 60+ days show 40% lower retention.
**Regional Performance**	South and West regions lead in total sales contribution.
**Channel** Trend	Online channels dominate 68% of total orders.

**Recruiter-Ready Summary**
This project demonstrates real-world data engineering and analytics skills — building a structured SQL Data Warehouse, performing ETL transformations, ensuring data quality, and generating analytical insights through Power BI. It showcases SQL proficiency, business understanding, and end-to-end data handling capability.Built around the same Bronze–Silver–Gold framework used in modern data lake and warehouse systems like Databricks, Snowflake.Implements practical business analytics metrics — RFM, customer segmentation, sales performance, and churn analysis — relevant for real-world use cases and used for validations, standardization, and reconciliation logic to ensure data trustworthiness.Optimized joins, aggregations, and bulk operations ensure efficient query execution even on large datasets. Gold views directly connect to Power BI, supporting KPI dashboards and visual storytelling.






