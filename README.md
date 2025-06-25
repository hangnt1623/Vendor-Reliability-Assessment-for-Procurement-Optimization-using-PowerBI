# PowerBI_Purchasing_Vendors Assessment

- Author: Nguyen Thuy Hang
- Date: 2025-06-25
- Tools Used: Power BI

---

## 📑 Table of Contents  
1. [📌 Background & Overview](#-background--overview)  
2. [📂 Dataset Description & Data Structure](#-dataset-description--data-structure)  
3. [🧠 Design Thinking Process](#-design-thinking-process)  
4. [📊 Key Insights & Visualizations](#-key-insights--visualizations)  
5. [🔎 Final Conclusion & Recommendations](#-final-conclusion--recommendations)

---

## 📌 Background & Overview  

### Objective:
### 📖 What is this project about? 
This project focuses on building an Operation Dashboard for Adventure Works. The primary goal is to visually assess vendor performance, providing leadership with clear, data-driven insights to optimize procurement and strengthen the supply chain.
The goal is to
- Ensure optimal procurement: Get the sufficient goods, delivery on time, at the best price
- Strengthen the supply chain: Identify and manage top-performing and underperforming suppliers
- Support data-driven decisions: Empower leadership with clear insights for better purchasing strategies

### 👤 Who is this project for?  

✔️ Chief Executive Officer (CEO)

✔️ Chief Operating Officer (COO)

✔️ Chief Procurement Officer (CPO)/Head of Purchasing

###  ❓Business Questions:  

✔️ Assess vendor fulfillment accuracy by analyzing whether suppliers consistently provide the correct and sufficient quantities of goods and materials as ordered

✔️ Evaluate vendor delivery performance by understanding how effectively our suppliers are meeting agreed-upon delivery timelines

✔️ Determine supplier credibility and reliability by examining factors that demonstrate their trustworthiness and consistent adherence to commitments

✔️ Optimize procurement costs by analyzing vendor pricing and overall expenditure to ensure the best value for Adventure Works

### 🎯Project Outcome:  

---

## 📂 Dataset Description & Data Structure  

### 📌 Data Source  
- Source: The dataset is obtained from Kaggle.
- Size:
  + Product table contains 504 records 
  + Purchasing Order Detail table contains 8,845 records
  + Purchasing Order Header table contains 4,012 records
  + Purchasing Product Vendor contains 460 records
  + Purchasing Vendor contains 104 records
- Format: .csv

### 📊 Data Structure & Relationships  

#### 1️⃣ Tables Used:  
There are 5 tables in the dataset:
- Product table: store information about products sold or used in the manfacturing of sold products
- Purchasing Order Detail table: store information about individual products associated with a specific purchase order
- Purchasing Order Header table: store information about general purchase order information
- Purchasing Product Vendor table: store information about cross-reference table mapping vendors with the products they supply
- Purchasing Vendor table: store information about companies from whom Adventure Works Cycles purchases parts or other goods

This project also make other tables from these 5 tables, these are:
- Product Price table: store information about product price
- Purchase Order: store information about individual products associated with a specific purchase order & general purchase order information
- Date: store information about the date
- Ship Method: store information about ship method

#### 2️⃣ Data Relationships

<img width="510" alt="{582A5354-C743-4FC7-BABC-F487F2CD043D}" src="https://github.com/user-attachments/assets/ea66fa22-a789-49d6-94f5-4d3be654313c" />

 (1) Purchasing_Vendor and Purchasing_OrderHeader
 
- Relationship: One-to-Many (1 on Purchasing_Vendor to * on Purchasing_OrderHeader)
- Fields: Purchasing_Vendor[BusinessEntityID] to Purchasing_OrderHeader[VendorID]
- Description: A single vendor (from Purchasing_Vendor) can have multiple purchase orders (Purchasing_OrderHeader).

(2) Purchasing_Vendor and Purchasing_ProductVendor

- Relationship: One-to-Many (1 on Purchasing_Vendor to * on Purchasing_ProductVendor)
- Fields: Purchasing_Vendor[BusinessEntityID] to Purchasing_ProductVendor[BusinessEntityID]
- Description: A single vendor can supply multiple products (recorded in Purchasing_ProductVendor), or a product can be supplied by multiple vendors but Purchasing_ProductVendor lists vendor-product pairs.

(3) Product_Product and Purchasing_ProductVendor
- Relationship: One-to-Many (1 on Product_Product to * on Purchasing_ProductVendor)
- Fields: Product_Product[ProductID] to Purchasing_ProductVendor[ProductID]
- Description: A single product can be associated with multiple vendors in the Purchasing_ProductVendor table. Combined with relationship 5, this creates a Many-to-Many relationship between Purchasing_Vendor and Product_Product through the Purchasing_ProductVendor bridge table.


(4) Purchasing_OrderDetail and Product_Product
- Relationship: Many-to-One (* on Purchasing_OrderDetail to 1 on Product_Product)
- Fields: Purchasing_OrderDetail[ProductID] to Product_Product[ProductID]
- Description: Multiple order detail lines can refer to the same product, but each product is unique in the Product_Product table.

(5) Purchasing_OrderHeader and Purchasing_OrderDetail
- Relationship: One-to-Many (1 on Purchasing_OrderHeader to * on Purchasing_OrderDetail)
- Fields: Purchasing_OrderHeader[PurchaseOrderID] to Purchasing_OrderDetail[PurchaseOrderID]
- Description: A single purchase order header can contain multiple detail lines (items) within that order.

(6)  Purchasing_OrderHeader and ShipMethod
- Relationship: Many-to-One (* on Purchasing_OrderHeader to 1 on ShipMethod)
- Fields: Purchasing_OrderHeader[ShipMethodID] to ShipMethod[ShipMethodID]
- Description: Many purchase orders can use the same shipping method, but each shipping method is unique in the ShipMethod table.

(7) Purchasing_OrderHeader and dim_Date
- Relationship: Many-to-One (* on Purchasing_OrderHeader to 1 on dim_Date)
- Fields: Purchasing_OrderHeader[OrderDate] to dim_Date[Date]
- Description: Many purchase orders can occur on the same date, but each date is unique in the dim_Date table. This allows for time-based analysis of orders.

*Others*

(8) Purchasing_ProductVendor and Product_Price (Many-to-Many via ProductID)

(9) Purchasing_OrderDetail and PurchaseOrder (1-1 via PurchaseOrderDetailID)

---

## 🧠 Design Thinking Process  

Explain the step-by-step approach taken to solve the problem.  

1️⃣ Empathize  

(1) 5W1H 

<img width="888" alt="{16F02EA4-5BC9-4762-9107-0532A29E03CC}" src="https://github.com/user-attachments/assets/51accd24-8b57-47cc-8f64-d5d19770fb51" />

(2) Empathy Map

<img width="744" alt="{57C97CED-896E-4C4C-B992-EC7B95450C31}" src="https://github.com/user-attachments/assets/ba9f9158-33b3-495b-9920-1dd97f2c710b" />

(3) Stakeholder need

<img width="322" alt="{02E2FE73-8877-42E6-9DE5-58C920D3D14A}" src="https://github.com/user-attachments/assets/c138b168-7918-41a2-a12c-8f31f8f939d9" />

2️⃣ Define point of view  

(1) North Star Metric

<img width="208" alt="{C76B8C0F-FFB1-4224-B0E1-7712031915A9}" src="https://github.com/user-attachments/assets/6d1e28db-fda3-4e91-9d2a-b148ddba44d0" />

(2) Point of view 

<img width="351" alt="{EE391BB0-E21C-4BB0-BA43-E5A6E43ACF94}" src="https://github.com/user-attachments/assets/154e3b98-3269-4b75-b699-995d6c39662c" />


3️⃣ Ideate  

<img width="432" alt="{F2B06667-9698-4565-B028-D5DCD83045E0}" src="https://github.com/user-attachments/assets/ba5eb8c3-587a-4e71-bd56-fc80bd288d68" />



4️⃣ Prototype and review  

This part is presented in Dashboard.

## ⚒️ Main Process

1️⃣ Data Cleaning & Preprocessing  
2️⃣ Exploratory Data Analysis (EDA)  
3️⃣ Power BI Visualization  
---

## 📊 Key Insights & Visualizations  

### 🔍 Dashboard Preview & Analysis

#### 1️⃣ Dashboard 1: Overview


**📌 Analysis 1**

***Oberservations***
- Profitability (North Star Metric): Overall Profit Margin is 11.61%, showing stability over time, despite fluctuations. Sales and Profit grow in parallel (Sales YOY: 51.55%).
- Customer Health: High Retention Rate (92.23%) and low Churn Rate (7.77%) indicate strong customer loyalty.
- Category Profit Disparity: Technology and Office Supplies show strong Profit Margins (both ~14%), significantly outperforming Furniture (only 7% Profit Margin).
- Segment Profit Uniformity: All customer segments (Home Office, Corporate, Consumer) exhibit similar Profit Margins (~12%). However, Corporate has the highest Return Rate compared to Home Office and Consumer.

***Recommendations***
- Enhance Furniture Profitability: Deep dive into the 7% Profit Margin of Furniture to identify cost or pricing issues. This is crucial for improving the overall Profit Margin.
- Capitalize on Top Categories: Continue investing in Technology and Office Supplies to leverage their strong (~14%) Profit Margins.
- Address Corporate Returns: Investigate the high Return Rate in the Corporate segment to protect its ~12% Profit Margin.
- Sustain Overall Growth: Maintain strategies driving strong sales growth (51.55% YOY) and high retention to support the stable 11.61% Profit Margin.

#### 2️⃣ Dashboard 2: Market Tracker
<img width="744" alt="{B71DE64E-B43A-4DB4-B3A9-6D5887CA3814}" src="https://github.com/user-attachments/assets/73ef3283-2ba2-44aa-ab09-ea95603a863a" />

**📌 Analysis 2**

***Oberservations***
- Strong & Stable Markets:
   + APAC: Largest sales share (28.36%), healthy 12.16% Profit Margin, and good 84.91% Retention
   + EU: High sales share (23.24%), highest Profit Margin (12.69%), but also the highest Return Rate (6.21%)
   + US: Significant sales share (18.17%), strong 12.47% Profit Margin, but moderate 5.95% Return Rate
- Promising Market with Challenges:
   + Africa: Good 11.34% Profit Margin with exceptionally low 0.04% Return Rate, but suffers from very low 53.21% Retention and high 46.79% Churn
- Markets Needing Urgent Review:
  + LATAM: Moderate 10.24% Profit Margin and moderate Return Rate (5.82%)
  + EMEA: Lowest Profit Margin (5.45%) and very high 40.85% Churn Rate
  + Canada: Exceptionally high 26.62% Profit Margin, but critically unsustainable with 93.44% Churn Rate and minimal sales share (0.53%)

***Recommendations***
- Sustain & Optimize Strong Markets
  + APAC: Continue investment to leverage scale and 12.16% PM
  + EU: Prioritize reducing its 6.21% Return Rate to maximize the 12.69% PM
  + US: Focus on improving retention and reducing its 5.95% Return Rate to solidify 12.47% PM.
- Develop Africa's Retention: Invest in strategies to boost retention and reduce churn in Africa, capitalizing on its good 11.34% PM and minimal returns
- Strategic Review for Challenging Markets:
  + LATAM: Optimize operations and address its 5.82% Return Rate to enhance its 10.24% PM
  + EMEA: Requires a major strategic overhaul to address the 5.45% PM and very high churn
  + Canada: Investigate the extreme churn (93.44%) despite high 26.62% PM; unsustainable for growth


#### 3️⃣ Dashboard 3: Product Tracker
<img width="735" alt="{0A5C27CE-4293-4B59-9103-9B1DAFFF741E}" src="https://github.com/user-attachments/assets/77e35abe-adf9-4909-89b6-0faedee1c865" />

**📌 Analysis 3**

***Oberservations***
- Product Category Performance:
  + Technology (37.53% sales) & Furniture (32.51% sales) are top revenue, but Technology has Profit Margin increase gradually between 13~14%
  + Office Supplies (29.96% sales) shows consistently low and declining Profit Margin (~3-5%), significantly impacting overall PM
- Customer Segment Health by Category:
  + Office Supplies has the highest Retention Rate (~89.32%)
  + Furniture has the highest Return Rate (~6-7.5%) and the lowest Profit Margin, with sub-categories even showing negative PM
- Sub-Category Profitability:
  + High PM: Paper (24.24%), Labels (20.45%), Envelopes (17.32%), Copiers (17.13%) (Office Supplies); Accessories (17.30%) (Technology)
  + Low/Negative PM: Tables (-8.46%), Chairs (9.35%) (Furniture); Machines (7.56%) (Technology); Storage (9.62%), Supplies (9.29%) (Office Supplies)

***Recommendations***
- Maximize Technology: Invest in Technology to capitalize on its increasing 13-14% PM
- Urgent Office Supplies Review: Investigate reasons for Office Supplies' declining ~3-5% PM despite high retention; focus on high-PM sub-categories
- Restructure Furniture: Address high returns and eliminate/re-evaluate loss-making Furniture (e.g., Tables: -8.46% PM)
- Optimize Sub-Categories: Promote high-PM items (Paper, Labels) and improve/review low-PM items (Machines, Storage, Supplies)


---

## 🔎 Final Conclusion & Recommendations  

> **The company demonstrates strong growth and customer loyalty, yet the overall 11.61% Profit Margin is significantly weighed down by underperforming product categories and specific markets.**

👉🏻 Based on the insights and findings above, we would recommend Senior Manager to consider the following:  

📌 Market Recommendations
- Sustain Strong Markets: Keep investing in APAC, EU, and US. For EU and US, focus on reducing return rates to maximize profit
- Develop Africa's Potential: With good profit and low returns, prioritize improving retention and reducing churn to unlock growth
- Overhaul Challenging Markets:
  + EMEA: Major strategic overhaul needed due to very low Profit Margin (5.45%) and high churn
  + Canada: Investigate extreme churn (93.44%) despite high profit; it's unsustainable
  + LATAM: Optimize operations and address return rates

📌 Product Recommendations  
- Urgent Furniture Profitability Fix: The 7% Profit Margin and unprofitable Tables (-8.46% PM) are major drags. Immediately review costs, pricing, and quality. Consider discontinuing loss-making items.
- Boost Office Supplies Margin: Despite high retention, the declining ~3-5% Profit Margin needs attention. Promote high-margin sub-categories (e.g., Paper, Labels) and address inefficiencies in low-margin ones.
- Capitalize on Technology: This category shows strong and increasing 13-14% Profit Margins. Continue investment and innovation.

***-> By aggressively addressing Furniture and Office Supplies profitability and implementing targeted market strategies (leveraging strong markets, developing Africa, and fixing underperformers), the company can significantly enhance its overall profit margin while sustaining strong growth and customer loyalty.***

