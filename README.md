# Vendor-Performance-Analysis


# Business Problem

Effective inventory and sales management are critical for optimizing profitability in the retail and wholesale industry. Companies need to ensure that they are not incurring losses due to inefficient pricing, poor inventory turnover, or vendor dependency. The goal of this analysis is to:

*Identify underperforming brands that require promotional or pricing adjustments.
*Determine top vendors contributing to sales and gross profit.
*Analyze the impact of bulk purchasing on unit costs.
*Assess inventory turnover to reduce holding costs and improve efficiency.
*Investigate the profitability variance between high-performing and low-performing vendors."

![image alt](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/dash1.png)



![image alt](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/dash2.png)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda1.png )

Following code first loads the initial 6 million rows of a CSV file named "sales.csv" into a Pandas DataFrame and saves it to a new CSV. It then sets up a SQLite database connection (inventory_new.db) using SQLAlchemy and sqlite3, preparing to iterate through files in a 'sales' directory to read them into DataFrames and potentially ingest them into the database
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda2.png )


This segment defines a function ingest_db to write Pandas DataFrames to a SQL database table. It then connects to the SQLite database inventory_new.db and queries the database to list all existing tables, which are then displayed to verify database structure. Finally, it demonstrates reading and displaying the first few rows of the 'begin_inventory' table, along with its record count, to show data ingestion and access.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda3.png)


This part of the code focuses on examining the 'purchases' and 'purchase_prices' tables from the database. It first prints the total record count for the 'purchases' table (2,372,474 records). Subsequently, it displays the first few rows of both the 'purchases' and 'purchase_prices' tables, providing a snapshot of their schema and data content, aiding in understanding purchase transaction and pricing details.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda4.png)



This section reviews the 'sales_5M' and 'vendor_invoice' tables within the database. It confirms the 'sales_5M' table contains 6,000,000 records, displaying its initial rows to show sales transaction data. Following this, it presents the first few entries of the 'vendor_invoice' table, which outlines vendor payment details and approval status
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda5.png )



This code block demonstrates a specific query on the 'purchases' table to filter records by 'VendorNumber'. It connects to the database and executes a SQL query to select all purchases made from 'VendorNumber' 4466. The resulting DataFrame, containing 2,192 rows and 16 columns, is then displayed, providing a focused view of transactions with this particular vendor.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda6.png )

This code retrieves and displays specific purchase price data and vendor invoice details from the database. It first queries the purchase_prices table to show prices for items from 'VendorNumber' 4466. Immediately following, it fetches and presents all invoice records associated with the same 'VendorNumber' from the vendor_invoice table, offering a comprehensive view of that vendor's transaction history.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda7.png )
This block specifically extracts sales data related to 'VendorNumber' 4466 from the sales_5M table. It performs a SQL query to select all sales records where the VendorNumber matches 4466. The output displays the first and last few rows of the resulting DataFrame, showing transaction details like quantity, sales dollars, and sales dates for products from this particular vendor.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt](  https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda8.png)



This code performs aggregation operations on sales and purchase data, then retrieves freight cost summaries. It groups purchase data by 'Brand' to sum 'Quantity' and 'Dollars', and similarly aggregates 'sales_5M' data by 'Brand' for 'SalesDollars' and 'SalesQuantity'. Finally, it queries the database to calculate the total 'Freightcost' for each 'VendorNumber' from the vendor_invoice table, providing summarized financial insights.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda9.png  )


This extensive SQL query constructs a comprehensive vendor_sales_summary table. It first calculates total Freightcost per vendor, then builds a PurchaseSummary by joining purchase and purchase price data, and a SalesSummary from sales data. These summaries are then joined together by VendorNumber and Brand, creating a unified dataset that combines purchasing, sales, and freight cost information at the brand level for each vendor.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt]([ ](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda10.png) )



This code block performs a basic check for missing values and lists unique vendor names from the compiled vendor_sales_summary DataFrame. It uses .isnull().sum() to report the count of missing values for each column, indicating data completeness. Subsequently, it extracts and displays an array of all distinct VendorName entries, providing an overview of all unique vendors included in the summary data.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda11.png )


This section cleans and enhances the vendor_sales_summary DataFrame by handling missing values and calculating key profitability metrics. It converts the 'Volume' column to a numeric type, removes rows with missing values, and strips whitespace from 'VendorName' for consistency. Crucially, it then computes 'GrossProfit', 'ProfitMargin', 'StockTurnover', and 'SaleToPurchaseRatio' based on existing columns, making the dataset ready for advanced analysis.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt]( https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda12.png )



This code prepares to store the processed vendor_sales_summary data into the SQLite database. It first prints the column names of the DataFrame, then defines a SQL CREATE TABLE statement with appropriate data types and a primary key. Finally, it executes this SQL command to create the vendor_sales_summary table in the database, and displays the first row of the DataFrame as confirmation.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
![image alt](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/eda13.png  )


