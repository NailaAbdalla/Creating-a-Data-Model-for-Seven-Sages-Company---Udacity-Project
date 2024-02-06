# Creating a Data Model for Seven Sages Company - Udacity Project
 First project in Data Analysis and Visualization--Power BI
# Project Overview
In this project, you'll create a data model and Power BI report for Seven Sages Tea Company (SSTC) that combines information from all over the company. Your data model will make it possible for the company's CFO to quickly review and analyze which tea beverages sell well and which ones generate the highest profitability.<br>

At the end, you will have applied the key concepts of this course to combine and centralize data that was previously siloed, solving a very common issue facing many companies. More importantly, you'll have a solid foundation to build on when it comes to more complex reporting visualization demands, advanced DAX requirements, or larger data models. No matter how large the data models get as your career progresses, the core principles remain the same.<br>
# Scenario
You're a junior BI developer who's just been hired by the Seven Sages Tea Company (SSTC) up near Seattle, Washington (USA).<br>

It's a small, but growing company, and the CFO is eager to get some help translating all the disjointed sales files and product records into something usable so that they can help the owners make sense of what is generating not only sales but profitability.<br>

It's common knowledge that the flagship tea beverage, Bamboo Grove Tea is the company's biggest seller.<br>

But what about the rest?<br>

The way the data is collected in-house, they are not even sure whether all the products are generating a profit at this stage.<br>
Seven Sages teas are sold in Washington State (USD) and British Columbia (CAD), so there's a currency consideration as well.<br>
The company runs on a fiscal calendar. So make sure you factor that into your efforts when you build the model.<br>
# Main Steps
Here are the main steps. We'll go over each of these in more detail on the pages that follow.<br>

# Source files.<br>
1-Download and familiarize yourself with the source files provided by SSTC.<br>
2-Sketch the data model. Sketch out the data model you intend to build.<br>
3-Use Get Data. Use Get Data to load the data from the starter materials into Power BI.<br>
4-Structure, combine, and clean the data. Clean and format your data so that it will work well in your data model.<br>
5-Create your date table. Create a date table to support time intelligence.<br>
6-Build relationships between your tables. Build a relationship from each dimension to the relevant key on the fact table.<br>
7-Write your measures. To satisfy the CFO's requirements, we will need to write six measures—to calculate Sales, Cost of Sales and Gross Profit Margin in two different currencies.<br>
8-Create a report. Build a basic visual report to display your findings.<br>
# Get Started <br>
1- ETL as the first thing to do here ( Extract transform and load the datasets). <br>
2- Get familiar with dataset to sketch the data model.<br>
# Ask yourself:

Which of the data sources will work best as my central fact table?<br>
Are there any repeating columns that indicate I can or should append similar data into a cohesive singular table?<br>
Are there any tables that might function as separate dimensions but would perform better merged as a single table?<br>
If there isn't an obvious join between two tables, is there a logical way I can build one to get access to necessary data?<br>
3-Structure, Combine, and Clean the Data <br>
4-Create dynamic Date Table. <br>
creating a dynamic date table that automatically updates to fit new data is an excellent way to avoid future errors and headaches. You'll want to create a continuous table that covers each full calendar year in the sales data set (starting on January 1st and ending on December 31st. In addition, the table should include:<br>

Calendar month name and number. <br>
Calendar year.<br>
Fiscal period.<br>
Fiscal year.<br>
Fiscal quarter -Quarter - FY (e.g., Q1 - FY2021)<br>
5-Build Relationships Between Tables. <br>
6-Write some Measures to calculate Sales, Cost of Sales and Gross Profit Margin in two different currencies.<br>
7-Create a Report.<br>
# The Report <br>
# Sales and GPM insights <br>
![reportt](https://github.com/NailaAbdalla/Creating-a-Data-Model-for-Seven-Sages-Company---Udacity-Project/assets/151609042/f5da9c73-2388-4e7b-bc47-072f68d0a065) <br>
# Gross Profit and unit sale <br>
![reporttt](https://github.com/NailaAbdalla/Creating-a-Data-Model-for-Seven-Sages-Company---Udacity-Project/assets/151609042/1f7ce98c-c9ab-4abc-82f2-7e0db719fe31) <br>
# The measures <br>
1- Calculating total of the amount sold. <br>  <br>
      `amount sold = SUMX('Monthly Sales',[Qty]*RELATED('Product'[Serving Amount])) `<br> <br>
2- Costs in USD(United State Dollars $). <br> <br>
     `  cost in USD = SUMX('Monthly Sales',[Qty]*RELATED('Product'[Per Unit Cost to make])*RELATED('USD-CAD Exchange Rates'[USD]))` <br> <br>
3- Costs In CAD( Canadian Dollars $) <br> <br>
`cost in CAD = SUMX('Monthly Sales',[Qty]*RELATED('Product'[Per Unit Cost to make])*RELATED('USD-CAD Exchange Rates'[CAD]))` <br> <br>
4-Gross Profit Margin in USD. <br>   <br>
`GPM (USD) = CALCULATE(([Sales (USD)]-[cost in USD])/[Sales (USD)])` <br> <br>
5-Gross profit in CAD. <br> <br>
`Gross profit in CAD = ([Sales in CAD]-[cost in CAD])` <br> <br>
6-Gross profit in USD <br> <br>
`Gross profit in USD = ([Sales (USD)]-[cost in USD])` <br> <br>
7-PCT Gross Profit by Product.<br> <br>
`PCT Gross Profit by Product = ([Gross profit in USD]+[Gross profit in CAD])/[Total Gross Profit]` <br> <br>
8-PCT Unit sales by Product <br> <br>
`PCT Unit sales by Product = ([Sales (USD)]+[Sales in CAD])/[Total sales]` <br> <br>
9-Sales (USD) <br> <br>
`Sales (USD) = SUMX('Monthly Sales',[Qty]*RELATED('Product'[Per Unit Sales price])*RELATED('USD-CAD Exchange Rates'[USD]))` <br> <br>
10-Sales in CAD <br> <br>
`Sales in CAD = SUMX('Monthly Sales',[Qty]*RELATED('USD-CAD Exchange Rates'[CAD])*RELATED('Product'[Per Unit Sales price]))` <br> <br>
11-Total Gross Profit <br> <br>
`Total Gross Profit = CALCULATE([Gross profit in USD]+[Gross profit in CAD],ALL())` <br> <br>
12-Total sales <br> <br>
```Total sales = CALCULATE([Sales (USD)]+[Sales in CAD],ALL())``` <br> <br>
   
 


