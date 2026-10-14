# Learning Notes: Superstore Excel Project

My daily notes while building this project. I am learning Excel for a data analyst career, so I wrote down what I did, what I found and what was hard.

---

## Day 1: Setup and basic formulas

**What I did**
- Downloaded the Sample Superstore dataset (9,994 rows, 21 columns)
- Opened the CSV in Excel, saved it as `.xlsx` and turned the data into a Table named `Sales`
- Checked the data: no blank cells and no duplicate rows
- Practiced SUM, COUNTIF, SUMIF and IF
- Added a `Result` column to mark each row as Profit or Loss

**Key numbers**
- Total Sales: 2,297,200.86
- Total Profit: 286,397.02
- Orders by Region: West 3,203 | East 2,848 | Central 2,323 | South 1,620
- Profit by Category: Furniture 18,451 | Office Supplies 122,491 | Technology 145,455
- Loss-making rows: 1,871 (Profit rows: 8,123)

**What I noticed**
- Furniture has high sales but the lowest profit
- West has the highest sales

**Struggles**
- My first dataset had no Profit column, so I had to find a different version
- The CSV did not open properly at first, so I used Data > From Text/CSV

---

## Day 2: Cleaning and lookups

**What I did**
- Checked that Order Date is a real date and not text
- Added helper columns to the `Data` sheet: Order Year, Order Month and Clean Name
- Used TRIM and PROPER on customer names. Nothing changed because the data was already clean
- Used a lookup formula to find the customer name from an Order ID

**What I found**
- No extra spaces in customer names
- Each row is one line item, not one order. One order can have many rows

**What I learned**
- XLOOKUP is easier than VLOOKUP because I do not need to count column numbers
- Helper columns like Year and Month make Pivot Tables much easier
- Always check what one row means before counting orders

**Struggles**
- Total Orders: counting rows gave 9,994, but that is line items, not orders. Unique orders are 5,009
- My unique count formula showed 0 at first. I fixed it by checking the calculation setting and using a simpler formula

---

## Day 3: Pivot Tables

**What I did**
- Built Pivot Tables for Region, Category, Sub-Category, Year, Top 10 Customers and Top 10 Products
- Sorted Sub-Category by Profit to find where the business loses money

**What I found**
- Tables, Bookcases and Supplies lose money. Tables is the worst at about -17,725
- Top customer: Sean Miller (about 25,043 in sales)
- Top product: Canon imageCLASS 2200 Advanced Copier (about 61,600 in sales)
- Sales grew from 484,247 in 2014 to 733,215 in 2017, with a small dip in 2015
- West and East earn the most profit

**Question I want to check later**
- Why do Tables lose money? Maybe because of heavy discounts, but I have not proven this yet

**What I learned**
- Sorting a Pivot by Profit quickly shows problem areas

**Struggles**
- In the Top 10 Customers chart the biggest customer showed at the bottom. I fixed it with "Categories in reverse order"
- I wanted to keep Sub-Category and % of Profit in my Pivot, but the chart picked up every field. I made a copy of the Pivot for the chart

---

## Day 4: Dashboard

**What I did**
- Made 3 KPI boxes: Total Sales, Total Profit, Total Orders
- Built 6 charts: Sales and Profit by Region, Profit by Category, Sales Trend by Year, Top 10 Customers, Profit by Sub-Category, Top 10 Products
- Added Slicers for Region, Category and Order Year, and connected them to all the Pivot Tables
- Cleaned up the dashboard: fixed chart titles, removed extra legends and field buttons, added commas to the KPI numbers
- Added a Profit Margin % on the Analysis sheet (12.47%)
- Saved the dashboard as an image with Copy as Picture

**Things to remember**
- Total Orders is 5,009 unique orders. 9,994 is the number of rows
- The KPI boxes use formulas on the table, so they do not change when I click a Slicer. I will fix this in Power BI

**Struggles**
- Excel warned me when I tried to merge cells because merging keeps only the top-left value. I used Center Across Selection instead
- I could not reorder columns inside a Table. Excel does not allow cut and paste there
- Slicers only worked on charts after I connected them in Report Connections

---

## What I want to do next
- Redo the same analysis in SQL
- Rebuild the dashboard in Power BI, with KPI cards that react to filters
- Check if discounts are the reason for losses in Tables and Bookcases
