# 🍕 Pizza Sales Analysis (2015)

## 📊 Project Overview
This project analyzes pizza sales data from 2015 using Power BI to uncover revenue drivers, demand patterns, product performance, and ingredient economics. The goal is to transform raw order-level transactional data into meaningful insights that support data-driven decision-making around staffing, menu engineering, pricing, and seasonal promotions.

---

## 🎯 Objectives
- Track key business KPIs
- Identify sales trends and seasonal patterns
- Analyze customer purchasing behavior
- Evaluate product and category performance
- Provide actionable business recommendations

---

## 🗂 Data Source & Model
- **Source:** a single flat file, `data_pizza.csv`, loaded via Power Query — one row per order line (order_id, date, time, pizza_id, quantity, size, price, name, category, ingredients).
- **Dimensions derived in Power Query:** `Dim Date` (full 2015 calendar), `Dim_Time`, `Pizza`, `Pizza Ingredients` (bridge table split from the ingredients text), `Ingredients`, and `Order Date Time` (used to measure the gap between consecutive orders).
- **Key DAX measures:** Total Revenue, Total Quantity Sold, Total Orders, Avg Order Value, Avg Pizza per Order, Avg Ingredient Price, Pizza/Ingredient Rank (driven by Top 5/Bottom 5 parameter), and two manually-computed Pearson correlation measures.
- Disconnected parameter tables let single visuals toggle between **Quantity vs. Revenue** and **Top 5 vs. Bottom 5** without duplicating charts.

---

## 📌 Key Metrics
- **Total Revenue:** $817.86K  
- **Total Orders:** 21K  
- **Total Pizzas Sold:** 50K  
- **Average Order Value:** $38.31  
- **Average Pizzas per Order:** 2.32  

---

## 📈 Key Insights

### 🕒 Sales Trends & Seasonality
- Weekly revenue typically runs **$13K–$17K**, dipping toward the start/end of the year and peaking around **week 48**.
- **Strongest days (by revenue):** Friday ($136.07K) > Thursday ($123.53K) > Saturday ($123.18K); **weakest:** Sunday ($99.20K) and Monday ($107.33K).
- Revenue peaks sharply at **12–1 PM** (lunch), with a secondary rise at **5–7 PM** (dinner); very little revenue before 11 AM or after 9 PM.
- **Strongest months:** July ($72.56K), May ($71.40K), March/November ($70.40K).
- **Weakest months:** October ($64.03K), September ($64.18K), December ($64.70K), February ($65.16K) — these four behave as one prolonged low-demand cluster (under 2% apart) rather than four separate dips.

### 📅 Customer Behavior
- **61.6% of orders (13,149 of 21,350) are multi-item**, vs. 38.4% single-item — and multi-item orders account for an even more dominant **~83.3% of total pizzas sold** (~41.3K of ~49.6K).
- Average interval between same-day orders: **11.0 minutes**, indicating steady, continuous demand through service hours.
- Peak hours: **Lunch 12–1 PM**, **Dinner 5–7 PM**. Best-performing days: **Thursday–Saturday**.

### 🍕 Product Performance
| Category | Quantity Sold | Revenue | Avg. Price/Pizza |
|---|---|---|---|
| Classic | 14,888 | $220.05K | $14.78 |
| Supreme | 11,987 | $208.20K | $17.37 |
| Chicken | 11,050 | $195.92K | $17.73 |
| Veggie | 11,649 | $193.69K | $16.63 |

Classic leads on both volume and revenue despite the lowest average price; Chicken and Supreme are the premium categories (highest average price) but sell lower volumes.

**Top 5 pizzas by quantity sold:** The Classic Deluxe (2,453), The Barbecue Chicken (2,432), The Hawaiian (2,422), The Pepperoni (2,418), The Thai Chicken (2,371).

**Bottom 5 pizzas by quantity sold:** The Brie Carre (490), The Mediterranean (934), The Calabrese (937), The Spinach Supreme (950), The Soppressata (961). The Brie Carre Pizza is the clearest menu-engineering candidate — about a fifth of the volume of the next-lowest pizza and under $12K in annual revenue.

