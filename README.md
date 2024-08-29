## Project Objective:
In this project, similar to a real-world scenario, we start by gathering requirements from stakeholders or sales managers. We then proceed to data analysis and visualization by collecting and analyzing the requirements. After this, we choose the right chart for each requirement. This analysis phase is followed by data preparation and understanding our data sources. After creating our data model in Tableau, we start building our charts and dashboards.

Visit the [Tableau Dashboard](https://public.tableau.com/views/SalesPerformance_17249616306820/SalesDashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) to explore the visualizations and insights.

## Introduction:
This user story outlines the specifications for building two dashboards using Tableau to help stakeholders, including sales managers and executives, analyze sales performance and customer data.

## Sales Dashboard | Requirements
### Dashboard Purpose
- The purpose of the sales dashboard is to present an overview of sales metrics and trends in order to analyze year-over-year sales performance and understand sales trends.

### Key Requirements
#### KPI Overview:
- Display a summary of total sales, profits, and quantity for the current year and the previous year.

**Chosen Chart:** BANs (Big Ass Numbers) for each of the KPIs (total sales, profit, and quantity), with a percentage difference between the current and previous year.

#### Sales Trends:
- Present the data for each KPI on a monthly basis for both the current year and the previous year.
- Identify the months with the highest and lowest sales and make them easy to recognize.

**Chosen Chart:** Sparklines to compare monthly trends, with markers for the highest and lowest sales.

#### Product Subcategory Comparison:
- Compare sales performance by different product subcategories for the current year and the previous year.
- Include a comparison of sales with profit.

**Chosen Chart:** Bar-in-Bar charts to compare sales performance across product subcategories.

#### Weekly Trends for Sales & Profit:
- Present weekly sales and profit data for the current year.
- Display the average weekly values.
- Highlight weeks that are above and below the average to draw attention to sales and profit performance.

**Chosen Chart:** Line graphs with a supporting average line to easily identify weeks above or below average, using color differentiation.

## Customer Dashboard | Requirements
### Dashboard Purpose
The customer dashboard aims to provide an overview of customer data, trends, and behaviors. It will help marketing teams and management understand customer segments and improve customer satisfaction.

### Key Requirements
#### KPI Overview:
- Display a summary of the total number of customers, total sales per customer, and total number of orders for the current year and the previous year.

#### Customer Trends:
- Present the data for each KPI on a monthly basis for both the current year and the previous year.
- Identify the months with the highest and lowest sales and make them easy to recognize.

**Chosen Chart:** BANs with Sparklines, similar to the sales dashboard, to track trends.

#### Customer Distribution by Number of Orders:
- Represent the distribution of customers based on the number of orders they have placed to provide insights into customer behavior, loyalty, and engagement.

**Chosen Chart:** Histograms to clearly show the distribution of customers based on order count.

#### Top 10 Customers by Profit:
- Present the top 10 customers who have generated the highest profits for the company.
- Show additional information like rank, number of orders, current sales, current profit, and the last order date.

**Chosen Chart:** A detailed table listing the top 10 customers with supplementary fields.

## Design & Interactivity Requirements
### Dashboard Dynamic
- The dashboard should allow users to check historical data by offering them the flexibility to select any desired year.
- Provide users with the ability to navigate between the dashboards easily.
- Make the charts and graphs interactive, enabling users to filter data using the charts.

### Data Filters
- Allow users to filter data by product information such as category and subcategory, and by location information such as region, state, and city.

## Dataset
The dataset used in this analysis includes a wide range of attributes such as order details, customer information, location, and product details.

### Key Attributes:
- Orders Data: Order Date, Ship Date, Sales, Quantity, Profit
- Location Data: City, State, Region
- Product Data: Category, Sub-Category
- Customer Data: Customer Name

## Parameters
- **Select Year:** A "Select Year" parameter allows the dashboard to be dynamic, adjusting calculated fields based on the selected year (e.g., "CY Sales, PY Sales").

## Calculated Fields
### Sales Dashboard
1. **KPI Sales:**
   - **CY Sales:** Calculates the sales of the "Select Year".
   - **PY Sales:** Calculates the sales of the "Select Year" - 1.
   - **% Diff Sales:** Percentage difference between the current year of sales and the previous year.
   - **Min/Max Sales:** Uses window functions to get the minimum and maximum sales.

2. **KPI Profit:**
   - **CY Profit:** Calculates the profit of the "Select Year".
   - **PY Profit:** Calculates the profit of the "Select Year" - 1.
   - **% Diff Profit:** Percentage difference between the current year of profit and the previous year.
   - **Min/Max Profit:** Uses window functions to get the minimum and maximum profit.

3. **KPI Quantity:**
   - **CY Quantity:** Calculates the quantity of the "Select Year".
   - **PY Quantity:** Calculates the quantity of the "Select Year" - 1.
   - **% Diff Quantity:** Percentage difference between the current year of quantity and the previous year.
   - **Min/Max Quantity:** Uses window functions to get the minimum and maximum quantity.

4. **Subcategory Comparison:**
   - **KPI Sales Less PY:** Identifies which subcategory sales of the current year are less than the previous year, making it easier to find issues.

5. **Weekly Trends:**
   - **KPI Sales AVG:** Uses window functions to calculate the average sales.
   - **KPI Profit AVG:** Uses window functions to calculate the average profit.

### Customer Dashboard
1. **KPI Customers:**
   - **CY Customers:** Calculates the customers of the "Select Year" who have placed at least one order.
   - **PY Customers:** Calculates the customers of the "Select Year" - 1 who have placed at least one order.
   - **% Diff Customers:** Percentage difference between the current year’s number of customers and the previous year.
   - **Min/Max Customers:** Uses window functions to get the minimum and maximum number of customers.

2. **KPI Sales per Customer:**
   - **CY Sales per Customer:** Calculates the CY Sales divided by CY Customers of the "Select Year".
   - **PY Sales per Customer:** Calculates the CY Sales divided by CY Customers of the "Select Year" - 1.
   - **% Diff Sales per Customer:** Percentage difference between the current year and the previous year.
   - **Min/Max Sales per Customer:** Uses window functions to get the minimum and maximum sales per customer.

3. **KPI Orders:**
   - **CY Orders:** Calculates the orders of the "Select Year".
   - **PY Orders:** Calculates the orders of the "Select Year" - 1.
   - **% Diff Quantity:** Percentage difference between the current year’s orders and the previous year.
   - **Min/Max Quantity:** Uses window functions to get the minimum and maximum orders.

4. **Customer Distribution:**
   - **Nr. of Orders per Customer:** Uses LOD Expressions to calculate the number of CY orders for each CY customer.

