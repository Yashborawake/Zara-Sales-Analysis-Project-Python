# 🛍️ Zara Sales Analysis

An end-to-end **Exploratory Data Analysis (EDA)** of Zara's product sales data using Python. The project cleans the data, engineers new features, and uncovers what drives sales: pricing, promotions, seasonality, product position, and category performance.

---

## 📌 Project Overview

This project analyzes **20,252 Zara clothing products** to answer business questions such as:

- Which categories and products generate the most revenue?
- Do promotions actually boost sales?
- How do price and season affect sales volume?
- Does in-store product position influence promotions or sales?
- Are men's or women's products performing better?

---

## 📂 Dataset

| Item | Details |
|------|---------|
| File | `Zara_sales.csv` (semicolon-separated) |
| Rows | 20,252 |
| Columns | 17 (15 after cleaning) |

**Key columns:** `Product ID`, `Product Position`, `Promotion`, `Seasonal`, `Sales Volume`, `name`, `description`, `price`, `terms` (jackets, jeans, shoes, sweaters, t-shirts), `section` (MAN/WOMAN), `season`, `material`, `origin`.

---

## 🛠️ Tools & Libraries

- **Python 3**
- **Pandas**, **NumPy**: data manipulation
- **Matplotlib**, **Seaborn**: visualization
- **Statistics**, **SciPy**: descriptive stats & Chi-square tests
- **Jupyter Notebook**

---

## 🔄 Workflow

1. **Import libraries & load dataset**
2. **Initial data exploration**: shape, dtypes, nulls, duplicates
3. **Data cleaning**: dropped null rows; removed noisy `url` and `currency` columns
4. **Feature engineering**
   - `Price_Range` (Low / Medium / High)
   - `Promotion_Flag` (binary encoding)
   - `Total` = `price × Sales Volume` (revenue proxy)
5. **Descriptive statistics**: mean, median, mode, std for price & sales volume; grouped statistics
6. **Univariate analysis**: histograms, KDE plots, count plots
7. **Bivariate analysis**: scatter plots and **Chi-square tests of independence**
8. **Business analysis**: revenue breakdown by section, category, promotion, season, and position

---

## 📊 Key Findings

- 💰 **Pricing:** Prices range from $12 to $134.99, right-skewed (mean $41.95 > median $35.95). Most products are low-to-mid priced.
- 📉 **Price vs Sales:** Higher prices are associated with lower sales volume.
- 🎯 **Promotions:** Promoted products average ~1,412 units vs ~872 for non-promoted, yet *total revenue* is nearly equal between the two groups.
- 🌦️ **Seasonality:** Summer and Winter show the highest average sales volume; seasonal products generate more total revenue than non-seasonal ones.
- 👗 **Gender section:** Women's products account for ~65% of items and more than **2× the revenue** of men's products.
- 🧥 **Top category:** **Jackets** dominate revenue (~$487M), followed by sweaters, t-shirts, shoes, and jeans. Jackets also make up most of the top-20 best-selling products.
- 🏬 **Product position:** Aisle placement generates the highest total sales, followed by End-cap and Front of Store.

### 🧪 Chi-Square Test Results

| Variables | p-value | Relationship |
|-----------|---------|--------------|
| Promotion × Seasonal | 0.00 | ✅ Significant |
| Promotion × Product Position | 0.01 | ✅ Significant |
| Promotion × Terms | 0.39 | ❌ Independent |
| Promotion × Section | 0.37 | ❌ Independent |
| Section × Product Position | 0.48 | ❌ Independent |
| Terms × Product Position | 0.40 | ❌ Independent |

---

## 💡 Business Recommendations

- Prioritize **inventory and marketing for jackets**: the biggest revenue driver.
- Plan stock around **Summer and Winter** peaks.
- Use promotions selectively, especially for **seasonal items**, since they don't significantly raise overall revenue.
- Invest in the **women's section**, which contributes the majority of sales.

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/zara-sales-analysis.git
cd zara-sales-analysis

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scipy jupyter

# 3. Place Zara_sales.csv in the project folder, then launch
jupyter notebook zara_sales_analysis.ipynb
```

---

## ⚠️ Notes

- `Promotion_Flag` currently maps `'Yes'→1` and `'NO'→0`, but the data uses `'No'`, so non-promoted rows become `NaN`. Fix with `.map({'Yes':1,'No':0})`.
- `Price_Range` uses `price > 40` / `price < 80`, so a price of exactly 40 or 80 falls into "High". Consider `>=` / `<`.

---

## 🙋 Author

**Your Name**
📧 your.email@example.com · 🔗 [LinkedIn](https://www.linkedin.com/in/yash-borawake/) · 💻 [GitHub](https://github.com/Yashborawake)

⭐ If you found this project useful, give it a star!
