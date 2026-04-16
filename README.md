# Atliq-Hardware-sales-insights
Finding the sales analysis of AtliQ Technologies using Power BI


Table of contents
Problem statement
Solution
Data
Task
Data Cleaning
Finding Profit Margin, Sales Quantity and Revenue made in each year/month
Analyzing top 5 customers and product type by revenue
Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each customer
Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each Market
Finding the Revenue trend by years
Analyzing Revenue contribution by customer type
Additional Tasks
Final Report
Insights

Tools used: Power BI, MySQL

Problem statement
AtliQ Hardware, with multiple branches across India, provides computer hardware and peripheral manufacturers to its clients. The sales director is encountering difficulties in comprehending the company’s current issues and performance, as sales are decreasing below expectations.

Whenever the director seeks updates from regional managers regarding sales and the market, they tend to sugarcoat the truth and send excessive Excel files, adding to the director’s frustration. The frustration is understandable, as humans often find it challenging to comprehend numbers from Excel files.

Solution
As a data analyst, a solution to address the sales director’s problem at AtliQ hardware would be to BI dashboards that can help with data visualization and analysis. The sales director can use dashboard that pulls in data from various sources, including the company’s sales data, market trends, and regional manager reports. With the dashboard, the sales director can easily see the current state of the business, identify problem areas, and make data-driven decisions.





By having a clear, visual representation of the data, the sales director can also avoid relying on Excel files and sugar-coated reports from regional managers, which can lead to misunderstandings and frustration.

Data
We are provided with the SQL dataset which contains customers, date, transactions, markets, and products tables. We need to provide insights using the data from those tables
<img width="1147" height="649" alt="Screenshot 2026-04-06 121131" src="https://github.com/user-attachments/assets/7192194b-7b9d-41a0-b08b-189b254421ee" />


Task
Finding Profit Margin, Sales Quantity and Revenue made in each year/month
Analyzing top 5 customers and product by revenue
Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each customer
Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each Market
Finding the Revenue trend by years
Analyzing Revenue contribution by customer type
Data Cleaning
Removed zones which were left blank in market table
Removed sales amount which were less than 0 in sales transaction table
Created new table called Normalized sales price to convert the USD price to INR price in sales transaction table
Removed duplicates from currency column in sales transaction table
Finding Profit Margin, Sales Quantity and Revenue made in each year/month
For all DAX calculations, I’ve created a separate table called as Base Measure and added measures in it.

Sales quantity = SUM('sales transactions'[sales_qty])
---------------------------------------------------------------------------------------
Revenue = SUM('sales transactions'[Normalized_sales_price])
---------------------------------------------------------------------------------------
Total Profit Margin = SUM('sales transactions'[profit_margin])
---------------------------------------------------------------------------------------
Profit margin % = DIVIDE([Total Profit Margin],[Revenue],0)
---------------------------------------------------------------------------------------
Revenue Margin Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales customers'),ALL('sales markets'), ALL('sales products')))
---------------------------------------------------------------------------------------
Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales customers'),ALL('sales markets'), ALL('sales products')))
<img width="215" height="277" alt="image" src="https://github.com/user-attachments/assets/99e9565f-8510-4041-9757-9995d293517c" />

I’ve used Card chart to visualize the values

<img width="418" height="87" alt="image" src="https://github.com/user-attachments/assets/d967d060-43fa-47f5-bc58-5e6f744cccb3" />


To display the top 5 customers, I’ve added stacked bar chart and used filtering type Top N to display in chart with x-axis to be revenue and y-axis to be customer and product code


Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each customer
Added a table to display Revenue Margin Contribution, Profit Margin Contribution and Profit % by each customer


Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each Market
Added stack bar chart to display Revenue Margin Contribution, Profit Margin Contribution and Profit % by each Market separately


Finding the Revenue trend by years
Line chart is used to analyze the revenue trend by years with x-axis as date and y-axis with revenue


Analyzing Revenue contribution by customer type
Used donut chart to get insights on revenue contribution by customer type with legend to be customer type and value as revenue


Additional Tasks
Added a horizontal tiles to find the insights for each year and each month.
Press enter or click to view image in full size

Added line and clustered column chart to analyze the profit margin % in current year with last year

Added slicer with value to be profit margin %. So whenever we have market or zones less than target value %, it’ll be indicated in different color

Added page navigators to navigate easily between pages

Final Report
Press enter or click to view image in full size

Press enter or click to view image in full size

Press enter or click to view image in full size

Insights
There is a decrease in the revenue trend from 2017–2020
Delhi NCR is the highest contributor in Revenue and Sales quantity by Market
E-commerce gives the highest revenue contribution by customer type
Surat gives highest profit % by market
Central Market contributes to more Revenue
