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

#### 1️⃣ Dashboard 1: Overview & Trend
<img width="760" alt="{1884184B-17A2-4B8B-8F3F-9C0A8F0DFE0C}" src="https://github.com/user-attachments/assets/8132ef8f-d68e-4e19-ab7d-d01a19bc0322" />


**📌 Analysis 1**

***Oberservations***
1. Vendor Reliability Score (North Star Metric) is strong but with notable past fluctuations:

- Overall, the Vendor Reliability Score is 8.80 and the Vendor Trust Score is very high (9.09), indicating generally good supplier reliability.
- However, the VENDOR RELIABILITY SCORE OVER TIME chart shows significant drops in Q3 of 2012, despite an impressive recovery afterward.

2. Key components of the Reliability Score show high performance:

- The On-time Delivery Rate is exceptionally good (99.36%)
- The Fulfilled Stocks Rate is 96.00% overall, and notably, Rejected Stocks has sharply decreased from high levels (8.16% in 2011, 11.21% in 2012) to less 5%  in 2013 and 2014, demonstrating significant improvement in quantity and quality fulfillment
- The Average Lead Time is 19.45 days, a key contributing factor to the score.

3. Clear differentiation in Reliability across vendors and shipping methods:

- The dashboard highlights vendors with the Highest Vendor Reliability Score (>9.30, e.g., Cruger Bike Company, Expert Bike Co) and those with the Lowest Vendor Reliability Score (<3.06, e.g., Merit Bikes, G & K Bicycle Corp.).
- The Overseas shipping method has a significantly lower Vendor Reliability Score (8.33) compared to other methods (8.80 - 8.85), indicating a specific area of weakness.



4. Procurement Costs are volatile and increasing, independent of Reliability Score:

- Total Cost has sharply increased and fluctuated heavily from mid-2013 to late 2014, despite improvements in the components contributing to the Vendor Reliability Score. This points to a significant cost management challenge not directly reflected in reliability metrics.

***Recommendations***

- Target Low-VRS Vendors: Focus on improving specific low-scoring vendors (e.g., Merit Bikes) across all VRS components
- Improve Overseas Shipping Reliability: Investigate and address the lower VRS for Overseas shipping
- Optimize Costs: Analyze and manage the recent sharp increase and volatility in Total Cost without compromising reliability
- Leverage Top Vendors: Strengthen partnerships with high-VRS suppliers (e.g., Cruger Bike Company)
- Set VRS Benchmarks: Define clear performance targets for VRS and its components




#### 2️⃣ Dashboard 2: Detail & Analysis I
<img width="752" alt="{3A31B8E1-844B-4613-B8D4-F8917375696B}" src="https://github.com/user-attachments/assets/14006539-10b9-4e04-897e-cf590f0df4af" />


**📌 Analysis 2**

***Oberservations***

- Historical Performance Trends
  + Ontime Delivery: Consistently at 100% across the board, demonstrating overall strong performance in meeting delivery deadlines
  + Fulfilled Stocks: Experienced a notable dip in Q1 2013 before recovering and stabilizing at high levels (around 96-97%). This highlights the potential for volatility in stock fulfillment, which could impact vendor reliability.

- Lead Times & On-Time Delivery
  + Overseas: Significantly longer lead times (17.1 days total) and the only method with a low On-time Delivery Rate (83.43%). This is a major detractor from its reliability
  + All Other Methods (Cargo, Express, Overnight, Truck): Consistent and shorter lead times (14.0 days total) with perfect 100% On-time Delivery Rates, indicating high reliability in meeting deadlines

- Fulfilled & Rejected Stocks
  + Cargo: While handling the largest volume of fulfilled stock (31.01%), it also has the highest percentage of rejected stock (39.36%). This indicates a significant quality or accuracy issue that undermines reliability despite on-time delivery
  + Overseas: Handles the smallest volume of fulfilled stock (10.49%) and has a relatively low rejected stock rate (10.29%). Its primary issue is timing, not necessarily stock accuracy
  + Overnight: Appears to be the most reliable in terms of stock fulfillment (highest fulfilled rate, lowest rejected rate).

***Recommendations***
- Channel Restructuring & De-risking:
  + Overseas: Reduce reliance for time-sensitive goods. Shift to Express/Overnight for high-priority items, accepting higher initial costs to avoid Total Cost of Failure (TCF) from delays and lost sales
  + Cargo: Implement strict at-source Quality Control (QC). Enforce a "Zero Tolerance" policy for rejected goods, compelling vendors to improve or be replaced

- Action-Oriented "Vendor Reliability Score":
  + Integrate Risk Factors: The score must reflect not just performance but also potential risk (e.g., volatility, single-source dependency)
  + Link Score to Order Allocation: Reward high-scoring vendors with increased orders; reduce/eliminate for low scores. Create financial leverage to drive improvement

- Proactive Forecasting & Early Warning Systems:
  + Real-time Visibility Platform: Invest in technology to track orders/inventory status to detect anomalies early
  + Predictive Analytics: Use data to anticipate risks (e.g., potential delays, stock shortages) before they materialize, enabling proactive decision-making

