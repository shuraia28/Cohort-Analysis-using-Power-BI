Customer Analytics Dashboard — Power BI

A comprehensive 4-page Power BI dashboard built on a retail 
transaction dataset to analyze customer behavior, retention, 
loyalty, and lifecycle patterns.

### Page 1 — 🏪 Retail Customers Analysis
<img width="1481" height="832" alt="Customer Analysis" src="https://github.com/user-attachments/assets/0f366cd0-e008-4a13-8324-9b51c2e208df" />
> **Purpose:** High-level executive summary of overall 
> retail performance.

**Key KPIs displayed:**
- 🟡 **Active Customers:** 5,878
- 🟡 **New Customers:** 5,878
- 🟡 **Sales Amount:** $17.74M
- 🟡 **Ordered Quantity:** 10.71M
- 🟡 **Average Price:** $3.21

**Visuals:**
- 📋 **Monthly Summary Table** — Breakdown of Active 
  Customers, New Customers, and Sales Amount by Month-Year
- 📈 **New Customers by Year and Month** — Area/line chart 
  tracking new customer acquisition trends from Jan 2010 
  to Jul 2012, revealing seasonality and growth patterns

**Insight Highlight:**  
October 2010 recorded the highest single-month active  
customers (1,497) with sales of $1,036,680, marking a  
notable peak in the dataset.

---

### Page 2 — 🔍 Customer Behavior Insights


<img width="1473" height="827" alt="Customer Behaviour" src="https://github.com/user-attachments/assets/ac845803-a77d-4f48-96b2-0fcdd0b02dbd" />


> **Purpose:** Deep-dive into cohort-level retention and 
> churn analysis.

**Tabs / Views available:**
- Cohort Performance
- Churned Customers
- Churned Rate
- **Retention Rate** *(highlighted/active)*

**Visuals:**
- 🗂️ **Cohort Retention Matrix** — A month-over-month 
  retention heatmap showing the percentage of customers 
  from each acquisition cohort (starting Dec 2009) who 
  returned in subsequent months (up to 24 months)

**How to read the matrix:**
- Rows = Acquisition cohort (month/year of first purchase)
- Columns = Months since first transaction (1 through 24)
- Values = % of original cohort still active that month

**Insight Highlight:**  
The December 2009 cohort shows the strongest long-term  
retention, maintaining ~19–30% activity through month 24,  
consistent with early loyal customer behavior.

---

### Page 3 — 🔄 Customer Lifecycle Overview


<img width="1482" height="830" alt="Customer Life_Cycle" src="https://github.com/user-attachments/assets/68b24a20-2fd4-47c1-92f1-ccd80fc8ee61" />


> **Purpose:** Tracks movement of customers through active, 
> lost, and recovered states over time.

**Visuals:**
- 📉 **Lost Customers by Month and Year** — Area chart 
  showing customer churn volume from Jan 2010 to Oct 2011, 
  with a notable spike approaching late 2011
- 📈 **Recovered Customers by Month and Year** — Area chart 
  showing win-back trends over the same period, peaking 
  around late 2011
- 📊 **New vs. Retained vs. Recovered Customers (Stacked 
  Bar)** — 100% stacked bar chart comparing the monthly 
  composition of:
  - 🟡 New Customers
  - 🟤 Retained Customers
  - ⚪ Recovered Customers

**Insight Highlight:**  
Retained customers consistently form the largest share of  
monthly activity. Recovery efforts show improvement post  
mid-2011, suggesting successful re-engagement campaigns.

---

### Page 4 — 💛 Customer Loyalty Analysis

<img width="1482" height="842" alt="Customer Loyalty" src="https://github.com/user-attachments/assets/b8df0957-ac91-4672-8346-dfa59e7933f7" />


> **Purpose:** Measures and monitors long-term loyalty 
> through retention and churn rate trends.

**Tabs / Views available:**
- **Retention Rate** *(active)*
- **Churned Rate**

**Visuals:**
- 📈 **Retention Rate & Churned Rate by Months** — Dual 
  line chart tracking both rates across 25 months since 
  first transaction

**Key Trends Observed:**

| Month | Retention Rate | Churn Rate |
|-------|---------------|------------|
| 1     | 0.0%          | 100.0%     |
| 2     | 22.7–23%      | 77–78%     |
| 5     | 81.0%         | 15–19%     |
| 15    | 88.6–89%      | 11%        |
| 25    | 96.8%         | 3.2%       |

**Insight Highlight:**  
After the initial steep churn in the first 2 months, the  
retention rate stabilizes rapidly and climbs steadily,  
reaching **96.8%** by month 25 — indicating a strong  
long-term loyal customer base among those who return  
after their initial purchase.

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — Dashboard development
- **DAX** — Custom measures and calculated columns
- **Power Query (M)** — Data transformation & cleaning
- **Star Schema** — Data modeling approach

---
## 🗃️ Data Modeling

<img width="1388" height="798" alt="Modeling" src="https://github.com/user-attachments/assets/ef71eaa1-17bc-44f1-b0a9-6bc0c1922817" />


The data model follows a **Star Schema** design with the 
following tables:

### Fact Table
- **FactSales** — Core transactional table containing:
  `Country`, `Customer ID`, `Invoice`, `InvoiceDate`,  
  `Month Since First Transaction`, `Price`

  ### Dimension Tables
- **DimCustomers** — Customer master table with  
  `Customer ID` and `First Transaction Month`
- **DimDate** — Date dimension with `Date` and  
  `Start of Month` for time intelligence

### Supporting Tables
- **_Measure** — Centralized DAX measures table  
  (e.g., `Active Customers`)
- **Retention Matrix** — Calculated table supporting  
  cohort-based retention analysis with  
  `Retention Matrix Fields` and `Retention Matrix Order`
- **Trend Analysis Metrics** — Table powering trend  
  visualizations with dynamic field parameters

### Relationships
| From | To | Cardinality |
|------|----|-------------|
| DimCustomers (Customer ID) | FactSales (Customer ID) | One-to-Many |
| DimDate (Date) | FactSales (InvoiceDate) | One-to-Many |

## 📊 Dataset Overview

The raw dataset contains transactional retail data with the 
following fields:

| Column        | Description                          |
|---------------|--------------------------------------|
| Invoice       | Unique invoice/order number          |
| StockCode     | Product identifier                   |
| Description   | Product name                         |
| Quantity      | Units purchased per transaction      |
| InvoiceDate   | Date and time of transaction         |
| Price         | Unit price of the product            |
| Customer ID   | Unique customer identifier           |
| Country       | Customer's country                   |

> Date range spans **December 2009 – late 2012**, primarily 
> covering UK-based retail customers.

---

## 🚀 How to Use

1. Clone this repository
2. Open `RetailCustomerAnalytics.pbix` in Power BI Desktop
3. If prompted, update the data source path to your local 
   dataset location
4. Refresh the data and explore all 4 pages

---

