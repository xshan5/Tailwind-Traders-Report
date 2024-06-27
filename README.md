# Tailwind Traders Capstone Project


## Overview

Your tasks in these exercises were to:

- Prepare Sales Excel data.

- Configure data sources.

- Design and develop the data model

- Configure aggregations using DAX.

- Create sales and profit reports.

- Create an executive dashboard.


## Exercise 1: Prepare the Sales Excel data

### Step 1: Prepare Sales Data:

   Open Tailwind Traders Sales.xlsx.
- Calculate Gross Revenue
- Calculate Total Tax
- Calculate Net Revenue
- Configure Data Sources in Power BI

### Step 2: Load Tailwind Traders Sales.xlsx.
- Assign data types.
- Validate data integrity.
- Design and Develop Data Model

### Step 3: Create a Calendar table with DAX.

- Configure the Calendar table
- Select New Table and add the following DAX code to create a new Calendar table:

```
CalendarTable = 
ADDCOLUMNS(
CALENDAR(DATE(2020, 1, 1), DATE(2023, 12, 31)),
"Year", YEAR([Date]),
"Month Number", MONTH([Date]),
"Month", FORMAT([Date], "MMMM"),
"Quarter", QUARTER([Date]),
"Weekday", WEEKDAY([Date]),
"Day", DAY([Date])
)
```

### Step 4: Create Sales in USD Calculated Table

Select New Table and add the following DAX code to create a new calculated table:

```
Sales in USD = 
ADDCOLUMNS(
    Sales,
    "Country Name", RELATED(Countries[Country]),
    "Exchange Rate", RELATED('Exchange Data'[Exchange Rate]),
    "Exchange Currency", RELATED('Exchange Data'[Exchange Currency]),
    "Gross Revenue USD", [Gross Revenue] * RELATED('Exchange Data'[Exchange Rate]),
    "Net Revenue USD", [Net Revenue] * RELATED('Exchange Data'[Exchange Rate]),
    "Total Tax USD", [Total Tax] * RELATED('Exchange Data'[Exchange Rate])
)
```
### Step 5: Load Currency Exchange data
Select Get Data, choose Python script, and then paste the following code into the script window in Power BI:


![nkN-tX3jREaYkeFU2nB4wg_ef72f6716b9c44b480ecaa18996edde1_image (1)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/aa93f8f7-335e-44f8-a027-bf2708014df9)

## Exercise 2: Design and develop the data model

![Screenshot (5)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/f99ca691-c153-4d7a-a813-f484f96de451)




           
  

## Exercise 3: Configure aggregations using DAX

### Step 1: Calculate Yearly Profit margin

This calculation divides the Gross Revenue by the Net Revenue, and shows how much money is kept as profit from sales after costs. This measure provides an overarching view of Tailwind Traders’ financial efficiency throughout the year and is a key indicator of the company's financial health.

![Screenshot (1)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/8ee72eab-381c-4218-80b6-6dc21466b019)



### Step 2: Calculate Quarterly Profit

This calculation isolates the profit made in each quarter by using a time intelligence function, which filters the profit to each respective quarter. This data provides actionable insights for short-term planning and strategy.

![Screenshot (3)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/0630faf8-4cc0-4883-8421-3e690d057f65)

### Step 3: Calculate Year-to-Date Profit

This measure accumulates the profit from the first day of the fiscal year to the current date, providing a running total of Tailwind Traders' profitability. This step provides a real-time snapshot of the company’s financial trajectory, allowing for comparison against the same period in previous years or projected targets.

![Screenshot (2)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/2f0103a6-6c8c-4a1b-a6d9-14e793d46824)


### Step 4: Calculate Median Sales

The median is a statistical measure that indicates the middle value in a set of numbers, which, in this case, represents sales volumes. Using the MEDIAN function on Gross Revenue identifies the sales value at the center of the dataset.

![Screenshot (4)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/82984276-9df4-46a7-87c6-53aba5e1f421)


## Exercise 4: Create a Sales report
- Step 1: Create a bar chart for loyalty points by country

- Step 2: Create a column chart for Quantity Sold by Product

- Step 3: Create a pie chart for median sales distribution by country

- Step 4: Create a line chart for median sales over time

- Step 5: Create cards that visualize the following measures:

     a) Stock.

     b) Quantity Purchased.

     c) Median Sales.

- Step 6: Create a slicer that displays the Country Name data from the Sales in USD table.

### Sales Report Snapshot

![Screenshot (7)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/8eb49734-7a59-4494-987a-991358cec584)


## Exercise 5: Create a Profit report

- Step 1: Create a bar chart for Net Revenue by Product

- Step 2: Create a donut chart for Yearly Profit Margin by Country

- Step 3: Create an area chart for Yearly Profit Margin over Time

- Step 4: Create cards to visualize your measures

  a) YTD Profit

  b) Net Revenue USD

- Step 5: Create a KPI for Gross Revenue USD

- Step 6: Create a slicer that displays the Datedata from the CalendarTable table.

## Profit report Snapshot
![Screenshot (8)](https://github.com/xshan5/Tailwind-Traders-Report/assets/140767371/1f1ce0ea-0234-4b89-9b8a-7edee749dff1)

