# Power BI Sales Dashboard Project
 
## 📖 Overview
 
This repository contains a Power BI report file (`Powerbi _1.pbix`) designed to analyze and visualize sales data. The dashboard provides insights into key performance indicators (KPIs), sales trends over time, top-performing products, and regional sales breakdowns.
 
The primary goal of this project is to offer a clear and interactive tool for business stakeholders to monitor sales performance and make data-driven decisions.
 
---
 
## 🖼️ Dashboard Preview
 
Here is a preview of the main dashboard page. A short GIF is included to demonstrate the report's interactivity.
 
![Dashboard Screenshot]

 <img width="1182" height="680" alt="image" src="https://github.com/user-attachments/assets/79b14bc9-250f-440e-a676-ff45270457e1" />

---
 
## ✨ Features
 
* **Executive Summary:** A high-level overview of critical KPIs like total revenue, profit margin, and total units sold.
* **Trend Analysis:** Interactive charts showing sales and profit trends on a monthly, quarterly, and yearly basis.
* **Product Insights:** Visuals to identify best-selling products and categories.
* **Regional Performance:** A map visualization to track sales performance across different geographical areas.
* **Interactive Filtering:** Slicers and filters for year, region, and product category to allow for granular analysis.
 
---
 
## 🛠️ Technical Details
 
### Report Pages
 
The report is organized into the following pages:
 
* **Summary Page:** An executive dashboard with key KPIs and high-level trends.
* **Product Detail:** A deep-dive page focusing on product performance, category analysis, and inventory levels.
* **Customer Analysis:** A breakdown of sales by customer segment and geography.
* **Data Details:** A table view of the raw data for verification purposes.
 
### Data Model
 
The data model follows a star schema, which is optimized for performance and simplicity in Power BI.
 
* **Fact Table:** `Sales` - Contains transactional data like order quantity, price, and cost.
* **Dimension Tables:**
    * `DimDate` - A calendar table for time-based analysis.
    * `DimProduct` - Contains details about each product (e.g., category, brand).
    * `DimCustomer` - Contains customer information (e.g., name, location).
    * `DimRegion` - Details on sales territories and regions.
 
![Data Model Schema]

<img width="298" height="382" alt="image" src="https://github.com/user-attachments/assets/389442d4-20c6-49d7-a86c-5886e45514c0" />

 
### Key DAX Measures
 
Here are some of the central DAX measures used to drive the report's calculations:
 
* **Total Revenue:** Calculates the sum of all sales transactions.
    ```dax
    Total Revenue = SUMX('Sales', 'Sales'[Order Quantity] * 'Sales'[Unit Price])
    ```
* **YoY Revenue Growth %:** Calculates the year-over-year growth percentage for revenue.
    ```dax
    YoY Revenue Growth % =
    VAR CurrentYearRevenue = [Total Revenue]
    VAR PreviousYearRevenue = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('DimDate'[Date]))
    RETURN
    DIVIDE(CurrentYearRevenue - PreviousYearRevenue, PreviousYearRevenue)
    ```
* **Total Profit Margin:** Calculates the overall profit margin as a percentage.
    ```dax
    Total Profit Margin =
    VAR TotalProfit = SUMX('Sales', 'Sales'[Order Quantity] * ('Sales'[Unit Price] - 'Sales'[Unit Cost]))
    VAR TotalRevenue = [Total Revenue]
    RETURN
    DIVIDE(TotalProfit, TotalRevenue)
    ```
 
---
 
##  Prerequisites
 
To open and interact with this report, you need to have **Power BI Desktop** installed on your machine.
 
* You can download it for free from the [official Microsoft website](https://powerbi.microsoft.com/en-us/desktop/).
 
---
 
## 🚀 How to Use
 
1.  **Download the File:**
    * Clone this repository:
        ```bash
        git clone <repository-url>
        ```
    * Or, download the `Powerbi _1.pbix` file directly from the GitHub interface.
 
2.  **Open the Report:**
    * Locate the downloaded `Powerbi _1.pbix` file on your computer.
    * Double-click the file to open it in **Power BI Desktop**.
 
3.  **Refresh Data (If Applicable):**
    * In the "Home" tab of Power BI Desktop, click the **"Refresh"** button.
    * You might be prompted to enter credentials for the underlying data sources.
 
---
 
## 📊 Data Sources
 
This report connects to the following data sources. Please ensure you have the necessary access permissions.
 
* **Source 1:** [e.g., An Excel file named 'SalesData.xlsx']
* **Source 2:** [e.g., A SQL Server database]
* **Source 3:** [e.g., A SharePoint folder]
 
*(Please update this section with the specific data sources used in your report.)*
 
---
 
## 👤 Author
 
* **Name:** Srinadha Reddy Emani
* **Contact:**srinadhareddy11@gmail.com
 
---
 
## 📄 License
 
This project is licensed under the MIT License. See the [LICENSE.md](LICENSE.md) file for details.
