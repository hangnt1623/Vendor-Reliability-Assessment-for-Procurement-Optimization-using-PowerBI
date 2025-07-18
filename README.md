# Vendor Reliability Assessment for Procurement Optimization using PowerBI

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
This project focuses on building an Operation Dashboard for **Adventure Works**. The primary goal is to visually assess **vendor performance**, providing leadership with clear, data-driven insights to optimize **procurement** and strengthen the **supply chain**.  
The goal is to:
- Ensure **optimal procurement**: Get the **sufficient goods**, **delivery on time**, at the **best price**  
- Strengthen the **supply chain**: Identify and manage **top-performing** and **underperforming suppliers**  
- Support **data-driven decisions**: Empower leadership with clear insights for better **purchasing strategies**


### 👤 Who is this project for?  

✔️ Chief Executive Officer (CEO)

✔️ Chief Operating Officer (COO)

✔️ Chief Procurement Officer (CPO)/Head of Purchasing

###  ❓Business Questions:  

✔️ Assess **vendor fulfillment accuracy** by analyzing whether suppliers consistently provide the **correct and sufficient quantities** of goods and materials as ordered

✔️ Evaluate **vendor delivery performance** by understanding how effectively our suppliers are meeting **agreed-upon delivery timelines**

✔️ Determine **supplier credibility** and **reliability** by examining factors that demonstrate their **trustworthiness** and consistent adherence to **commitments**

✔️ Optimize **procurement costs** by analyzing **vendor pricing** and overall **expenditure** to ensure the **best value** for **Adventure Works**



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
The dataset includes 5 main tables:

- **Product**: Details of products sold or used in manufacturing  
- **Purchase Order Detail**: Line-item data for each purchase order  
- **Purchase Order Header**: Overall info for each purchase order  
- **Product Vendor**: Links vendors to the products they supply  
- **Vendor**: Information about companies supplying goods

Additional tables derived from the above:

- **Product Price**: Product pricing details  
- **Purchase Order**: Combined detail and header info  
- **Date**: Standardized date information  
- **Ship Method**: Shipping method details


#### 2️⃣ Data Relationships

<img width="690" alt="{467EDCAA-DD07-44CE-A217-9064C290F0D5}" src="https://github.com/user-attachments/assets/6c9a784b-3f22-4d44-bac3-a9e95ef7c01f" />

---

## 🧠 Design Thinking Process  

Explain the step-by-step approach taken to solve the problem.  

**1️⃣ Empathize**

***(1) 5W1H*** 

<img width="685" alt="{FB59653B-B620-4EEA-BEDA-7AD02224ED4A}" src="https://github.com/user-attachments/assets/a379e3d4-1109-4388-ac61-713db7ce752a" />

***(2) Empathy Map & Stakeholder need***

<img width="685" alt="{50DE9CB0-1E7E-4C7A-877F-5812E419161D}" src="https://github.com/user-attachments/assets/c9e9aaf1-ce3e-4092-a97a-08cc65f6d1e0" />


**2️⃣ Define point of view**

***(1) North Star Metric***

<img width="687" alt="{33BF4370-4AF5-4209-A476-092308A558F4}" src="https://github.com/user-attachments/assets/35d5d710-0bca-43d4-878b-3437e7f46a98" />

***(2) Point of view*** 

<img width="690" alt="{1DE6A1C3-F407-439E-9A66-16F9A11482A6}" src="https://github.com/user-attachments/assets/b28b5ee4-ecdc-480b-ac9b-7403436af263" />


**3️⃣ Ideate**

<img width="683" alt="{D4DBDDE5-5757-45CF-AF36-72B7D1507892}" src="https://github.com/user-attachments/assets/19a3ffed-c447-479c-bfba-ebe7b73d1e61" />


---

## 📊 Key Insights & Visualizations  

### 🔍 Dashboard Preview & Analysis

#### 1️⃣ Dashboard 1: Overview & Trend

<img width="767" height="417" alt="{815E0C32-72BC-4962-9D11-F2653654A999}" src="https://github.com/user-attachments/assets/711c393b-2792-476b-91c6-2cb6ca54d129" />


**📌 Analysis 1**

***Oberservations***
- **Vendor Reliability Score (North Star Metric)**:
  + Overall strong (Score: 8.80, Trust Score: 9.09), indicating good supplier reliability. -> Adventure Works generally benefits from a trustworthy and reliable supplier base, which is foundational for stable operations.
  + Critical Fluctuations: Significant drops in Q1 2011, Q3 2011, and Q4 2014 directly correlate with missing cost data. -> These periods represent significant operational vulnerabilities or data integrity issues. The simultaneous drop in reliability and missing cost data suggests severe disruptions that likely hampered both performance and financial visibility, posing a risk to procurement planning and historical analysis.
  
