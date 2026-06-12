# Retail Sales & Customer Behavior Analysis — Tableau Dashboard

Interactive Tableau dashboards built on the **Online Retail** transactional dataset (UK-based online retailer, Dec 2010 – Dec 2011), covering sales trends, geographic performance, customer segmentation, and top products.

🔗 **Live Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/YOUR_PROFILE/viz/YOUR_WORKBOOK_NAME) *(replace with your published link)*

## 📂 Repository Contents

```
├── Retail_Sales_Customer_Behavior.twb   # Tableau workbook (open in Tableau Desktop/Public)
├── data/
│   ├── retail_monthly_summary.csv       # Revenue, quantity, orders by month
│   ├── retail_daily_summary.csv         # Revenue, quantity, orders by day
│   ├── retail_country_summary.csv       # Revenue, quantity, orders, customers by country
│   ├── retail_customer_summary.csv      # Per-customer revenue, orders, RFM-based segment
│   └── retail_product_summary.csv       # Revenue, quantity, orders by product
├── Retail_Sales_Customer_Behavior_Analysis_Colab.ipynb  # Source notebook (EDA + data prep)
└── README.md
```

## 📊 Dashboards

### 1. Sales Overview
- **Monthly Revenue Trend** — line chart of total revenue by month, highlighting seasonality (Nov/Dec peak).
- **Daily Sales Trend** — daily revenue trajectory across the full period.
- **Revenue by Country** — bar chart ranking countries by revenue (UK dominates ~85%+ of sales).
- **Quantity vs Orders** — monthly units sold vs. order count, colored by order volume.

### 2. Customer & Product Insights
- **Customer Segments** — customers grouped into segments (e.g., High Value, Medium, Low) sized by total revenue contribution.
- **Top Products by Revenue** — best-selling SKUs ranked by revenue generated.
- **Monthly Revenue Trend** — repeated for cross-referencing with customer/product patterns.

## 🚀 How to Use

1. Clone this repo and keep the folder structure intact (the `.twb` references CSVs via the relative `data/` path).
2. Open `Retail_Sales_Customer_Behavior.twb` in **Tableau Desktop** (free with Tableau Public) — version 2023.1+ recommended.
3. Tableau will load each CSV as a separate data source automatically.
4. Explore the two dashboards via the tabs at the bottom: **Sales Overview** and **Customer & Product Insights**.

> 💡 To publish on **Tableau Public**, use *File → Save to Tableau Public* once the workbook is open — this packages the data and workbook together as a `.twbx`.

## 🏗️ Build From Scratch (Tableau Public)

If you'd rather rebuild the dashboards manually:

1. Download [Tableau Public](https://public.tableau.com) and connect each CSV in `data/` as a Text File data source.
2. Create 6 worksheets:
   - **Monthly Revenue Trend** — `month` → Columns, `total_revenue` → Rows, Line chart
   - **Daily Sales Trend** — `date` → Columns, `total_revenue` → Rows, Line chart
   - **Revenue by Country** — `country` → Rows, `total_revenue` → Columns, Bar chart (sorted desc)
   - **Customer Segments** — `customer_segment` → Columns, `total_revenue` → Rows, Bar chart
   - **Top Products by Revenue** — `description` → Rows, `total_revenue` → Columns, Bar chart (Top 10 filter)
   - **Quantity vs Orders** — `month` → Columns, `total_quantity` → Rows, `order_count` → Color
3. Create 2 dashboards and drag sheets into a grid layout:
   - **Sales Overview**: Monthly Revenue Trend, Daily Sales Trend, Revenue by Country, Quantity vs Orders
   - **Customer & Product Insights**: Customer Segments, Top Products by Revenue
4. *File → Save to Tableau Public As...* to publish and get a shareable link.

## 🛠️ Data Pipeline

The summary CSVs were generated from the raw `Online_Retail.xlsx` dataset via the included Colab notebook, which performs:
- Cleaning (removing cancelled orders, nulls, negative quantities)
- Revenue calculation (`quantity × unitprice`)
- Aggregation by month, day, country, customer, and product
- Customer segmentation (High / Medium / Low value based on total revenue & order frequency)

## 📈 Key Insights

- UK accounts for the overwhelming majority of revenue, with Netherlands, EIRE, Germany, and France as the next largest markets.
- Revenue peaks sharply in **November**, driven by pre-holiday wholesale ordering.
- A small group of "High Value" customers contributes a disproportionate share of total revenue (Pareto pattern).
- "DOTCOM POSTAGE" and "REGENCY CAKESTAND 3 TIER" are among the top revenue-generating line items.

## 🧰 Tools Used
- Python (pandas) for data cleaning & aggregation
- Tableau Desktop / Public for visualization

---
*Dataset source: UCI Machine Learning Repository — Online Retail Data Set.*
