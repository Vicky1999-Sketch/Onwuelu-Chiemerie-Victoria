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
### Insight: 
Bookcases are the top-selling products in both India and China, while copiers are the most popular in the United States.

2a. **Highest shipping costs in the USA:**

![HASC USA](https://github.com/user-attachments/assets/43c16e6b-c1b5-40a2-96aa-de2985291810)
### Findings:
- Copiers (165), Machines (132), and Tables (70)

3a. **Nigeria’s profitability in 2014:**

Globally                                       | Africa
:---------------------------------------------:|:-----------------------------------------|
![NP Globally](https://github.com/user-attachments/assets/46146471-293e-40fb-afb1-cadf825c9540)|![NP Africa](https://github.com/user-attachments/assets/25e8889e-632f-4627-b97f-d60a945cae32)

### Findings
Globally, out of 138 countries in 2014, Nigeria ranked second to last in profitability, with a profit/loss of -$23,285.19, compared to the highest, the USA, with $93,507.51. In comparison with the other 39 African countries that year, Nigeria came last, while South Africa was the most profitable, with $9,363.24.

b. **Factors that might be responsible for Nigeria’s poor performance:**

Nigeria had 137 orders, 128 customers, and 257 products. When the number of customers, products, and orders in Nigeria is compared to other countries globally and amongst African countries, it becomes clear that the major challenge of the Nigerian market, or its low position, isn't due to being the lowest in these parameters. In fact, in comparison, these parameters are relatively high. 

Notably, some factors most likely responsible for Nigeria's poor revenue performance are its high average discount and low shipping cost. 

Nigeria had an average discount of 0.70, which is significantly higher than the global average (0.14) and the African average (0.14). 

Additionally, the analysis further suggests a potential correlation between high shipping costs and high profitability. The top profitable countries both globally and in Africa (USA, South Africa, and Morocco) had relatively high shipping costs. Nigeria's average shipping cost was $5.50, which is lower than the global average ($26.27) and the African average ($18.52), potentially impacting its revenue.

4a. **Least profitable subcategory in Southeast Asia:**

![LPPS](https://github.com/user-attachments/assets/cb0fba0e-c5cd-4ab0-a826-1beda9058a71)
### Finding:
- **Tables** (-$18,618.31)

b. **The specific country in Southeast Asia that should stop offering the product, table:**
![P2 LPPS Indo](https://github.com/user-attachments/assets/eb4b3f7b-11a0-4908-b8bb-8f291480cc2a)
### Finding:
**Indonesia**. This is due to extreme losses (-$10,680.28).
5a. **Least profitable city in the USA:**
![P2 lapc](https://github.com/user-attachments/assets/939a2b1d-b7e7-40c3-840d-d0447663f760)
### Finding:
- **Lancaster** (-$157.37 average profit)
b. **The reasons behind this city’s low average profit**
Copier had the most sales, with an average profit of $817.90 in the United States. On average, Lafayette, the most profitable city in the United States, surpassed that with $8,399.98. However, despite Copier being the top-selling category nationwide, Lancaster made no sales in the Copier category. Furthermore, Lancaster experienced a significant loss in Machines (-$6,599.98), contributing to the city's overall low average profit.

6a. **Most profitable subcategory in Australia:**

![HAPS](https://github.com/user-attachments/assets/b4ad68e1-384d-4523-b219-dd32c9ceec90)
### Finding:
- **Appliances** ($139.01 average profit).

7a **Most valuable customers:**

 ![MVC](https://github.com/user-attachments/assets/4e9751c0-0c1e-4630-94a4-c5a7d3707116)
### Finding:
- Top customers mainly purchased **Canon imageCLASS 2200 Advanced Copiers**.
## IX. Recommendations
1. Increase resource allocation to the USA, India, and China to capitalize on high-profit potential.
2. Customize product offerings by region (e.g., focus on copiers in the USA and bookcases in India/China).
3. Investigate the reasons behind the relatively high shipping costs for machines and tables in the United States, as these two products attracted low total profits (machine) and negative loss (table) on average. Identify opportunities to reduce these costs and improve profitability.
4.Nigeria's high discounts (0.70) might be contributing to its low profitability. Negotiating better prices or reducing discounts could help improve profitability.
5. Nigeria's low shipping costs (5.50) might be indicative of inefficient logistics or infrastructure. Investing in these areas could help reduce costs and improve profitability.
6. Address Lancaster’s low profitability by investigating machine category losses. It could be due to high costs, low demand, or inefficient operations.
7. Create a sales plan to target the copier category in Lancaster, as it has potential for high profits nationwide.
8. Identify areas to optimize operations and reduce costs in Lancaster, particularly in categories with high losses.
9. Investigate customer behavior and preferences in Lancaster to tailor sales strategies and improve profitability.
10. Consider exploring new markets or categories in Lancaster that may offer better profit opportunities.
11. Discontinue table sales in Indonesia due to high losses.
    
## X. Conclusion
This analysis of Global Superstore’s dataset has highlighted key trends and insights into profitability, shipping costs, and customer behavior. The United States remains the most profitable market, while Nigeria struggles due to high discounts and low shipping costs. In Southeast Asia, table sales are a major loss driver, particularly in Indonesia. Furthermore, Lancaster’s low profitability in the United States is linked to poor product mix and high losses in the machine category. Addressing these issues through strategic product positioning, pricing adjustments, and cost optimization will enhance overall profitability and operational efficiency for Global Superstore.

## Dashboard
![P2 D2](https://github.com/user-attachments/assets/88008ad3-a87c-4617-8176-88a677790199)
Page 1
![P2 D1](https://github.com/user-attachments/assets/149a1edc-bd91-4c83-a081-7335f89b04dc)
Page 2


