This final code block saves the prepared vendor_sales_summary DataFrame to both a CSV file and the SQLite database. It first writes the DataFrame to vendor_sales_summary_new.csv without including the index. Then, it utilizes the to_sql method to ingest the DataFrame into the vendor_sales_summary table in the inventory_new.db database, ensuring data persistence and accessibility for further analysis.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Data Visulaisation with Power BI

![image alt](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/dash1.png)




Dashboard 1 
# 1. KPI Cards (Top Row):

# *Total Purchase($): 5.87M
Explanation: This card shows the aggregate value of all purchases made by the company, totaling 5.87million.Itprovidesaquickoverviewofthetotalspendingoninventoryorgoodsacquiredfromvendors
# ∗TotalSales: 7.00M $
Explanation: This card indicates the total revenue generated from all sales, amounting to 7.00million.Its a key metric for understanding the overall sales performance of the business.
# ∗GrossProfit: 1.12M $
Explanation: This card displays the total gross profit, calculated as Total Sales minus Total Purchases (or Cost of Goods Sold), which is $1.12 million. It represents the profit generated from sales before deducting operating expenses.
# *Average Profit Margin: 21.18$
Explanation: This card shows the overall average profit margin across all sales, which is 21.18%. It indicates the percentage of revenue that remains as gross profit, reflecting the general profitability of the products or operations.
# 2. Top 10 Vendors By Sales (Left-Middle Bar Chart):

Explanation: This horizontal bar chart visualizes the top ten vendors based on the total sales amount attributed to their products. It allows for quick identification of the most significant vendors in terms of revenue generation for the business, helping to prioritize vendor relationships.
# 3. Top 5 Vendors by sales to purchase ratio (Right-Middle Table/Table Chart):

Explanation: This table lists the top five vendors, along with a specific brand they supply and the "Sales to Purchase Ratio" for that brand. This ratio indicates how effectively the sales generated from a brand compare to the cost of purchasing that brand, highlighting vendors whose brands offer strong revenue-to-cost efficiency.
# 4. Top 10 Brands By Sales (Bottom-Left Bar Chart):

Explanation: This horizontal bar chart presents the ten highest-selling brands in terms of total sales dollars. It helps in understanding which specific brands are the primary drivers of revenue for the business, guiding inventory and marketing strategies.
# 5. Top 5 Purchase Contribution by Percentage (Bottom-Right Donut Chart):

Explanation: This donut chart illustrates the percentage contribution of the top five vendors to the total purchases. Each slice represents a vendor's share of overall purchasing spend, providing a visual breakdown of where the majority of procurement budget is allocated.
# Dashboard 2 

![image alt](https://github.com/Vijay-Dhok/Vendor-Performance-Analysis/blob/dcfccc18992e302cf926638bec284712228ecef3/dash2.png)



# 1. KPI Cards (Left Column):

# *Total unsold capital($): 1.38M
Explanation: This card shows the total monetary value of inventory that has been purchased but not yet sold, amounting to 1.38million.Itrepresentscapitaltiedupininventoryandisacrucialmetricforinventorymanagementandcashflow.∗∗∗TotalFreightCost(): 49.44M**
Explanation: This card displays the total cost incurred for shipping and transportation of goods, which is $49.44 million. This highlights a significant operational expense that impacts overall profitability and logistics efficiency.
# 2. Low Performing Brands (Top-Right Scatter Plot):

Explanation: This scatter plot (similar to your scatter.png but with a filter applied and likely a modified DAX for "Low Performing Brands") visualizes individual brands based on TotalSales (X-axis) and AvgProfitmargins (Y-axis). The points are colored to distinguish "Low Performing Brands" (pink/magenta) from others (cyan/blue).
If DAX identifies "low sales, low profit": The pink points would primarily be in the bottom-left quadrant, indicating brands that are struggling with both low sales volume and low profitability within the current sales filter context.
If DAX identifies "low sales, high profit" (original logic): The pink points would be in the upper-left quadrant, identifying brands with low sales volume but high average profit margins, as discussed earlier.
The filter TotalSales < 1000 is applied, meaning only brands with total sales less than $1000 are shown, and the "Low Performing Brands" classification is relative to this filtered subset.
# 3. Unsold Inventory % by VendorName (Bottom-Left Donut Chart):

Explanation: This donut chart breaks down the percentage of unsold inventory value contributed by different vendors. It helps identify which vendors are associated with the largest portions of capital tied up in unsold stock, guiding inventory planning and vendor negotiations.
# 4. Top 5 Low Performing Vendors by avg Stock Turnover (Bottom-Right Bar Chart):

Explanation: This horizontal bar chart displays the top five vendors with the lowest average stock turnover rates. A low stock turnover indicates that inventory from these vendors is selling slowly, potentially leading to higher holding costs and obsolescence. This chart helps identify problematic vendors from an inventory efficiency perspective.