#### 3️⃣ Dashboard 3: Detail & Analysis II
<img width="754" alt="{65F1ED17-96B0-419B-9457-02D88364CB64}" src="https://github.com/user-attachments/assets/037e054b-823c-4fa7-bd8f-81aa6d4b07fc" />

**📌 Analysis 3**

***Oberservations***
- Cost Structure by Ship Method (Focus: Hidden Costs & Scale):
  + Cargo Dominance: "Cargo" is the overwhelmingly largest cost driver in both Subtotal Cost (29.24M) and Freight (1.59M / 39.66% of total freight). Critically, its Tax Amount is disproportionately high (2.34M / 45.83% of total tax), suggesting potential inefficiencies or unfavorable tax structures unique to Cargo shipments.
  + Overseas Cost vs. Performance: While "Overseas" has a significant Subtotal Cost (7.25M), its Freight (0.58M) and Tax (0.58M) are not the highest. This reinforces that its core problem (from Analysis I) is poor on-time delivery and long lead times, not necessarily inflated direct costs.

- Vendor Performance Deep Dive (Focus: Specific Weaknesses & Strengths):
  + Overall Strong On-time Delivery: Most vendors achieve 100% on-time delivery, which is excellent. However, a crucial few (implicitly causing the 99.36% average in Vendor Details, but explicitly seen in "Overseas" in Analysis I) are dragging down the overall reliability.
  + Critical Unreliability Flag: Proseware, Inc.: This vendor stands out as a major red flag with an extremely low Vendor Trust Score (1.25) and an "Unreliable" Supplier Reliability Score, despite a decent 94.80% Fulfilled Stocks Rate. Their significant Sub Total Cost (2.34M) indicates they represent a material operational risk.
  + Top Performers & Leverage: "Superior Bicycles" (highest Sub Total Cost, excellent performance, highest Credit Rating) represents a crucial strategic partner.

- Vendor Reliability vs. Trust Score (Focus: Metric Consistency & Actionability):
  + General Positive Correlation: Higher "Vendor Trust Score" generally correlates with higher "Vendor Reliability Score," as expected. Top Credit Rating vendors (Rating 1) exhibit both high trust and reliability.
  + Critical Anomaly: Credit Rating 5 vs. 4: The data shows a Credit Rating 5 vendor with a higher "Vendor Reliability Score" (approx. 7.8) than a Credit Rating 4 vendor (approx. 7.5). This inconsistency is a major flaw in the current scoring methodology or Credit Rating definition. If the COO relies on these scores, this discrepancy can lead to flawed strategic decisions.

***Recommendations***
- Optimize Shipping Portfolio for True Value:
  + Action: Shift volume from high-risk Cargo (high tax/rejections) and slow Overseas. Prioritize faster, reliable channels, even if direct freight costs are higher
  + Goal: Minimize Total Cost of Failure (TCF) from delays and rejections

- Implement Tiered Vendor Management:
  + Action: Categorize vendors (e.g., Strategic, At-Risk) based on a refined "Vendor Reliability Score"
  + Goal: For "At-Risk" vendors, enforce "Improve or Exit." For "Strategic" vendors, deepen partnerships to secure long-term reliability

- Elevate "Vendor Reliability Score" to Predictive Tool:
  + Action: Transform the "Vendor Reliability Score" into a "Predictive & Early Warning Tool"
  + Goal: Incorporate external risks and forecasting data so the score signals potential issues before they occur, enabling proactive strategic decisions


---

## 🔎 Final Conclusion & Recommendations  

**Conclusion**
- High Baseline, but Hidden Vulnerabilities: While the overall "Vendor Reliability Score" (8.80) is strong and on-time delivery is generally excellent (99.36%), deeper analysis reveals critical vulnerabilities:
  + Channel-Specific Risks: "Overseas" shipping is a consistent source of delay (83.43% on-time), while "Cargo" is a major source of rejected stock (39.36%) and unexplained high tax costs. These significantly erode true reliability and incur hidden costs.
  + Vendor-Specific Risks: Isolated, highly unreliable vendors like "Proseware, Inc." (Trust Score 1.25) pose substantial operational and financial risks despite contributing to overall spend.
  + Cost Management Gap: Total procurement costs are volatile and increasing, seemingly decoupled from improving reliability metrics, indicating a lack of cost optimization alongside performance.
- Opportunity for Proactive, Value-Driven Procurement: The current data allows for a shift from reactive problem-solving to a strategic, predictive, and value-optimizing procurement function.

👉🏻 Based on the insights and findings above, we would recommend Senior Manager to consider the following:  

- Optimize Shipping Channels:
  + Reallocate volume based on true channel value (including failure costs), not just freight. Reduce reliance on risky Cargo and Overseas for critical items.

- Tiered Vendor Management:
  + Categorize vendors (Strategic, At-Risk) using the corrected "Vendor Reliability Score."
  + For At-Risk vendors: Enforce an "Improve or Exit" policy.
  + For Strategic vendors: Deepen partnerships for stable supply.

- Elevate "Vendor Reliability Score" to Predictive Tool:
  + Fix scoring logic immediately for absolute reliability.
  + Integrate forecast and external risk data for the score to predict potential issues early, enabling proactive CPO decisions.

>**These actions will directly help the COO elevate the "Vendor Reliability Score," control hidden costs, and build a stronger supply chain.**
