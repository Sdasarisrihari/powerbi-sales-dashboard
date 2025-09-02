# Sales Performance Dashboard

An end-to-end data analytics project involving ETL, data modeling, and the development of an interactive Power BI dashboard to analyze sales performance across European markets. This project transformed raw transactional data into a strategic asset for business intelligence.

## 📊 Project Files & Access

This project was developed using **Power BI Desktop**. The interactive dashboard is contained within the `.pbix` file.

*   **Download the Power BI File:** [SN_Crop_Dashboard.pbix](https://mytrine-my.sharepoint.com/:u:/r/personal/sdasari241_my_trine_edu/Documents/SN_Crop_Dashboard.pbix?csf=1&web=1&e=JLKC2P)
    *   *Requires Microsoft Power BI Desktop to open and view interactivity.*


## 🎯 Business Objectives & Value Delivered

This dashboard was designed to answer critical business questions and provide actionable insights for the sales and leadership teams:

*   **Performance Tracking:** Monitor KPIs like Total Sales, Profit, and Profit Margin % over time to assess business health.
*   **Geographic Analysis:** Identify top-performing countries and cities to optimize regional strategy and resource allocation.
*   **Product Intelligence:** Analyze profitability and sales across product categories and sub-categories to inform inventory and marketing decisions.
*   **Customer Segmentation:** Understand purchasing behavior by customer segment (Consumer, Corporate, Home Office) for targeted campaigns.
*   **Operational Efficiency:** Evaluate the cost and profitability impact of different Ship Modes.

## 🛠️ Technical Deep Dive: Implementation & Process

### 1. Data Extraction & Transformation (ETL with Power Query)

*   **Data Source:** Connected to a raw `Orders` table from an Excel workbook (`Power BI Dataset.xlsx`).
*   **Data Cleansing:** Performed data quality checks, handled null values, and ensured consistent formatting for fields like `Order Date`, `City`, and `Country`.
*   **Data Enrichment:**
    *   Extracted date attributes (Year, Month, Quarter) from the `Order Date` column to enable time intelligence analysis.
    *   Created conditional columns to categorize or flag data as needed for analysis.
*   **M Language:** Authored **Power Query (M)** scripts to automate the data preparation and loading process, ensuring reproducibility.

### 2. Data Modeling

*   **Schema Design:** Built a **Star Schema** for optimal performance and simplicity.
    *   **Fact Table:** `Sales` (Measures: Sales, Profit, Cost, Quantity)
    *   **Dimension Tables:** `Date`, `Product`, `Customer`, `Geography`, `Ship Mode` (connected to the fact table via relationships).
*   **Relationships:** Established and managed **one-to-many** relationships between dimension tables and the fact table, enforcing referential integrity and enabling accurate filtering across the model.

### 3. DAX & Measure Creation

Authored **Data Analysis Expressions (DAX)** to create calculated columns and, more importantly, robust performance measures.

**Key Performance Indicators (KPIs):**
```dax
Total Sales = SUM(Sales[Sales])
Total Profit = SUM(Sales[Profit])
Total Cost = [Total Sales] - [Total Profit] // Calculated from core measures
Total Quantity = SUM(Sales[Quantity])
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
``` 

## 📊 Key Business Insights Derived from DAX

*   **Profitability Analysis:** The `Profit Margin %` measure is the core metric for assessing product and regional health, clearly showing which areas are most efficient at generating profit from revenue.
*   **Performance Tracking:** The `Total Sales` and `Total Profit` measures provide the foundational numbers for all time-series analysis (e.g., Year-over-Year growth).
*   **Cost Management:** The `Total Cost` measure, calculated indirectly from sales and profit, helps the business understand its expenditure structure relative to income.

## 📈 How to Use the Dashboard

1.  **Global Overview:** Start with the summary cards at the top to get a high-level sense of overall performance (Total Sales, Profit, and Margin).
2.  **Filter for Focus:** Use the slicers on the right (Year, Country, Ship Mode) to isolate specific segments of the business.
3.  **Identify Trends:** Look at the "Sales and Profit by Month" line chart to identify seasonal patterns or growth trends.
4.  **Drill into Details:** Use the tooltip features or click on chart elements (e.g., a specific country on the map) to cross-filter the entire report and see contributing factors.
5.  **Analyze Geography:** The map visual quickly highlights the top-performing countries within Europe.
6.  **Evaluate Products:** The bar charts for Product Category and Sub-Category show which items are driving the most revenue and profit.

## 🚀 Value for Stakeholders

*   **For Sales Directors:** Quickly identify top and bottom-performing regions to allocate resources and tailor sales strategies effectively.
*   **For Marketing Teams:** Understand which customer segments and product categories are most profitable, allowing for more targeted and efficient marketing campaigns.
*   **For Logistics/Operations:** Analyze the cost implications of different `Ship Modes` to optimize the supply chain for better profitability.
*   **For Leadership:** Gain a single, reliable source of truth for European sales performance, enabling data-driven strategic decision-making.