### 🧀 Size & Ingredient Analysis
- **Large** is the top-selling size, followed by Medium then Small; XL/XXL together are a small, niche share of sales.
- **Garlic** is the standout cross-category favorite ingredient; Red Peppers, Red Onions, and Chicken are each the top ingredient within their own category.
- Consistently least-used ingredients: Pesto Sauce, Green Peppers, Kalamata Olives, Plum Tomatoes, and a premium cluster (Caramelized Onions, Pears, Prosciutto, Thyme, Brie Carre Cheese).

### 💰 Correlations
- **Avg. pizza price vs. total quantity sold (by category): r ≈ –0.95** — a strong negative relationship; the cheapest category (Classic) sells the most, the priciest (Chicken, Supreme) sell the least, confirming clear price sensitivity.
- **Ingredient quantity vs. revenue: r ≈ 1** — expected, since revenue is derived directly from quantity (Revenue = Price × Quantity), reflecting a mathematical dependency rather than an independent relationship.

---

## 🧠 Business Recommendations
- Introduce a **mid-range pricing tier** between Classic and the premium Chicken/Supreme categories to capture volume without eroding margin.
- Promote top sellers (Classic Deluxe, Barbecue Chicken, Thai Chicken) and **bundle them with drinks/sides** at checkout.
- Reassess or reformulate bottom performers (Brie Carre, Mediterranean, Calabrese) and reduce reliance on their low-volume ingredients (Prosciutto, Thyme, Pears, Caramelized Onions).
- **Roster more staff** for confirmed peaks (12–1 PM, 5–7 PM, Thu–Sat) and consider trimming quiet pre-11 AM/post-9 PM hours.
- Run **targeted promotions across the Oct–Sep–Dec–Feb low-demand cluster** as one extended trough rather than treating each month separately.
- Lean further into **combo/family-bundle offers** — multi-item orders already drive roughly five out of every six pizzas sold.

---

## 📊 Dashboard Pages
1. **Common Metrics & Sales Trends** — KPI cards; daily sales line chart; Day-of-Week × Hour revenue heatmap; month slicer.
2. **Category & Pizza Analysis** — 100% stacked column chart by category/size; Quantity/Revenue and Top 5/Bottom 5 toggled bar charts.
3. **Ingredient Analysis** — Category slicer with most/least popular ingredients; scatter chart of quantity vs. revenue by ingredient with correlation card.
4. **Average Indicators** — Scatter chart of avg. price vs. total orders by category (with trend line and correlation card); order-mix pie chart (single vs. multi-item); average time-between-orders card.

**Interactivity:** every slicer cross-filters all visuals on its page (including KPI cards); the Quantity/Revenue and Top 5/Bottom 5 parameters let one pair of charts serve four views; the bidirectional Pizza↔Ingredients relationship means selecting an ingredient filters back to the pizzas/categories that use it.

---

## 🛠 Tools Used
- Power BI  
- SQL  
- Data Cleaning & Transformation  
- Data Visualization  

---

## 📷 Dashboard Preview
<img width="1179" height="666" alt="Screenshot 2026-04-07 002750" src="https://github.com/user-attachments/assets/122bb1d4-c27d-4703-848e-ad29c387fbe1" />
<img width="1209" height="684" alt="Screenshot 2026-04-07 002758" src="https://github.com/user-attachments/assets/6c5806ee-794f-44e4-be50-1d41fd5e9460" />
<img width="1214" height="685" alt="Screenshot 2026-04-07 002806" src="https://github.com/user-attachments/assets/6ea0c61c-27e5-4500-b829-ae33a6d75a2f" />
<img width="1213" height="682" alt="Screenshot 2026-04-07 002815" src="https://github.com/user-attachments/assets/0cdabe0f-30b4-4109-8060-a54149c86d2f" />





---

## 🚀 Author
**Thao Vy Dang**  
- GitHub: https://github.com/vydang123  
