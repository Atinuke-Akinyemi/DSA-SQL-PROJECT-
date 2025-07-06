# DSA-SQL-PROJECT-
## Kultra Mega Stores (KMS) Sales Analysis
### Description: A detailed analysis of sales and order data for a retail company.
#### Steps to my SQL Analysis 
- Firstly i created a Database and named it KMS_db and then created Table KMS_dbORDERS
Below are my queries:
CREATE DATABASE KMS_DB

Create Table KMS_dbORDERS(
[Row_ID]INT,
[ORDER_ID]INT,
[ORDER_Date]Date,
[ORDER_Priority]varchar(50),
[ORDER_Quantity]Int,
Sales Decimal (10,2),
Discount Decimal (10,2),
[ship_Mode]Varchar (50),
Profit Decimal(10,2),
[Unit_Price]Decimal(10,2),
[Shipping_Cost]Decimal (10,2),
[Customer_Name] Varchar (255),
Province Varchar (100),
Region Nvarchar(100)
[Customer_segment] varchar (100),
[Product_Category]  varchar (100),
[product_sub_category]varchar (100),
[product_name]varchar (max),
[product_container] varchar(100),
[product_base margin] decimal(10,2)
[ship_date] date
)

Below are my query use to answer the Following Questions:
--- Which product Tocategory that has the highest?

select product_category, sum([Sales]) as [Total sales]
from [dbo] .[KMS SQL case study]
group by product_category
order by [Total sales]desc

[dbo].[KMS SQL case study]
select * from [dbo].[KMS SQL case study]
CREATE DATABASE KULGAR_DB
