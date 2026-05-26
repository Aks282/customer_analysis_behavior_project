# 🛍️ Customer Shopping Behavior Analysis
This project analyzes a retail customer shopping dataset (~3,900 records) to uncover behavioral trends across demographics, product categories, subscription status, and purchase channels. It combines SQL querying, Python-based EDA, and an interactive Power BI dashboard to deliver actionable business insights.

## Project Structure

```
customer-behavior-analysis/
│
├── customer_shopping_behavior.csv             # Raw dataset
├── customer_behavior_analysis_sql.sql         # SQL queries for business questions
├── customer_shopping_behavior_analysis.ipynb  # Python EDA notebook
└── customer_behavior_dashboard.pbix           # Power BI interactive dashboard
```

---

## Dataset Overview

The dataset contains **3,900 customer records** with **18 features** covering:

| Feature | Description |
|---|---|
| `Customer ID` | Unique customer identifier |
| `Age` | Customer age |
| `Gender` | Male / Female |
| `Item Purchased` | Name of the product bought |
| `Category` | Product category (Clothing, Footwear, etc.) |
| `Purchase Amount (USD)` | Transaction value |
| `Location` | US state |
| `Season` | Season of purchase |
| `Review Rating` | Customer rating (1–5) |
| `Subscription Status` | Whether the customer is subscribed |
| `Shipping Type` | Shipping method chosen |
| `Discount Applied` | Whether a discount was used |
| `Promo Code Used` | Whether a promo code was applied |
| `Previous Purchases` | Count of past purchases |
| `Payment Method` | Payment method used |
| `Frequency of Purchases` | How often the customer shops |

---

## Business Questions Answered

### SQL Analysis (`customer_behavior_analysis_sql.sql`)

The SQL script addresses 10 key business questions:

1. **Revenue by Gender** — Total revenue split between male and female customers
2. **Smart Discount Users** — Customers who used discounts yet spent above average
3. **Top-Rated Products** — Top 5 products by average review rating
4. **Shipping & Spending** — Average purchase amount by shipping type (Standard vs. Express)
5. **Subscriber Value** — Do subscribers spend more? Average spend and revenue comparison
6. **Discount-Heavy Products** — Which 5 products have the highest discount usage rate
7. **Customer Segmentation** — Classify customers as New, Returning, or Loyal based on purchase history
8. **Top Products per Category** — Top 3 most purchased items within each product category
9. **Repeat Buyers & Subscriptions** — Correlation between repeat buying (>5 purchases) and subscription
10. **Revenue by Age Group** — Revenue contribution broken down by customer age segments

### Python EDA (`customer_shopping_behavior_analysis.ipynb`)

The notebook covers:
- Data cleaning and preprocessing
- Univariate and bivariate analysis
- Distribution plots, correlation heatmaps, and category breakdowns
- Visualizations of purchasing frequency, seasonal trends, and payment preferences

### Power BI Dashboard (`customer_behavior_dashboard.pbix`)

An interactive dashboard featuring:
- Revenue by gender, age group, and category
- Subscription vs. non-subscription spend comparison
- Seasonal and geographic purchase trends
- Product performance and discount analysis

---

## Tools & Technologies

| Tool | Purpose |
|---|---|
| **PostgreSQL / SQL** | Business question querying & aggregation |
| **Python** (pandas, matplotlib, seaborn) | Exploratory data analysis |
| **Jupyter Notebook** | Interactive Python analysis |
| **Power BI** | Dashboard & data visualization |

---

## Getting Started

### Run the SQL Queries
1. Load `customer_shopping_behavior.csv` into your database as a table named `customer`
2. Open `customer_behavior_analysis_sql.sql` in your SQL client (PostgreSQL recommended)
3. Run queries individually or all at once

> **Note:** Query 10 references an `age_group` column — make sure to create this derived column before running it:
> ```sql
> ALTER TABLE customer ADD COLUMN age_group TEXT;
> UPDATE customer SET age_group =
>   CASE WHEN age < 25 THEN 'Gen Z'
>        WHEN age BETWEEN 25 AND 40 THEN 'Millennial'
>        WHEN age BETWEEN 41 AND 56 THEN 'Gen X'
>        ELSE 'Boomer+' END;
> ```

### Run the Python Notebook
```bash
pip install pandas matplotlib seaborn jupyter
jupyter notebook customer_shopping_behavior_analysis.ipynb
```

### Open the Power BI Dashboard
Open `customer_behavior_dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

---

## Key Insights

- Subscribed customers show notably higher average spend compared to non-subscribers
- A small set of products consistently receive the highest discount application rates
- The majority of customers fall in the "Returning" segment (2–10 previous purchases)
- Revenue distribution varies meaningfully across age groups and seasons

---


