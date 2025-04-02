# Global Superstore Data Analysis Report
_Disclaimer: The dataset used in this analysis is from the Global Superstore, a hypothetical multinational retail corporation. The data is for educational and analytical purposes only._
![Sales Image](https://github.com/user-attachments/assets/1e74d13f-9dd3-474b-8565-e5a4a9aa66ab)
## I. Introduction
Global Superstore is a global online retailer based in New York, boasting a broad product catalog and aiming to be a one-stop shop for its customers. This report analyzes the Superstore's data to identify trends and insights.
## II. Data Description
This dataset comprises three tables:
- **Order Table**: Contains 24 columns ([Row ID, Order ID, Order Date, Ship Date, Ship Mode, Customer ID, Customer Name, Segment, City, State, Country, Market, Region, Product ID, Category, Subcategory, Product Name, Sales, Quantity, Discount, Profit, Postal Code, Shipping Cost, Order Priority]) and 51,290 rows. The dataset includes over 10,000 different products purchased by customers from 147 different countries. Products belong to three main categories: office supplies (e.g., staples), furniture (e.g., chairs), and technology (e.g., smartphones).
- **People Table**: Contains 2 columns and 13 rows.
- **Returns Table**: Contains 3 columns and 1,173 rows.  
![Flat file](https://github.com/user-attachments/assets/7bfdb7bb-7233-4895-a121-e5f17def8aa8)
## III. Problem Statement
### 1. Profitability Analysis
**(a)** Identify the three countries that generated the highest total profit for Global Superstore in 2014. 
**(b)** Determine the three most profitable products in these countries, including their names and total profit.
### 2. Shipping Cost Analysis
**(a)** Identify the three subcategories with the highest average shipping cost in the United States.
### 3. Nigeria's Profitability
**(a)** Assess Nigeria’s total profit in 2014 and compare it to other African countries.  
**(b)** Investigate factors contributing to Nigeria’s poor performance, including shipping costs and average discounts.
### 4. Profitability in Southeast Asia
**(a)** Identify the least profitable product subcategory in Southeast Asia. Assume that Southeast Asia comprises Cambodia, Indonesia, Malaysia, Myanmar (Burma), the Philippines, Singapore, Thailand, and Vietnam.
**(b)** Determine whether Global Superstore should stop offering this subcategory in a specific country.
### 5. Least Profitable City in the United States
**(a)** Identify the least profitable city in terms of average profit, discarding cities with fewer than 10 orders.
**(b)** Analyze the reasons behind this city’s low average profit.
### 6. Australia’s Most Profitable Subcategory
**(a)** Identify the product subcategory with the highest average profit in Australia.
### 7. Customer Value Analysis
**(a)** Identify the most valuable customers and what they purchase.
## IV. Methodology
Power BI was used for data cleaning, modeling, analysis, and visualization.
## V. Data Transformation & Cleaning
The dataset was cleaned using Power Query. The steps included:
1. Confirming data types, ensuring correctness.
2. Extracting the year from the Order Date column in the Order Table.
3. Deleting the Postal Code column from the Order Table due to 80% null values.
4. Removing the People Table as it was irrelevant to the analysis.
5. Using the first row as headers in the Returns Table.
6. Merging the Returns Table with the Order Table. Then, splitting the Order Table into fact and dimension tables for data modeling.
7. Removing duplicates in all dimension tables except the Fact Table and Customer Table.
## VI. Data Modeling
### A. Fact Table Columns:
The Fact Table contained numeric data and key identifiers: Customer ID, Discount, Order Date, Order ID, Order Year, Product ID, Profit, Quantity, Row ID, Sales, Ship Date, Ship Mode, and Shipping Cost.
### B. Dimension Tables:
1. **Customer Table** ([Customer ID, Customer Name, Segment]) – One-to-many relationship with the Fact Table.
2. **Location Table** ([Row ID, City, Country, Market, Region, State]) – One-to-one relationship with the Fact Table.
3. **Product Table** ([Product ID, Category, Subcategory, Product Name]) – One-to-many relationship with the Fact Table.
4. **Order & Shipping Table** ([Order ID, Order Date, Order Priority, Order Year, Returned, Ship Date, Ship Mode]) – One-to-many relationship with the Fact Table.
![P2 Data modelling](https://github.com/user-attachments/assets/beb6bbb4-18d5-4a6d-a7c0-e753dc6be191)
## VII. DAX Formulas Used
1. Number of customers
2. Number of countries
3. Number of products
4. Number of orders
5. Total profits
6. Average shipping cost
7. Average discount
8. Average profit
9. Average profit for cities with at least 10 orders
10. City order count
## VIII. Findings & Insights
1a. **Top 3 profitable countries in 2014:**
![Most Profitable Countries](https://github.com/user-attachments/assets/5cb7d1f4-2480-432c-9237-d8d81dfa1bd1)
### Findings:
  - USA ($94K), India ($49K), China ($47K).
### Insight: 
The United States generated the highest total profit in 2014, with nearly twice the profit of India, the second-highest earner. China followed closely behind India.

  b. **Top 3 profitable products per country:**
  USA                                          | India                                            | China
  :-------------------------------------------:|:------------------------------------------------:|:--------------------------------------------------:
  ![P2 USA](https://github.com/user-attachments/assets/dc95ffe4-c14f-4274-9055-4c0df770ef7d)|![P2 India](https://github.com/user-attachments/assets/a7ea669e-5934-4ae3-b54f-1c3443e8ccf2)|![P2 China](https://github.com/user-attachments/assets/8bd8fb58-493b-427e-aa62-2a913a17b677)

  


