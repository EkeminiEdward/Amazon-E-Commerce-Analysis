# Amazon E-Commerce Analytics & Executive Intelligence Dashboard

---

## ⚙️ Project Type Flags

-  Exploratory Data Analysis (EDA)
- [ ] SQL Analysis / Querying
-  Dashboard / Data Visualization
-  Data Pipeline / ETL
- [ ] Predictive Modelling / Machine Learning
-  Data Cleaning / Wrangling
- [ ] End-to-End (multiple of the above)
- [ ] Other: ___________

---

## 1. Project Overview

**Context:** This project presents an end-to-end Executive Business Intelligence solution built in Power BI using a large-scale Amazon e-commerce dataset containing over 1 million transaction records. The dashboard was designed to provide decision-makers with a centralized view of marketplace performance across sales, customers, products, sellers, inventory, and logistics operations.

The solution transforms data into actionable insights, enabling stakeholders to monitor business performance, identify growth opportunities, evaluate operational efficiency, and support strategic decision-making.

**Problem Statement:** E-commerce organizations generate large volumes of transactional data across multiple business functions. However, without a unified analytics platform, it becomes difficult to; monitor revenue and order performance, identify high-value customers and retention trends, evaluate product and seller effectiveness, detect inventory and fulfillment risks and to understand return behaviour and operational bottlenecks.

**Outcome:** The final solution delivers a scalable executive reporting framework that enables leadership to monitor marketplace performance, improve operational efficiency, optimize customer retention strategies, and support data-driven decision-making across the e-commerce value chain.

---

## 2. Objectives

- Analyze revenue performance across categories, locations, and sales channels.
- Segment customers based on purchasing behaviour and value contribution.
- Evaluate repeat purchase patterns and customer retention.
- Assess product and seller performance.
- Monitor inventory availability and operational efficiency.
- Identify delivery delays and return-risk hotspots.
- Deliver actionable insights through an executive-level dashboard experience.

---

## 3. Project Scope & Tools

### Scope

| Dimension | Details |
|-----------|---------|
| **In Scope** | Synthetic Amazon-style e-commerce transaction dataset, with 1 million rows, 20 columns, for 5 cities in India, Mar 2024-                  Mar 2026.
                Analysis covers revenue, return rates, payment method, product category, customer and seller performance.|
| **Out of Scope** | Customer demographics and marketing spend data were excluded -
                     demographic data was incomplete for two cities, and marketing
                     data sits in a separate system outside this engagement. |
| **Time Period** | March 2024-March 2026 |

### Tools & Technologies


| Category | Tool(s) Used |
|----------|-------------|
| Data Storage | CSV files |
| Data Processing | Power Query |
| Analysis | DAX |
| Visualization | Power BI |
| Version Control |  Git / GitHub |
| Documentation | Markdown |

---

## 4. Repository Structure

```
Amazon-ECommerce-PowerBI-Analytics/
│
├── data/                  
│   ├── ecommerce_dataset.csv
│
├── reports/                  
│   ├── Amazon_Ecommerce_Analytics_Executive_Intelligence_Dashboard.pbix
│
├── visuals/                  
│   ├── Executive_Overview.png
│   ├── Customer_Insights.png
│   ├── Product_Seller_Intelligence.png
│   ├── Operations_Delivery.png
│
├── documentation/            
│   ├── Data_Model.png
│
└── README.md                 
```

---

## 5. Data Workflow

```
[Data Source(s)]
      ↓
[Ingestion / Collection Method]
      ↓
[Cleaning & Transformation]
      ↓
[Analysis / Modelling / Querying]
      ↓
[Output / Visualisation / Reporting]
```

