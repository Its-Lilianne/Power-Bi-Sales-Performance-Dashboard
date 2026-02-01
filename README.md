# 📊 Power BI Sales Performance Dashboard (End-to-End Project)

## 🔍 Project Overview

This project demonstrates an end-to-end **data analytics workflow using Power BI**, from raw data assessment and cleaning to modelling, DAX development, dashboard design, and executive storytelling. The goal was not only to build visuals, but to **think critically like a business analyst**, challenge unrealistic data patterns, and present insights that support decision-making.

The dataset represents sales transactions for a retail business across **products, customers, and regions**, limited to **one year (2023)** and **three months (January, February, & March)**.

---

![image alt]


## 🎯 Project Objectives

* Assess and clean raw data across multiple tables
* Build a robust data model in Power BI
* Calculate key business KPIs using DAX
* Identify profitability drivers and performance gaps
* Design an executive-ready interactive dashboard
* Transparently document assumptions and analytical decisions

---

## 🗂️ Dataset Description

The Power BI model is built from **three tables**:

* **Sales Table**: Transaction-level data including quantity sold, unit cost, sales amount, date, and customer reference
* **Products Table**: Product attributes such as brand and color
* **Customers Table**: Customer demographics including region, gender, and income level

These tables were connected using a **star schema** with Sales as the fact table.

![image alt]

---

## 🧹 Data Quality Assessment & Cleaning

A column-by-column review revealed several issues:

* Inconsistent text casing across categorical fields
* Missing or unrealistic cost-to-price relationships leading to negative profit
* Limited time coverage (2 months only)
* Potential ambiguity in whether `SalesAmount` represented unit price or total transaction value

### Cleaning Actions Taken

* Standardized text fields (Brand, Region, Gender, Color)
* Validated numeric fields (Quantity, Cost, Sales Amount)
* Ensured correct data types for dates and measures
* Built calculated columns/measures to resolve pricing ambiguity

Rather than ignoring data inconsistencies, the project explicitly **documents and addresses them**.

---

## 🧠 Business Assumptions & Analytical Decisions

### Why the Dataset Was Challenged

Initial analysis showed **negative total profit**, which is unrealistic for a functioning retail business. This prompted a reassessment of the data structure.

### Key Assumption Introduced

* `SalesAmount` represents **unit selling price**, not total revenue
* Revenue should therefore be calculated as:

  > Quantity × SalesAmount

This assumption was applied consistently and clearly documented, resulting in more realistic financial outcomes.

---

## 📐 DAX Measures (Adjusted Business Logic)

**Total Revenue**

```
Total Revenue =
SUMX(Sales, Sales[Quantity] * Sales[SalesAmount])
```

**Total Cost**

```
Total Cost =
SUMX(Sales, Sales[Quantity] * Sales[UnitCost])
```

**Total Profit**

```
Total Profit =
[Total Revenue] - [Total Cost]
```

**Total Customer**

```
Total Customer =
DISTINCTCOUNT(Customers[CustomerID])
```

**Total Sales**

```
Total Sales =
COUNTROWS(Sales)
```


**Profit Margin %**

```
Profit Margin % =
DIVIDE([Total Profit], [Total Revenue])
```

---

## 📈 KPI Summary (Adjusted View)

* **Total Revenue:** ₦3.1M
* **Total Cost:** ₦2.2M
* **Total Profit:** ₦932K
* **Total Customer:** 250
* **Total Sales:** 5200
* **Profit Margin:** 30%

This adjusted view provides a more accurate representation of operational performance.

---

## 📊 Dashboard Design & Visuals

The dashboard was designed using a **minimal, executive-friendly theme**, focusing on clarity and interaction.

### Key Visuals

* Brand by Profit (Most profitable products)
* Color by Total Purchase (Best-selling color)
* Monthly Customer Count (Performance gaps)
* Income Level by Profit (Customer value segmentation)
* Revenue KPIs (Cards)

### Interactivity

* **Slicers:** Region, Gender
* **Insight Pop-up Panel:** Executive narrative accessible via button
* **Recommendations Pop-up:** Action-oriented summary

Limited time coverage was handled by:

* Avoiding misleading trend lines
* Using categorical comparisons instead of forecasts
* Explicitly stating time constraints in insights

---

## 🧩 UX & Storytelling Features

* Toggleable **Insights** and **Recommendations** panels
* Clear separation between metrics and interpretation
* Consulting-style executive narratives
* Transparent communication of assumptions

---

## 📌 Key Executive Insight (Adjusted View)

After applying commercially realistic pricing and cost assumptions, the business generated ₦3.1M in total revenue against a ₦2.2M cost base, delivering an adjusted profit of ₦932K and a 30% margin. This indicates a structurally healthy operating model with effective cost control and strong value capture from sales activities.

---

## 🎯 Recommendations

Management should prioritize scaling high-margin product segments, reinforce cost discipline, and leverage regional and customer insights to optimize pricing strategies. With a demonstrated 30% margin under realistic assumptions, the business is well-positioned for targeted growth initiatives.

---

## 🚀 Tools & Skills Demonstrated

* Power BI (Data Modelling, DAX, Visualization)
* Business-focused data validation
* Analytical storytelling
* Dashboard UX design
* Critical thinking & assumption management

---

## 📁 Repository Structure (Suggested)

```
📦 PowerBI-Sales-Dashboard
 ┣ 📂 Data
 ┣ 📂 DAX
 ┣ 📂 Dashboard
 ┣ 📄 README.md
```


---

## 🏁 Final Note

This project reflects not just technical execution, but **analytical judgment** — a core skill for real-world data analysts. Rather than accepting flawed data at face value, the analysis challenges assumptions, documents decisions, and delivers insights aligned with business reality.

---

## 👤 Author

**Lilian Arnold-Addo**
*Data Analyst | Power BI | Data Storytelling*
