#  Chip Category Analysis & Trial Store Evaluation

A retail analytics project analyzing 12 months of loyalty transaction data for a supermarket chip category, answering two real business questions: **where should the category strategy focus for the next half-year**, and **did a 3-store sales trial actually work?**

---

## 📌 Business Problem

The supermarket needed two decisions made from data before finalizing its next half-year chip category plan:

1. **Category Strategy** — Which brands, pack sizes, and customer segments should the next 6 months of category planning prioritize?
2. **Trial Evaluation** — A sales trial was run in Stores 77, 86, and 88. Did it actually lift sales, or is the change just normal month-to-month noise?

---

##  Objectives

- Clean and explore ~265,000 loyalty card transactions (Jul 2018 – Jun 2019)
- Identify top-performing brands, pack sizes, and customer lifestages
- Quantify seasonal demand patterns
- Select statistically matched control stores for each trial store
- Test whether trial-store sales were significantly different from control, using a 95% confidence interval
- Translate findings into a business-ready recommendation (delivered as a Pyramid-Principle PowerPoint report)

---

##  Dataset

| File | Description |
|---|---|
| `dataset.csv` | Full transaction-level chip sales data (date, store, customer, product, quantity, sales) |
| `qvi_data.csv` | Cleaned/merged transaction data used for the trial store evaluation |

Key fields: `STORE_NBR`, `LYLTY_CARD_NBR`, `TXN_ID`, `PROD_NAME`, `PROD_QTY`, `TOT_SALES`, `PACK_SIZE`, `BRAND`, `LIFESTAGE`, `PREMIUM_CUSTOMER`

---

##  Tools & Libraries

- **Python** — pandas, NumPy
- **Statistics** — scipy.stats (t-distribution, confidence intervals)
- **Visualization** — Matplotlib
- **Reporting** — PowerPoint deck built with pptxgenjs, structured using the Pyramid Principle
- **Jupyter Notebook** for exploratory analysis

---

##  Methodology

### Part 1 — Category Sales Analysis
1. Cleaned inconsistent product name text (typos, salsa dip products removed as non-chip items)
2. Removed an outlier loyalty card (bulk/commercial buyer skewing results)
3. Aggregated sales by brand, pack size, lifestage, and customer type
4. Analyzed daily transaction volume to detect seasonality

### Part 2 — Trial Store Evaluation
1. For each trial store, selected the **control store** with the most similar pre-trial sales and customer trend (correlation + magnitude scoring)
2. Scaled the control store's sales to the trial store's baseline level
3. Calculated the % difference between trial and scaled control for each post-trial month
4. Built a **95% confidence interval** using pre-trial variability to test whether the post-trial gap was statistically significant (t-distribution, 6 degrees of freedom)

---

## 📊 Key Insights

**Category Strategy**
- Total chip category sales: **₹1,805,171.70**
- **5 brands** (Kettle, Doritos, Smiths, Pringles, Infuzions) drive **59%** of total sales
- **Kettle** alone accounts for ~22% of category revenue
- Top 3 pack sizes (175g, 150g, 134g) drive over half of sales
- **Older Singles/Couples, Retirees, and Older Families** are the highest-value lifestage segments
- Daily transactions spike ~30% in the two weeks before Christmas

**Trial Store Evaluation**

| Store | Control Store | Result |
|---|---|---|
| 77 | 233 | ✅ Significant, sustained uplift |
| 86 | 155 | ⚠️ No consistent uplift (inconclusive) |
| 88 | 237 | ✅ Strongest, statistically significant uplift |

**Recommendation:** Roll out the trial format to stores with a profile similar to 77 and 88; hold off on scaling the Store 86 format until the cause of its inconsistent result is understood.


---

## ▶️ How to Run

```bash
git clone https://github.com/<your-username>/chip-category-analysis.git
cd chip-category-analysis
pip install pandas numpy matplotlib scipy jupyter
jupyter notebook notebooks/sales_analysis.ipynb
```

---

## 📑 Deliverable

A stakeholder-facing PowerPoint report (`report/Chip_Category_Trial_Report.pptx`) built using the **Pyramid Principle** — leads with the answer, supports it with key insights, and closes with clear recommendations — designed for a non-technical business audience.

---

## 👤 Author

**Udhai**
B.Tech, Artificial Intelligence and Data Science
[LinkedIn](www.linkedin.com/in/udhayachandrika-s-56aaa4294) · [GitHub](https://github.com/Udhaya1075)
