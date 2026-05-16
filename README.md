# Coffee-Shop-Sales
Shows coffee shop performance across stores, products, times of day, and categories. It highlights total sales, volume, pricing effects, and peak trading periods while surfacing top and underperforming items and locations. It supports operational and merchandising decisions by revealing demand patterns and mix.

SQL QUERY

CREATE TABLE Coffee_Shop_Sales1(
			"transaction_date" Date,
			"transaction_time" time,
			"transaction_qty" smallint,
			"store_id" smallint,
			"store_location" varchar,
			"product_id" smallint,
			"unit_price" real,
			"product_category" varchar,
			"product_type" varchar,
			"product_detail" varchar,
			"Sales" real,
			"Month" varchar);
			

--COPYING PATH

Copy Coffee_Shop_Sales1 from 'C:\Users\HomePC\Documents\DATA ANALYTICS FILES\capstone project\Coffee Shop Sales1.csv' with (format csv, header);


--SQL QUESTIONS AND ANSWERS

--1. Count the number of transactions in the dataset

select count(*) 
from Coffee_Shop_Sales1

--2. Retrieve all records where the sales amount is greater than 100.

select *
from Coffee_Shop_Sales1
where "Sales" > 100

--3. Find the total sales amount for each store

select store_location, sum("Sales") as "Total_sales"
from Coffee_Shop_Sales1
group by store_location

--4. List the unique product categories available in the dataset.

select distinct("product_category")
from Coffee_Shop_Sales1

/*5. Retrieve transactions where the product type is 
'Housewares' and the sales amount is between 50 and 100.*/

select *
from Coffee_Shop_Sales1
where "product_type" = 'Housewares' and "Sales" Between 50 and 100

--6.	Calculate the average sales amount per transaction

select Round(avg("Sales")) as Avg_sales_Amount
from Coffee_Shop_Sales1

--7.Find the store with the highest total sales.

select  store_location, sum("Sales") as "Total_sales"
from Coffee_Shop_Sales1
Group by store_location
order by  "Total_sales" desc
limit 1

/*8.	Count the number of transactions for each product 
category and sort the result by the count in descending order.*/

select "product_category", count(*) as "Num_of_transactions"
from Coffee_Shop_Sales1
group by "product_category"
order by "Num_of_transactions" desc

--9. Find the average sales amount per transaction for each product type.

select "product_type", Round(avg("Sales")) as Avg_sales_Amount
from Coffee_Shop_Sales1
group by "product_type"

--10.Find the total sales amount for each Month.

select "Month", sum("Sales") as "Total_sales"
from Coffee_Shop_Sales1
group by "Month"
