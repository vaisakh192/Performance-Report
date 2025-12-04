# 🌿 Plant Co. Power BI Performance Dashboard – 2024

This project is a complete Power BI analytics solution designed to analyze Quantity, Sales, and Gross Profit performance for Plant Co. in 2024. 
The dashboard provides an interactive view of product performance, profitability, geographic patterns, and month-on-month trends.

---

## 📊 Project Objectives

- Track YTD vs PYTD performance for Quantity, Sales, and Gross Profit  
- Identify top & bottom performing countries  
- Analyze monthly trends with visual breakdown  
- Understand product-level profitability using GP% segmentation  
- Provide interactive KPI switching (Sales, Quantity, Gross Profit)

---

## 🧰 Tools & Technologies

- **Power BI Desktop**
- **Power Query**
- **DAX Measures**
- **Excel Dataset**
- **Data Modelling (Star Schema)**

---

## 📁 Dataset

**Source:** Plant Co. transactional dataset  
**File:** `Plant_DTS.xls`

Contains fields such as:
- Quantity
- Sales Value
- Gross Profit
- Product Type (Indoor / Outdoor / Landscape)
- Country
- Month / Year

---

## 🏗 Data Model

The data model uses:
- **Fact Table:** Fact_Sales  
- **Dimensions:**  
  - Dim_Date  
  - Dim_Product  
  - Dim_Country  

Model follows a **clean star-schema** optimized for performance.

