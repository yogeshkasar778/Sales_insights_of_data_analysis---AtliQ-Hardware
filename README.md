#  Project : Sales Insights of Data Analysis-AtliQ Hardware

![Sales insights AtliQ](https://user-images.githubusercontent.com/118357991/230730818-34393de8-2b5c-46da-83f1-be293b0107b4.png)

## Problem Statement :

In this project performed India based AtliQ hardware company sales insights - A Data Analysis project. 
Developed ETL mappings using SQL to extract the data from unstructured data and transformed it to the staging area to conduct data cleaning and design star schema data model on Power BI. Developed a Power BI dashboard to perform analysis, producing quantitative visualizations in Power BI to draw valuable insights based on different parameters affecting the company performance year on year and further provide business solutions.

AtliQ Hardware is a company which supplies computer hardware and peripherals to many of clients such as excel stores, surge stories across India. AtliQ Hardware head office is situated in Delhi, India and they have many regional office through out the India.

Sales director for this company is facing a lot of challenges is this the market is growing dynamically and sales director is facing issue in terms of tracking the sales in this dynamical growth market and he is having issues with growth of this bussiness, as overall sales was declining. He has regional manager for North India, South and Central India. Whenever he wants to get insights of thses region he would call these people and on the phone regional manager give some insights to him that this was the sales last quarter and we are going to grow by this much in the next quarter.

The problem was that all thses thing happening is verbal and these was mo proof with facts that how his business is affected and which made him frustraed as he can see that overall sales is declining but when he can ask regional manager, he is not getting complete picture of this bussiness and when he and this AtliQ hardware is big business. so to see insights clearly. and he will get proper insights anbd can take data driven decision to increase sales of hos company.
All he wants is a simple data visualization tool which he can access on daily basis. By using such tools and technology one can make data driven decisiions which helps to increase the sales of the company. So, In this projects we will help a company make its own sales related dashboard using power BI.

## Data Discovery :

- #### Project Planning using AIMS Grid -

  It is a project management tool which consists of four components-
  
     - Purpose - (What to do exactly)
     - Stackholder - (Who will be involved)
     - End result - (What do you want to achieve)
     - Success Criteria - (Cost optimization and time save)
 - #### AIMS Grid -
     **1. Purpose :-** To unlock sales insights that are not visible before for the sales them for decision support and automate them to reduced manual time spent in data gathering.
     
     **2. Stakeholders :-** 
     - Sales Director
     - Marketing Team 
     - Customer Service Team
     - Data and Analytics Team
     - IT 
     
     **3. End result :-** An automated dashboard providing quick and latest sights in order to support Data driven decision making.
     
     **4. Success Criteria :-**
     - Dahboard uncovering sales order insights with latest data available
     - Sales team able to take better decisions and prove 10% cost saving of total spend.
     - Sales analysis stop data gathering manually in order to save 20% business time andreinvest it value added activity.
   
- #### Flowchart of project execution -

  ![1_khhcniAryBdmmfJt0Zk0Lg](https://user-images.githubusercontent.com/118357991/231545034-7f6cc437-5683-44f1-92df-a671540ccae9.jpg)

   

## Data Analysis using MySQL :

Completed the Data discovery and then used mySQL for data analysis.

SQL database dump is in db_dump.sql file above. Download db_dump.sql file to your local computer

- Importing Data to MySQL workbench

![Screenshot (61)](https://user-images.githubusercontent.com/118357991/230953941-d5ce7cde-26ec-47fe-acb1-e499f9028da9.png) 

The import of data is done from an already existing MySQL file. This file has to be loaded into MySQL workbench for further data analysis. 

- Analysis of data by looking into different tables and reflecting garbage values

   We can see that garbage value that the table market cantains certain values which are incorrect.
   
     `SELECT * FROM sales.market;`
     
   And then we can check that transacation table we can see that ceratin negative value in amount which is not possible. and we can see that certain transactions are      in USD. Hence, filtration of that is also needed by converting into INR.
     
     `SELECT * FROM sales.transactions;`
     
 - Analysis of different SQL statement on data base
     
   1.To find of all customers records 
     
     `SELECT * FROM sales.customers;`
      
   2.To find total number of customers 
     
     `SELECT count(*) From sales.customers;`

   3.To find transactions for Chennai market (market code for chennai is Mark001
     
      `SELECT * FROM sales.transactions where market_code='Mark001';`

   4.To find distrinct product codes that were sold in chennai
     
      `SELECT distinct product_code FROM sales.transactions where market_code='Mark001';`

   5.To find transactions for Chennai market (market code for chennai is Mark002
     
      `SELECT * FROM sales.transactions where market_code='Mark002';`

   6.To find distrinct product codes that were sold in mumbai
     
      `SELECT distinct product_code FROM sales.transactions where market_code='Mark002';`
      
   7.To find transactions where currency is US dollars
     
      `SELECT * from sales.transactions where currency="USD";` 
      
   8.To find transactions in 2020 join by date table
     
      `SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020;`  

   8.To find transactions in 2019 join by date table
     
      `SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019;`  

   9.To find total revenue in year 2020,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";` 
      
   10.To find total revenue in year 2019,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";`       

   11.To find total revenue in year 2020, January Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   12.To find total revenue in year 2020, February Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   13.To find total revenue in year 2019, January Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   14.To find total revenue in year 2019, February Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   15.To find total revenue in year 2020 in Chennai
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark001";` 

   16.To find total revenue in year 2020 in Mumbai
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark002";` 

Similarly, if we want different of any other particular city the market code of that city is used on the mysql workbench.