1. **Source:** Yearly synthetic Amazon-style E-commerce transaction dataset.
2.             A csv file with 1 million rows and 20 columns, covering Mar 2024 - Mar 2026.
3. **Ingestion:** Imported the csv file into Power BI, and proceeded to use the Power Query Editor to carry out data
4.                 preparation by cleaning and transforming the data, making it ready for analysis. 
5. **Cleaning:** Converted purchase_date column into a Date format.
6.               Removed unnecessary errors and duplicates.
7.               Set the data type for price, discount, final_price columns, as Decimal Number.
8.               Set the data type for rating, shipping_time_days, stock, review_count columns, as Whole Number.
9.               Set the data type for seller_rating, as Decimal Number (Verifying that the range is 2.5-5.0).
10. **Transformation:** Created a dedicated Date table for trend and time intelligence analysis.
11.                     Aggregated data to monthly and regional gains for trend analysis.
12.                     Created dimension tables for data modelling.
13.                     Optimized columns for reporting performance.
14. **Analysis:** Descriptive statistics, regional comparisons, return rate by product category, top performing products,
15.               delivery status breakdown, payment method distribution, etc.
16. **Output:** Summary report (PDF)

---

## 6. Data Model & Schema


### Dataset / Table: `Transaction_Facts`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `user_id` | string  | Unique customer identifier | U521020 |
| `product_id` | string  | Unique product identifier | P90848 |
| `category` | string | Top-level product category | Home |
| `subcategory` | string | Category subdivision | Furniture |
| `brand` | string | Product brand | Nike |
| `price` | decimal | Original listed price | 12006.66 |
| `discount` | decimal | Discount percentage applied | 41.83 |
| `final_price` | decimal | Price after discount | 6984.57 |
| `rating` | int | Product rating (1-5) | 4.4 |
| `review_count` | int | Total reviews (log-normal distribution) | 11 |
| `stock` | int | Available inventory units | 11 |
| `seller_id` | [string | Unique seller identifier | S8057 |
| `seller_rating` | decimal | Seller rating (2.5-5.0) | 2.8 |
| `purchase_date` | date | Transaction date | Friday, August 16, 2024 |
| `shipping_time_days` | int | Delivery time in days | 1 |
| `location` | string | Customer city | Delhi |
| `device` | string | Platform - Mobile/Web/Tablet | Mobile App |
| `payment_method` | string | UPI/Card/COD | UPI |
| `is_returned` | boolean | Return flag (True/False) | False |
| `delivery_status` | string | Final delivery outcome | Delayed |

### Dataset / Table: `Dim_User`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `user_id` | string  | Unique customer identifier | U521020 |
| `location` | string  | Customer city | Chennai |


### Dataset / Table: `Dim_Selller`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `seller_id` | string  | Unique seller identifier | S1771 |
| `seller_rating` | decimal  | Seller rating (2.5-5.0) | 2.9 |


### Dataset / Table: `Dim_Product`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `product_id` | string  | Unique product identifier | P29555 |
| `category` | string  | Top-level product category | Beauty |
| `subcategory` | string  | Category subdivision | Skincare |
| `brand` | string  | Product brand | HP |


### Dataset / Table: `Dim_Payment`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `payment_id` | int  | Unique payment identifier | 1 |
| `payment_method` | string  | UPI/Card/COD | UPI |


### Dataset / Table: `Dim_Device`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `device_id` | int  | Unique device identifier | 1 |
| `device` | string  | Platform - Mobile/Web/Tablet | Tablet |



### Dataset / Table: `Dim_Delivery`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `delivery_id` | int  | Unique delivery identifier | 1 |
| `delivery_status` | string  | Final delivery outcome | Returned |


> **Row count (approx.):** 1,000,000 rows
> **Date range:** Sunday, March 31, 2024 – Tuesday, March 31, 2026
> **Key join / relationship:** `Dim_User.user_id` → `Transaction_Facts.user_id`
                                `Dim_Product.product_id` → `Transaction_Facts.product_id`
                                `Dim_Seller.seller_id` → `Transaction_Facts.seller_id`
                                `Dim_Device.device_id` → `Transaction_Facts.device_id`
                                `Dim_Payment.payment_id` → `Transaction_Facts.payment_id`
                                `Dim_Delivery.delivery_id` → `Transaction_Facts.delivery_id`
                                `Dim_Date.date` → `Transaction_Facts.purchase_date`
                                ( All: One-to-many, single direction relationships.)


---

## 7. Analysis & Metrics



### Analytical Approach

This project followed a Business Intelligence and Descriptive Analytics approach to transform raw e-commerce transaction data into actionable executive insights. The analysis focused on answering key business questions across five major areas: Revenue Perfomance, Customer Intelligence, Product & Seller Performance, Operational Efficiency, and Risk Analysis.

The project moved from data preparation to data modelling to metric creation to visualization, and finally to business interpretation.

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `Revenue` | Sum of final_price | Measures total sales generated after discounts; primary business performance KPI |
| `Total Orders` | Count of all transaction records | Measures total purchase volume and business activity |
| `Unique Customers` | Distinct count of user_id | Measures the unique customers acquired or served |
| `Average Order Value (AOV)` | Revenue divided by Total Orders | Shows average customer spending per transaction |
| `Revenue per Customer` | Revenue divided by Unique Customers | Measures average customer value contribution |
| `Customer Segment` | Groups customers by revenue contribution | Identify High Value, Medium Value, and Low Value customers |
| `Repeat Customers` | Customers with more than one purchase | Measures customer loyalty and retention strength |
| `One-Time Customers` | Customers with only one purchase | Identifies acquisition without retention |
| `Average Product Rating` | Average of product ratings | Measure customer satisfaction and product quality perception |
| `Product Review Count` | Total product reviews | Measures product popularity and customer engagement |
| `Seller Revenue Contribution %` | Seller Revenue divided by Revenue | Shows each seller's share of marketplace revenue |
| `Average Seller Rating` | Average seller rating | Measures seller reliability and service quality |
| `Revenue by Location` | Revenue grouped by location | Measures regional sales performance |
| `Inventory Availability` | Sum of available stock | Tracks current inventory capacity |
| `Total Returns` | Count of returned transactions | Measures return volume and operational impact |
| `Return Rate %` | Total Returns divided by Total Orders | Measures customer dissatisfaction and product/service issues |
| `Delivery Count` | Count of deliveries/transactions | Measures fulfillment activity |
| `Delivered Orders` | Orders with delivered status | Measures successful order fulfillment |
| `Delivery Success Rate %` | Delivered Orders divided by Total Orders | Evaluates logistics effectiveness |
| `Delayed Delivery Count` | Orders exceeding delivery threshold | Identifies shipping performance problem |
| `Average Shipping Time` | Average delivery days | Measures logistics speed and customer experience |
| `Customer Type` | Classifies customers by purchase frequency | Separates repeat vs one-time buyers |
| `Revenue Trend` | Revenue over time | Tracks business growth and seasonality |
| `Purchase Frequency` | Number of purchases per customer | Measures customer engagement level |

### Methods Used

- Descriptive statistics - distribution analysis, comparative analysis.
- Trend analysis across March 2024 - March 2026.
- Segmentation analysis / group comparison by High Value, Medium Value, and Low Value.
- Retention analysis - repeat customer classification, purchase frequency analysis.
- Pewrformance analysis - product performance, seller performance, delivery performance.
- Inventory analysis - stock aggregation, target comparison.
- Return risk analysis - return rate calculation, location analysis, device analysis, heatmap visualization.

---

## 8. Key Insights


**Insight 1: Return Rates, not sales volume, explain the underperformnce in Hyderabad, Chennai and Bangalore**
These three cities (Hyderabad, Chennai, Bangalore) had return rates of 36.05%, 36.32% and 36.35% respectively - more than the company average of 35.04%. Revenue was not lost at the point of sale; it was lost post-sale through refunds. This points to a fulfillment or product quality issue specific to these cities, not a demand problem.

**Insight 2: Highest-performing product category**
Electronics, had the best performance in the product category, with highest revenue of $6.5 billion. The business may have dependency risk. While Clothing had worst performance in the product category, with a revenue of $329 thousand.


**Insight 3: Customer groups that drive revenue**
Customers were grouped into three groups - High Value, Medium Value, Low Value - based on revenue contribution.
The report identifies that High-Value customers drive the most revenue, with of revenue of $4.7 billion. 

**Insight 4: Customer retention**
Repeat Customers and One-Time Customers were the two measures used to show whether revenue is supported by loyalty or acquisition.
High repeat customer percentage indicates; strong customer experience, product satisfaction, trust in marketplace.
The report identifies that the repeat customers had the highest percentage (57.08%) compared to the one-time customers' percentage of 42.92%.


**Insight 5: Product performance analysis**
The product performance was grouped into four groups; High Rating + High Revenue = Best products, High Rating + Low Revenue = Marketing Opportunity products, Low Rating + High Revenue = Quality Risk products, and Low Rating + Low Revenue = Product Improvement candidate.
A Samsung product, under the electronics category with the product_id P46010, had a high rating of 4.07 and a high revenue of $456 thousand, which made it to be the best product. A Lenovo product, in the sports category with the product_id P96839, had high rating of 4.50 and a low revenue of $48 thousand, which shows that it has a marketing opportunity. A Lenovo product, in the clothing category with a product_id P75806, had a low rating of 3.77 and a high revenue of $377 thousand, and that made it to be a quality risk product. Finally, another Samsung product in the electronics category with a aproduct_id P68624, had a low rating of 2.85 and a low revenue of $14 thousand, and that made it to be a product improvement candidate.


**Insight 6: Top revenue-generating sellers**
A seller with high revenue but poor rating represents marketplace risk. A highly rated seller with low revenue represents growth potential.
The seller with seller_id S4656, sold an electronic product and got a rating of 2.60 but made revenue of $670 thousand. That points to the fact that there might be a marketplace risk. Another seller with seller_id S7251, sold a home product and got a rating of 5.00 but made revenue of $60 thousand. This shows that there is a growth potential in that seller.

---

## 9. Recommendations


| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | Analyze: Top returned products, Seller contribution, Category patterns. | Insight 1 - return rate anomalyin Hyderbad, Chennai and Bangalore. | Operations |
| Medium | Strengthen High-Performing category (Electronics) by prioritizing; inventory availabilty, marketing campaigns and seller allocation. | Insight 2 - best performing product category. | Operations |
| Medium | Create a VIP retention strategy: For High Value customers; exclusive offers, loyalty benefits, early access campaigns. This approach will increase lifetime value and reduce churn risk. Also, move Medium Value customers into High Value customers through; bundled offers, cross-selling and personalized recommendations. | Insight 3 - customer groups that drive revenue. | Operations |
| High | Improve retention by; monitoring repeat purchase cycles, sending product recommendations, improving customer service response time, and reducing return rates. | Insight 4 - customer retention. | Operations |
| High | For Star products, increase; inventory, advertising, and seller visibility. For Quality risk products, investigate; product defects, customer expectations, and description accuracy, because these products may generate revenue now but damage long-term trust. For Marketing opportunity products, improve; search ranking, promotions, and product visibility. | Insight 5 - product performance analysis  | Operations |
| High | For sellers with marketplace risk, apply; quality monitoring, customer complaint review, and performance improvement plans. For sellers with growth potential, support with; better product placement, promotional visibility, and increased traffic allocation. | Insight 6 - top revenue-generating sellers | Operations |

---

## 10. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| Amazon E-Commerce Executive Overview | Contains a high-level view of business performance. | visuals/Executive Overview.png |
| Customer Insights | Focuses on customer behaviour and retention. | visuals/Customer Insights.png |
| Product & Seller Intelligence | Analyzes marketplace performance. | visuals/Product & Seller Intelligence.png |
| Operations & Delivery Report | Monitors fulfillment and operational performance. | visuals/Operations & Delivery Report.png |
| Data Model | A Star schema data model was implemented |  |

---

## 11. Author

**Ekemini Edward**
Data Analyst

- 🔗 [LinkedIn URL]
- 💼 [Portfolio or GitHub profile URL]
- 📧 [Email - optional]

---

*Last updated: [Month YYYY]*
*If this template helped you, consider starring the repository.*
