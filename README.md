# Sales-Insight-Data-Analysis-Project

## Objective
To get the sales insight that are not visible before for the sales department of a computer hardware company to support them in decision making and automate it in order to reduce manual time involved in data gathering.

## Problem Statement
This project is based on the case study of a computer hardware business which is facing challenges in dynamically changing market. Sales director of the company decides to invest in data analysis project and wants to get a power BI dashboard that can give him real time sales insights in order to know the actual causes for not generating the expected output by the company. So, it is required to analyze the sales data of the company from each and every aspect and make it visible for ease of decision making by getting answers of some questions like which market, in which year, which customer, what type of product,how much sales quantity, revenue and profit etc.

## Process
So in order to collect all these infomation some tools were used for analyzing all the data. Used MySQL database and analyzed it, performed ETL and data cleaning operations in Power Query Editor, performed data modelling, used DAX (Data Analysis Expressions) and built Power BI dashboard in Microsoft Power BI Desktop to get real time sales insight showing most possible and important aspects for the sales director of the company.

Here is the process flow:


![Screenshot (97)](https://user-images.githubusercontent.com/90664702/137720291-47e20c71-30a9-44a0-bd9e-01e64bc5ead2.png)





## Data Analysis using MySQL

![images3](https://user-images.githubusercontent.com/90664702/139130740-1535dd46-a486-4f6a-84e2-6fd0360f41dd.png)


## To show all customer records:

SELECT * FROM customers;

## To show total number of customers:

SELECT count(*) FROM customers;

## To show transactions for Mumbai market (Mumbai market code: Mark002):

SELECT * FROM transactions where market_code='Mark002';

## To show codes of distinct products that were sold in chennai:

SELECT distinct product_code FROM transactions where market_code='Mark001';

## To show transactions where currency is in US dollars:

SELECT * from transactions where currency="USD"

## To show transactions in 2020 join by date table:

SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

## To show total revenue in year 2020:

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

## To show total revenue in year 2020, April Month:

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="April" and (transactions.currency="INR\r" or transactions.currency="USD\r");

## To show total revenue in year 2018 in Delhi NCR:

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2018 and transactions.market_code="Mark004";




## Data Analysis using PowerBI

![PowerBI-Logo](https://user-images.githubusercontent.com/90664702/139130315-1dccb1c4-0926-46ba-a4b0-6d56f52b03f8.png)




## Other operations in Power BI are-

1. Removed bottom rows from sales markets table using   👉 Remove Rows
2. Removed -1 & 0 from sales_amount column in sales transactions table 

## DAX functions used

1. To create Base Measure Profit Margin 👉  Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)
3. To create Base Measure Profit Margin Contribution % 👉  Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))
4. To create Base Measure Revenue 👉  Revenue = SUM('sales transactions'[Norm_sales_amount])
5. To create Base Measure Revenue Contribution % 👉  Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))




## Final Result


![Screenshot (91)](https://user-images.githubusercontent.com/90664702/139132191-89f8bd09-64a1-446d-852c-5650b1cea0fe.png)

👉 An automated Power BI dashboard was created providing sales insights in a very less time from all necessary aspects in order to help the sales director in data driven decision making.


👉 Sales department began to make better decisions based on data and saved almost 10% cost of total spend.








