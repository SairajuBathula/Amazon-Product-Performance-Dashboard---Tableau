# Amazon Product Performance Dashboard – Project Documentation

**Author:** Sairaju Bathula
**Project Type:** Data Analytics Case Study (Hiringhood Internship Assignment)
**Tools Used:** Power BI, Tableau (Secondary), Excel/CSV Dataset

---

# 1. Project Objective

The goal of this project was to analyze Amazon product data and build an interactive dashboard that provides business insights about:

* Product distribution across categories
* Customer ratings
* Discount strategies
* Top performing products
* Revenue potential

The final deliverable included:

* Data cleaning and transformation
* DAX calculations
* Interactive dashboard
* Business insights documentation

---

# 2. Dataset Overview

The dataset contained Amazon product details such as:

* Product ID
* Product Name
* Category hierarchy
* Actual Price
* Discounted Price
* Discount Percentage
* Rating
* Rating Count
* Reviews

This was a raw dataset and required preprocessing before visualization.

---

# 3. Data Cleaning & Transformation (Power Query)

Performed inside Power BI → Transform Data

## 3.1 Fix Price Columns

Columns: `actual_price`, `discounted_price`

* Removed special symbols (₹, commas, text noise)
* Converted data type → Decimal Number

## 3.2 Clean Discount Percentage

Column: `discount_percentage`

* Removed `%` symbol
* Converted to decimal format
* Data type → Decimal Number

## 3.3 Clean Rating Columns

Columns: `rating`, `rating_count`

* Replaced blanks or dashes with 0
* Rating → Decimal Number
* Rating Count → Whole Number

## 3.4 Split Category Hierarchy

Original format:

```
Electronics | Mobiles | Smartphones
```

Steps:

* Split column by delimiter `|`
* Created:

  * Main Category
  * Sub Category 1–4

## 3.5 Handle Null Values

* Replaced null category levels with: **"Not Specified"**

## 3.6 Remove Duplicates

Columns used:

* Product ID
* Product Name

Power BI → Remove Rows → Remove Duplicates

---

# 4. Data Modeling

Single table model used for simplicity (flat model):

* Table Name: `amazon`

This was sufficient since no multiple table relationships were required.

---

# 5. DAX Measures Created

All measures created from: Modeling → New Measure

## 5.1 Total Products

```DAX
Total Products = COUNTROWS(amazon)
```

Counts total unique products in the dataset.

---

## 5.2 Average Rating

```DAX
Avg Rating = AVERAGE(amazon[rating])
```

Measures overall customer satisfaction.

---

## 5.3 Average Discount

```DAX
Avg Discount % = AVERAGE(amazon[discount_percentage])
```

Shows average discount applied across products.

---

## 5.4 Discount Amount

```DAX
Discount Amount =
SUMX(
    amazon,
    amazon[actual_price] - amazon[discounted_price]
)
```

Calculates total discount value provided.

---

## 5.5 Revenue Potential

```DAX
Revenue Potential =
SUMX(
    amazon,
    amazon[discounted_price] * amazon[rating_count]
)
```

Estimates possible revenue using rating count as a proxy for demand.

---

# 6. Dashboard Design

The dashboard was designed to follow a business storytelling layout.

## 6.1 KPI Cards (Top Section)

* Total Products
* Avg Rating
* Avg Discount %

Purpose: Quick executive summary.

---

## 6.2 Number of Products by Category (Bar Chart)

* Axis → Main Category
* Values → Count of Products

Insight: Shows category demand and inventory concentration.

---

## 6.3 Rating Distribution Histogram

* Field → Rating (binned)
* Shows frequency distribution of ratings

Insight: Identifies overall product quality trend.

---

## 6.4 Top 10 Most Reviewed Products

* Axis → Product Name
* Values → Rating Count
* Filter → Top 10

Insight: Highlights high-engagement products.

---

## 6.5 Category Performance Matrix

* Rows → Main Category
* Color → Avg Discount or Avg Rating

Insight: Quick comparison of category-level performance.

---

## 6.6 Discount vs Rating Scatter Plot

* X-axis → Avg Discount %
* Y-axis → Avg Rating
* Size → Rating Count
* Legend → Category

Insight: Relationship between pricing strategy and customer satisfaction.

---

# 7. Business Insights Generated

## 7.1 Electronics Dominates Volume

* Highest number of products
* Strong competition and demand

## 7.2 Discounts Do Not Guarantee Ratings

* Highly discounted products don’t always perform better
* Price ≠ satisfaction

## 7.3 Category-Based Pricing Strategies

* Some categories show consistently higher discounts
* Indicates aggressive pricing to stay competitive

## 7.4 Quality Over Price

* Products with low discounts still maintain strong ratings
* Suggests brand trust and product quality matter more

## 7.5 Top Brands by Reviews

* boAt dominates highly reviewed products
* Strong brand engagement

## 7.6 Mixed Quality in Electronics

* High volume but not highest ratings
* Indicates wide quality variation

---

# 8. Tableau Version (Secondary Build)

The same dataset was used to recreate the dashboard in Tableau to demonstrate multi-tool capability.

Key implementations:

* KPI sheets using text marks
* Histogram for rating distribution
* Scatter plot for discount vs rating
* Category matrix using square marks

This version validated cross-tool analytics skills.

---

# 9. Challenges Faced

* Cleaning messy currency values
* Handling mixed data types
* Designing beginner-friendly layout
* Building KPI cards in Tableau (manual setup)

These were solved using Power Query transformations and calculated measures.

---

# 10. Final Deliverables

* Power BI Dashboard (.pbix)
* Tableau Dashboard (.twbx)
* Business Insights PDF
* GitHub Repository
* Submission Document for Hiringhood

---

# 11. Skills Demonstrated

* Data Cleaning (Power Query)
* DAX Calculations
* Data Visualization
* Dashboard Storytelling
* Business Insight Generation
* Multi-tool Analytics (Power BI + Tableau)

---

# 12. Conclusion

This project demonstrates the end-to-end data analytics workflow:

1. Raw data cleaning
2. Data modeling
3. DAX calculations
4. Dashboard building
5. Insight generation

The dashboard provides actionable insights into pricing strategies, product performance, and customer behavior on Amazon.

This project was built as part of a real-world internship assignment and reflects practical industry-ready analytics skills.

---

**Created by:** Sairaju Bathula
