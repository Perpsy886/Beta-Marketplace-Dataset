# Beta Marketplace Dataset


## Project Overview
This repository presents a comprehensive analysis of the Beta Marketplace Sales Dataset, focusing on key business dimensions such as products, customers, regions, and financial metrics. The core aim is to extract actionable insights that can support Beta Marketplace in streamlining operations, enhancing customer satisfaction, boosting profitability, and achieving a deeper understanding of its overall business performance.


### Dataset Sources & Description
Primary Dataset: Beta Marketplace Sales Dataset.csv
This dataset contains granular sales transaction records, including details on product categories, customer demographics, pricing, regional sales distribution, and associated costs.


### Objectives
The analysis is guided by the following key objectives:
- Evaluate Product Performance: Identify the most and least successful products and subcategories based on revenue, profit, and quantity sold.
- Understand Customer Behavior: Segment customers by gender, region, and purchase trends to assess lifetime value and buying preferences.
- Analyze Financial Health: Review revenue patterns, cost structures, and profitability on both monthly and daily bases to track business performance.
- Examine Regional Distribution: Explore how product sales vary across regions and states.
- Uncover Growth Opportunities: Identify potential areas for optimizing inventory, targeting marketing campaigns, and improving financial strategy.


### Tools & Technology
1. Data Extraction & Analysis	Azure Data Studio
2. Data Cleaning & Transformation	Microsoft Excel
3. Data Visualization	Power BI
4. Documentation & Reporting	GitHub Markdown

### Data Preparation & Cleaning
In the initial data preparation phase, I performed the following Task;

1. Handling Missing Values: Identifying and addressing any missing entries in critical columns (e.g., revenue, quantity).
2. Correcting Data Types: Ensuring all columns are in their appropriate data types (e.g., numerical values are not stored as strings).
3. Removing Duplicates: Eliminating any duplicate records that might skew the analysis.
4. Standardizing Formats: Ensuring consistent formatting for categorical data (e.g., "Male" vs. "male").
5. Outlier Detection: Identifying and deciding how to handle extreme values that could impact statistical measures.


### 🔍 Exploratory Data Analysis (EDA)
EDA was conducted to understand the underlying patterns and relationships within the data. This included:

1. Summary Statistics: Calculating mean, median, mode, standard deviation for numerical columns.
2. Distribution Analysis: Visualizing the distribution of key metrics (e.g., revenue, profit) using histograms and box plots.
3. Categorical Analysis: Examining the distribution of categorical variables (e.g., gender, product categories) using bar charts and pie charts.
4. Trend Analysis: Visualizing revenue and cost trends over time (monthly, daily).
5. Correlation Analysis: Exploring relationships between different variables, such as profit vs. revenue by product category.


### Data Analysis
```
-- CTE Query 1: Calculate Aggregated Profit and Revenue by Product Category
-- This CTE prepares the data by summing up the total revenue and total profit
-- for each product category. This aggregated data can then be used to
-- analyze the relationship between profit and revenue at a category level.
WITH CategoryPerformance AS (
    SELECT
        ProductCategory,
        SUM(TotalRevenue) AS TotalCategoryRevenue,
        SUM(TotalProfit) AS TotalCategoryProfit
    FROM
        SalesData -- Assuming 'SalesData' is your main sales table
    GROUP BY
        ProductCategory
)
-- You can then select from this CTE to perform further analysis or visualization
SELECT
    ProductCategory,
    TotalCategoryRevenue,
    TotalCategoryProfit
FROM
    CategoryPerformance;

  SQL 2 
-- Window Query: Calculate Running Total of Revenue by Product Category
-- This query uses a window function to calculate the running total of revenue
-- for each product category, ordered by date. This can be useful for
-- visualizing cumulative performance and understanding how different
-- categories contribute to overall revenue over time.
SELECT
    SaleDate,
    ProductCategory,
    TotalRevenue,
    SUM(TotalRevenue) OVER (PARTITION BY ProductCategory ORDER BY SaleDate) AS RunningCategoryRevenue
FROM
    SalesData
ORDER BY
    ProductCategory, SaleDate;
```


### 📌 Key Findings
---

### 🛍️ Product Performance
- The unit cost across products is consistently lower than the unit price, indicating healthy profit margins overall.
- Products such as Juice, Dishwashers, and Soft Drinks display strong profitability due to the wide gap between their cost and selling price.
- The Household, Beverages, and Fashion categories generated the highest total revenue—₦35,630,869.
- Some products within profitable categories (e.g., Vegetable Oil) have thin profit margins, likely due to high production costs, lower price points, or minimal sales volume.

### 👥 Customer Insights
- High Lifetime Value (LTV) customers such as CUST75107, CUST3292, CUST48740, and CUST13118 should be prioritized in targeted marketing campaigns.
- Repeat Purchase Rate is 0%, indicating an urgent need for customer retention strategies.
- Gender distribution is nearly even, with 49.7% Male and 50.3% Female customers.
- Top customer locations include: FCT, Kwara, Taraba, Bauchi, and Katsina.

### 🌍 Regional Distribution
- Product unit price variation across regions suggests differences in value perception, affordability, or distribution costs.
- North West and North Central states show lower unit prices but generate higher total revenue, possibly due to greater sales volume.
- South West and South East regions underperform in revenue, despite being economically significant zones in Nigeria—warranting further investigation.

### 💵 Financial Overview
- Revenue exhibits seasonal fluctuation, with noticeable peaks in November, December, and on Sundays.
- There’s a strong positive correlation between profit and revenue across product categories, reinforcing the value of volume-driven sales.


### ✅ Recommendations

- Optimize pricing for underperforming products by investigating the bottom five in terms of profit. Assess if high unit costs, excessive discounts, or inefficiencies are driving margins down.
- Double down on top earners like Juice, Dishwashers, and Detergents. Prioritize these in inventory stocking, promotions, and advertising. Use cross-selling strategies to maximize value.
- Investigate why the South West and South East regions are underperforming despite economic viability. Review pricing models in regions with lower unit prices to identify potential margin improvements.
- Launch targeted campaigns around June to counter mid-year slumps in sales.
- Explore behavioral patterns behind seasonal peaks and dips, especially in the latter half of the year.
- Plan inventory and workforce around peak demand months like January, September, and October for better operational efficiency.

  
### ⚠️ Limitations
- Dataset is limited to a single year; no long-term trends.
- No return/refund data available.
- Customer income or age data missing, limiting demographic analysis.
- Lack of business context: Certain insights (e.g., 0% repeat rate) cannot be fully explained without more background information or additional variables.


### 🧾 Conclusion
This analysis offers a thorough view of Beta Marketplace’s operational performance across products, customers, regions, and financial outcomes. The insights can inform strategic decisions in pricing, inventory management, customer engagement, and sales planning. Addressing challenges like low repeat rates and high-cost products will be critical to sustaining long-term growth.



📚 References
1. Kaggle – Data Cleaning & EDA Guide
2. Towards Data Science – Sales Analysis Tutorial
3. Microsoft Learn – Analyze Data with Power BI
4. Fundamentals with Digitech – [Beta Marketplace Data Source](https://work.betamarketplace.com/)







