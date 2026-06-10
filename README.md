# 🛒 Olist E-Commerce — Exploratory Data Analysis

## Overview
End-to-end exploratory data analysis on 100,000+ orders from **Olist**, Brazil's largest e-commerce marketplace (2016–2018). This project uncovers business insights across sales trends, delivery performance, customer reviews, product categories, geospatial patterns, customer segmentation, and seller performance.

---

## Dataset
**Brazilian E-Commerce Public Dataset by Olist**  
Source: [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)  
9 interconnected datasets · 100k orders · 2016–2018 · Real anonymised commercial data

---

## Tools & Libraries
- **Python** — Pandas, NumPy
- **Visualization** — Matplotlib, Seaborn
- **Notebook** — Jupyter / Kaggle Notebook
- **Version Control** — Git & GitHub

---

## Project Structure
```
olist-ecommerce-eda/
│
├── notebooks/
│   └── olist_eda.ipynb        ← Main analysis notebook
│
├── images/
│   └── monthly_revenue.png
│   └── delivery_by_state.png
│   └── review_by_delivery.png
│
└── README.md
```

---

## Analysis — 7 Story Arcs

### ✅ Arc 1 — Sales Trends & Seasonality
> *"When do customers buy and how has revenue grown over time?"*

**Approach:**
- Merged `orders` + `order_items` tables
- Engineered time features — year_month, day of week, hour of day
- Filtered to delivered orders only to measure real revenue

**Key Insights:**
- 📈 Olist revenue grew **3x between January and December 2017** — driven by steady organic growth
- 🛍️ A sharp **Black Friday spike in November 2017** produced the single highest revenue day — suggesting Olist should increase inventory and logistics capacity in October each year to handle the surge without delivery delays
- ⏰ **Peak ordering hours are 10am–4pm** — marketing emails and flash sale notifications should be scheduled in the morning to land before the peak window begins
- 📅 **Order volume is highest Monday–Tuesday** — weekly promotions should launch Sunday night to capture early-week buying intent

---

### ✅ Arc 2 — Delivery Performance
> *"Are orders reaching customers on time — and which states have the worst delays?"*

**Approach:**
- Engineered `delivery_delay` = actual delivery date − estimated delivery date
- Engineered `actual_delivery_days` = purchase date → delivery date
- Engineered `is_late` boolean flag
- Merged with `customers` table to analyse by state

**Key Insights:**
- ✅ **Olist delivers before its promised date in all 27 states** — suggesting estimates are deliberately padded as an under-promise, over-deliver strategy
- 🗺️ **Customers in remote northern states (RR, AP, AM) wait up to 29 days** — nearly **3.5x longer** than customers in São Paulo (8 days)
- 💸 **Customers in remote states pay higher freight costs yet wait longer** — freight pricing reflects distance, not service speed
- 🏭 Olist should either partner with regional carriers in northern states or open fulfillment centers in high-volume remote states to close the 20-day experience gap

---

### ✅ Arc 3 — Review Score Analysis
> *"What drives a bad review — is it the product or the delivery wait?"*

**Approach:**
- Merged orders with `order_reviews` table
- Created `delivery_status` column (Early / On Time / Late) using `np.select`
- Analysed average review score by delivery status
- Built crosstab of review score distribution per delivery status

**Key Insights:**
- ⭐ **Late orders average just 2.27 stars** vs 4.29 for early orders — a nearly **2 point drop** confirming delivery delay is the single biggest driver of negative reviews
- 😡 **53.7% of late orders receive 1 star** compared to only 6.6% of early orders
- 🤔 **16.5% of late orders still receive 5 stars** — suggesting some customers forgive delays when product quality is high or communication is good
- 📦 **6.6% of early orders still receive 1 star** — product quality issues (damaged goods, inaccurate descriptions, faulty items) are an independent driver of dissatisfaction regardless of delivery speed
- 🏪 Olist should implement stricter seller quality checks and monitor sellers with consistently high 1-star rates on early deliveries

---

### 🔄 Arc 4 — Product Category Deep Dive *(Coming soon)*
> *"Which categories drive the most revenue — and which have the worst customer satisfaction?"*

---

### 🔄 Arc 5 — Geospatial Analysis *(Coming soon)*
> *"Where are Olist's customers and sellers — and how does geography affect the business?"*

---

### 🔄 Arc 6 — RFM Customer Segmentation *(Coming soon)*
> *"Who are Olist's best customers — and who is at risk of churning?"*

---

### 🔄 Arc 7 — Seller Performance *(Coming soon)*
> *"Which sellers drive the most revenue — and do fast sellers get better reviews?"*

---

## Key Findings Summary

| Finding | Impact |
|---|---|
| Black Friday drives single biggest revenue spike | Plan logistics capacity in October |
| Peak orders: Monday–Tuesday, 10am–4pm | Time marketing campaigns accordingly |
| All 27 states receive orders before estimated date | Olist pads estimates deliberately |
| Remote states wait 3.5x longer than São Paulo | Logistics infrastructure gap |
| Late orders average 2.27 stars vs 4.29 for early | Delivery is #1 review driver |
| 6.6% of early orders still get 1 star | Product quality is independent issue |

---

## How to Run

1. Clone this repository
```bash
git clone https://github.com/yourusername/olist-ecommerce-eda.git
cd olist-ecommerce-eda
```

2. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) and place CSVs in the `data/` folder

3. Open the notebook
```bash
jupyter notebook notebooks/olist_eda.ipynb
```

---

## What I Learned
- How to engineer meaningful features from raw datetime columns
- How to ask business questions from data, not just data questions
- How to connect multiple tables to build a complete picture
- How to choose the right chart for each story
- How to write insights that are actionable, not just descriptive

---

*This project is part of my data science portfolio. Analysis ongoing — arcs 4–7 coming soon.*