- **Key components of the Reliability Score show high performance**:
  + On-time Delivery Rate is exceptionally good (99.36%) -> This high rate indicates highly effective logistics management and reliable fulfillment of delivery promises by suppliers. It directly supports maintaining production schedules and inventory levels, minimizing operational delays.
  + Improved Stock Fulfillment: 96.00% fulfilled. Rejected Stocks dramatically decreased from 8.16% (2011) and 11.21% (2012) to <5% (2013-2014). -> The substantial reduction in rejected stocks is a major success in quality and quantity control. This suggests improved supplier vetting, better communication of requirements, or enhanced incoming inspection processes, directly leading to less waste, fewer production stoppages, and better inventory accuracy.
  + The Average Lead Time is 19.45 days, a key contributing factor to the score.

- **Clear differentiation in Reliability across vendors and shipping methods**:
  + The dashboard highlights vendors with the Highest Vendor Reliability Score (>9.30, e.g., Cruger Bike Company, Expert Bike Co) and those with the Lowest Vendor Reliability Score (<3.06, e.g., Merit Bikes, G & K Bicycle Corp.)
  + The Overseas shipping method has a significantly lower Vendor Reliability Score (8.33) compared to other methods (8.80 - 8.85), indicating a specific area of weakness.

- **Procurement Costs are volatile and increasing, independent of Reliability Score**:
  + Total Cost has sharply increased and fluctuated heavily from mid-2013 to late 2014, despite improvements in the components contributing to the Vendor Reliability Score. This points to a significant cost management challenge not directly reflected in reliability metrics.

- **Freight & Tax Dynamics**
  + After Q2 2013, Freight Amount consistently surpassed Tax Amount -> This indicates a shift in cost structure, likely due to increased shipping distances, rising fuel prices, higher volumes, or a reliance on more expensive shipping methods. This trend directly contributes to the overall rising costs and highlights freight as a key area for cost optimization strategies.

***Recommendations***

- **Target Low-VRS Vendors**: Focus on improving specific low-scoring vendors (e.g., Merit Bikes) across all VRS components
- **Improve Overseas Shipping Reliability**: Investigate and address the lower VRS for Overseas shipping
- **Optimize Costs**: Analyze and manage the recent sharp increase and volatility in Total Cost without compromising reliability
- **Leverage Top Vendors**: Strengthen partnerships with high-VRS suppliers (e.g., Cruger Bike Company)
- **Set VRS Benchmarks**: Define clear performance targets for VRS and its components


#### 2️⃣ Dashboard 2: Detail & Analysis I

<img width="766" height="419" alt="{867DE10B-935F-4C54-AD67-82856C03660E}" src="https://github.com/user-attachments/assets/08545ae9-69ed-46f5-9682-2327a3fa2aff" />


**📌 Analysis 2**

***Oberservations***

- **Overall Delivery & Fulfillment**:
  + On-time Delivery: Consistently high (98-100%), demonstrating strong performance in meeting deadlines across most methods.
  + Fulfilled Stocks: Generally high, but February and August dips highlight recurring volatility that needs investigation.

- **Shipping Method Performance**:
  + Overseas: The primary reliability bottleneck due to significantly longer lead times (17.1 days total) and the only low On-time Delivery Rate (83.43%). Its issue is timing, not stock accuracy (low rejection rate).
  + Cargo: Handles the largest fulfilled volume (31.01%) but has an unacceptably high rejection rate (39.36%). This indicates major quality or accuracy issues undermining its value despite on-time delivery.
  + Other Methods (Express, Overnight, Truck): Exhibit exceptional reliability with 100% On-time Delivery and shorter, consistent lead times (14.0 days total), making them highly efficient.
  + Overnight: Appears to be the most reliable for stock fulfillment (high fulfilled rate, likely lowest rejected rate), ideal for critical orders.

***Recommendations***
- **Channel Restructuring & De-risking**:
  + Overseas: Reduce reliance for time-sensitive goods. Shift to Express/Overnight for high-priority items, accepting higher initial costs to avoid Total Cost of Failure (TCF) from delays and lost sales
  + Cargo: Implement strict at-source Quality Control (QC). Enforce a "Zero Tolerance" policy for rejected goods, compelling vendors to improve or be replaced

- **Action-Oriented "Vendor Reliability Score"**:
  + Integrate Risk Factors: The score must reflect not just performance but also potential risk (e.g., volatility, single-source dependency)
  + Link Score to Order Allocation: Reward high-scoring vendors with increased orders; reduce/eliminate for low scores. Create financial leverage to drive improvement

- **Proactive Forecasting & Early Warning Systems**:
  + Real-time Visibility Platform: Invest in technology to track orders/inventory status to detect anomalies early
  + Predictive Analytics: Use data to anticipate risks (e.g., potential delays, stock shortages) before they materialize, enabling proactive decision-making

#### 3️⃣ Dashboard 3: Detail & Analysis II

<img width="766" height="417" alt="{BDFFF827-CF6F-4136-9B34-4CFE09A463BA}" src="https://github.com/user-attachments/assets/2423c998-f267-4d3c-98a4-f103bd953881" />


**📌 Analysis 3**

