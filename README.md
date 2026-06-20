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

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Workflow](#5-data-workflow)
6. [Data Model & Schema](#6-data-model--schema)
7. [ERD - Entity Relationship Diagram](#7-erd--entity-relationship-diagram) *(SQL projects)*
8. [Analysis & Metrics](#8-analysis--metrics)
9. [Key Insights](#9-key-insights)
10. [Recommendations](#10-recommendations)
11. [Assumptions & Limitations](#11-assumptions--limitations)
12. [Future Enhancements](#12-future-enhancements)
13. [Deliverables](#13-deliverables)
14. [Author](#14-author)

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

<!--
  Explain what you measured and how - before you share what you found.

  WHAT GOOD LOOKS LIKE:
  Metric: "Customer Return Rate"
  Definition: "Number of transactions flagged as returns divided by total
               transactions, calculated at product-category and regional grain."
  Why It Matters: "Return rate - not sales volume - was hypothesised to
                  explain regional revenue gaps. This metric tests that hypothesis."

  WHAT TO AVOID:
  ❌ Defining a metric only in code: SUM(returns) / COUNT(transaction_id)
     That's an implementation. Write the plain-language definition here.
     Both belong in your project - the definition in the README,
     the implementation in the code.
-->

### Analytical Approach

[Describe how you approached the analysis. Were you exploring patterns? Testing a hypothesis? Building and validating a pipeline? Be honest about your method - exploratory work is valid, just call it that.]

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `[Metric 1]` | [What it measures, in one sentence] | [What decision or question it answers] |
| `[Metric 2]` | [What it measures, in one sentence] | [What decision or question it answers] |
| `[Metric 3]` | [What it measures, in one sentence] | [What decision or question it answers] |

### Methods Used

- [e.g., Descriptive statistics - distribution, central tendency, outlier detection]
- [e.g., Trend analysis across [time period]]
- [e.g., Segmentation / group comparison by [dimension]]
- [e.g., Correlation analysis between [variable A] and [variable B]]
- [e.g., SQL window functions for [specific aggregation]]
- [e.g., Custom aggregation or transformation logic in [tool]]

---

## 9. Key Insights

<!--
  Findings + implications. Not just what happened - what it means.

  WHAT GOOD LOOKS LIKE:
  ✅ "Return rates, not sales volume, explain Region A's underperformance.
      Region A's return rate on home goods was 34% - more than double the
      company average. Revenue was not lost at the point of sale; it was
      lost post-sale through refunds. This points to a fulfilment or
      product quality issue specific to that region, not a demand problem."

  WHAT TO AVOID:
  ❌ "Region A had lower revenue than other regions in Q4."
     (That's an observation. It describes what happened.
      An insight says what it means and where to look next.)

  Aim for 3–6 insights. Quality over quantity.
-->

**Insight 1: [Short descriptive headline]**
[What you found + what it suggests. One short paragraph.]

**Insight 2: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 3: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 4 (if applicable): [Short descriptive headline]**
[What you found + what it suggests.]

---

## 10. Recommendations

<!--
  Action-oriented. Addressed to a real audience.
  Tied explicitly to the insight that supports each one.

  WHAT GOOD LOOKS LIKE:
  Priority: High
  Recommendation: "Conduct a fulfilment audit for home goods deliveries
                   in Region A - specifically investigating whether returns
                   correlate with a particular warehouse, carrier, or SKU batch."
  Based On: Insight 1 - return rate anomaly in Region A
  Owner: Operations / Supply Chain team

  WHAT TO AVOID:
  ❌ "Improve the return rate."
     (Not actionable. Doesn't say who, how, or where to start.)
  ❌ "Further analysis is needed."
     (This is a placeholder, not a recommendation.)
-->

| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Medium | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Low | [Exploratory or longer-term suggestion] | [Insight it comes from] | [Who should act] |

---

## 11. Assumptions & Limitations

<!--
  WHAT GOOD LOOKS LIKE:
  Assumption: "Transaction records were assumed to be complete for all five regions.
               No validation was performed against source system record counts."
  Limitation: "The analysis cannot distinguish between returns initiated by
               the customer vs. returns initiated by the business (e.g., recalls).
               If business-initiated returns are concentrated in Region A, the
               return rate finding may reflect a policy decision, not a quality issue."

  WHAT TO AVOID:
  ❌ Leaving this section blank or writing "None known."
     Every project has limitations. Documenting them is a sign of
     analytical maturity - not a confession of failure.
-->

### Assumptions
- [What did you treat as true without being able to verify?]
- [What simplifications did you make for scope or feasibility?]
- [What domain rules or definitions did you accept as given?]

### Limitations
- [What gaps exist in the data?]
- [What analysis was out of scope but could affect interpretation?]
- [What would a more rigorous version of this project include?]
- [Are there known biases in the data source or collection method?]

> *The goal here is pre-emptive Q&A. What would a thoughtful skeptic push back on? Document the answer here, before they ask.*

---

## 12. Future Enhancements

<!--
  WHAT GOOD LOOKS LIKE:
  ✅ "Automate the monthly data pull from the POS export folder using
      a scheduled Python script, replacing the current manual process."
  ✅ "Expand the return rate analysis to include carrier-level data,
      which was unavailable in this dataset but exists in the logistics system."

  WHAT TO AVOID:
  ❌ "Add a machine learning model."
     (Vague, and disconnected from the actual findings of this project.)
  ❌ Listing aspirational features that don't follow logically from the work.
-->

- [ ] [Enhancement 1 - specific and traceable to a real gap in this project]
- [ ] [Enhancement 2]
- [ ] [Enhancement 3]
- [ ] [Enhancement 4]

---

## 13. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |

---

## 14. Author

**[Your Name]**
[Your role or title - current or target]

- 🔗 [LinkedIn URL]
- 💼 [Portfolio or GitHub profile URL]
- 📧 [Email - optional]

---

*Last updated: [Month YYYY]*
*If this template helped you, consider starring the repository.*
