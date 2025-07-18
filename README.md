# DSA-SQL-PROJECT-
## Kultra Mega Stores (KMS) Sales Analysis
### Description: A detailed analysis of sales and order data for a retail company.
#### Steps to my SQL Analysis 
- Firstly i created a Database and named it #### project and then select all my data from my [KMS Sql Case Study] table that i imported to my project database
##### Below are my queries use to create my database and to select my data from my database:
create database project

select*
from [KMS Sql Case Study]
#### My display table below after selecting all my data
<img width="1600" height="900" alt="SQL FIRST PAGE SCREENSHOT" src="https://github.com/user-attachments/assets/a8ff5500-017b-4aea-b8fc-a227ab29e205" />

#### Below are my query use to answer the Following Questions:

##### QUESTION 1: Which product category had the highest sales?
select top 1 
[Product_Category],count 
([Product_Category])as 
[Product Count]
from [KMS Sql Case Study]
group by Product_Category
order by [Product Count] 
desc
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 1" src="https://github.com/user-attachments/assets/b7c92045-3742-4633-8491-d2640a65fac0" />

##### QUESTION 2: What are the Top 3 and Bottom 3 regions in terms of sale
select top 3 
[Region],sum([sales]) as 
[Total Sales]
from [KMS Sql Case Study]
group by Region
order by [Total Sales] desc

select top 3 
[Region],sum([sales]) as 
[Total Sales]
from [KMS Sql Case Study]
group by Region
order by [Total Sales] asc
##### My display table below:
<img width="1600" height="868" alt="SCREENSHOT QUESTION 2" src="https://github.com/user-attachments/assets/b5545fed-0280-4843-8d1f-893035c2fca7" />

##### QUESTION 3: What were the total sales of appliances in Ontario?
Select Region, SUM(sales) 
as [Total Sales]
from [KMS Sql Case Study]
where Region='ontario'
Group by Region
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 3" src="https://github.com/user-attachments/assets/ded907de-487c-4e04-a82b-efc3ab03b429" />

##### QUESTION 4: Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
Select top 10 
[Customer_Name], 
SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study]
group by Customer_Name
order by [Total Sales] asc
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 4" src="https://github.com/user-attachments/assets/7a8a92fe-a75c-433d-876d-dceb9ec11bf2" />

##### QUESTION 5: KMS incurred the most shipping cost using which shipping method?
Select Top 1 [Ship_Mode], 
SUM([Shipping_Cost]) as 
[Total Shipping Cost]
from [KMS Sql Case Study]
group by Ship_Mode
order by [Total Shipping Cost] desc
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 5" src="https://github.com/user-attachments/assets/9e7c4e15-fbd6-4c12-a2d4-828cc339e968" />

##### QUESTION 6: Who are the most valuable customers, and what products or services do they typically purchase?
Select [Customer_Name],Product_Name, 
SUM(sales) as [Total Sales]
from [KMS Sql Case Study]
Group by Customer_Name,Product_Name
order by [Total Sales] desc
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 6" src="https://github.com/user-attachments/assets/6aa41a10-b129-476e-8b83-184fdb8ab24c" />

##### QUESTION 7: Which small business customer had the highest sales?
Select top 1 
Customer_Name,Customer_Segment, 
SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study]
where Customer_Segment ='small Business'
group by Customer_Name,Customer_Segment
order by [Total Sales] desc
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 7" src="https://github.com/user-attachments/assets/79834bf6-87cd-49fa-8b00-d95cfba22788" />

##### QUESTION 8: Which Corporate Customer placed the most number of orders in 2009 – 2012?
Select top 1  
Customer_Name,Customer_Segment, count([Order_ID]) as [Total order]
from [KMS Sql Case Study]
where Customer_Segment ='corporate' and Order_Date between '2009' and '2012'
group by Customer_Name,Customer_Segment
order by [Total order] desc
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 8" src="https://github.com/user-attachments/assets/d14eac55-47bc-408d-9f51-14f21ec40bf5" />

##### QUESTION 9: Which consumer customer was the most profitable one?
Select top 1 
Customer_Name,Customer_Segment, sum([Profit]) as [Total profit]
from [KMS Sql Case Study]
where Customer_Segment ='Consumer'
group by Customer_Name,Customer_Segment
order by [Total profit] desc
##### My display table below:
<img width="1600" height="900" alt="SCREENSHOT QUESTION 9" src="https://github.com/user-attachments/assets/a8ee18f2-a211-4aa2-9df3-75369f2a2970" />

##### QUESTION 10: Which customer returned items, and what segment do they belong to?
select Customer_Name,Customer_Segment,[Status]
from [KMS Sql Case Study]
join [dbo].[Order_Status]
on [KMS Sql Case Study].Order_ID = [dbo].[Order_Status].[Order_ID]

##### If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority?
Select Order_Priority, Ship_Mode,
COUNT([Order_ID]) AS [order count],
SUM(sales - profit) AS [Estimated shipping cost],
AVG(DATEDIFF(DAY, [Order_Date], [Ship_Date])) AS [Avg ship date]
from  [KMS Sql Case Study1] 
group by Order_Priority,Ship_Mode
order by  Order_Priority,Ship_Mode desc       
##### EXPLANATION
No, KMS did not appropriately spend shipping costs based on the order of  priority.
They overused delivery trucks, which are best for bulk or non-urgent orders and underused express air, which is meant for urgent deliveries. 
This leadS to an inefficient spending and wasted cost.