***Oberservations***
- **Cost Structure by Ship Method** (Focus: Hidden Costs & Scale):
  + Cargo Dominance: "Cargo" is the overwhelmingly largest cost driver in both Total Cost (32.31M) and Freight (1.59M / 39.66% of total freight). Critically, its Tax Amount is disproportionately high (2.34M / 45.83% of total tax), suggesting potential inefficiencies or unfavorable tax structures unique to Cargo shipments.
  + Overseas Cost vs. Performance: While "Overseas" has a significant Total Cost (8.00M), its Freight (0.58M) and Tax (0.58M) are not the highest. This reinforces that its core problem (from Analysis I) is poor on-time delivery and long lead times, not necessarily inflated direct costs.
 
- **Vendor Reliability vs. Trust Score** (Focus: Metric Consistency & Actionability):
  + General Positive Correlation: Higher "Vendor Trust Score" generally correlates with higher "Vendor Reliability Score," as expected. Top Credit Rating vendors (Rating 1) exhibit both high trust and reliability.
  + Critical Anomaly: Credit Rating 5 vs. 4: The data shows a Credit Rating 5 vendor with a higher "Vendor Reliability Score" (approx. 7.8) than a Credit Rating 4 vendor (approx. 7.5). This inconsistency is a major flaw in the current scoring methodology or Credit Rating definition. If the COO relies on these scores, this discrepancy can lead to flawed strategic decisions.

- **Vendor Performance Deep Dive** (Focus: Specific Weaknesses & Strengths):
  + Overall Strong On-time Delivery: Most vendors achieve 100% on-time delivery, which is excellent. However, a crucial few (implicitly causing the 99.36% average in Vendor Details, but explicitly seen in "Overseas" in Analysis I) are dragging down the overall reliability.
  + Critical Unreliability Flag: Proseware, Inc.: This vendor stands out as a major red flag with an extremely low Vendor Trust Score (1.25) and an "Unreliable" Supplier Reliability Score, despite a decent 94.80% Fulfilled Stocks Rate. Their significant Sub Total Cost (2.34M) indicates they represent a material operational risk.
  + Top Performers & Leverage: "Superior Bicycles" (highest Sub Total Cost, excellent performance, highest Credit Rating) represents a crucial strategic partner.


***Recommendations***
- **Optimize Shipping Portfolio for True Value**:
  + Action: Shift volume from high-risk Cargo (high tax/rejections) and slow Overseas. Prioritize faster, reliable channels, even if direct freight costs are higher
  + Goal: Minimize Total Cost of Failure (TCF) from delays and rejections

- **Implement Tiered Vendor Management**:
  + Action: Categorize vendors (e.g., Strategic, At-Risk) based on a refined "Vendor Reliability Score"
  + Goal: For "At-Risk" vendors, enforce "Improve or Exit." For "Strategic" vendors, deepen partnerships to secure long-term reliability

- **Elevate "Vendor Reliability Score" to Predictive Tool**:
  + Action: Transform the "Vendor Reliability Score" into a "Predictive & Early Warning Tool"
  + Goal: Incorporate external risks and forecasting data so the score signals potential issues before they occur, enabling proactive strategic decisions


---

## 🔎 Final Conclusion & Recommendations  

**Conclusion**
- **High Baseline, but Hidden Vulnerabilities**: While the overall **Vendor Reliability Score** (8.80) is strong and **on-time delivery** is generally excellent (99.36%), deeper analysis reveals **critical vulnerabilities**:  
  + **Channel-Specific Risks**: "**Overseas**" shipping is a consistent source of **delay** (83.43% on-time), while "**Cargo**" is a major source of **rejected stock** (39.36%) and **unexplained high tax costs**. These significantly erode **true reliability** and incur **hidden costs**.  
  + **Vendor-Specific Risks**: Isolated, highly **unreliable vendors** like "**Proseware, Inc.**" (**Trust Score** 1.25) pose substantial **operational** and **financial risks** despite contributing to overall **spend**.  
  + **Cost Management Gap**: Total **procurement costs** are **volatile** and **increasing**, seemingly **decoupled** from improving **reliability metrics**, indicating a lack of **cost optimization** alongside performance.

- **Opportunity for Proactive, Value-Driven Procurement**: The current data allows for a shift from **reactive problem-solving** to a **strategic**, **predictive**, and **value-optimizing** procurement function.

**👉🏻 Based on the insights and findings above, we would recommend COO to consider the following:**

- **Optimize Shipping Channels**:  
  + **Reallocate volume** based on **true channel value** (including **failure costs**), not just freight. Reduce reliance on **risky Cargo** and **Overseas** for **critical items**.

- **Tiered Vendor Management**:  
  + **Categorize vendors** (**Strategic**, **At-Risk**) using the corrected **Vendor Reliability Score**.  
  + For **At-Risk vendors**: Enforce an "**Improve or Exit**" policy.  
  + For **Strategic vendors**: **Deepen partnerships** for **stable supply**.

- **Elevate "Vendor Reliability Score" to Predictive Tool**:  
  + **Fix scoring logic** immediately for **absolute reliability**.  
  + **Integrate forecast** and **external risk data** for the score to **predict potential issues early**, enabling **proactive COO decisions**.


>**These actions will directly help the COO elevate the "Vendor Reliability Score," control hidden costs, and build a stronger supply chain.**
