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

DAX Measures Used

The project uses a clean and optimized DAX framework to calculate KPIs, compare YTD with PYTD, and dynamically switch visuals based on user selection.

## KPI Measures

Quantity = SUM(Fact_Sales[Quantity])
Sales = SUM(Fact_Sales[Sales_USD])
Gross Profit = [Sales] - [COGS]
GP% = DIVIDE([Gross Profit], [Sales])

## YTD Measures

YTD_Quantity = TOTALYTD([Quantity], Dim_Date[Date])
YTD_Sales = TOTALYTD([Sales], Dim_Date[Date])
YTD_GrossProfit = TOTALYTD([Gross Profit], Dim_Date[Date])

## PYTD Measures

PYTD_Quantity =
CALCULATE(
    [Quantity],
    SAMEPERIODLASTYEAR(Dim_Date[Date]),
    Dim_Date[Inpast] = TRUE()
)

PYTD_Sales =
CALCULATE(
    [Sales],
    SAMEPERIODLASTYEAR(Dim_Date[Date]),
    Dim_Date[Inpast] = TRUE()
)

PYTD_GrossProfit =
CALCULATE(
    [Gross Profit],
    SAMEPERIODLASTYEAR(Dim_Date[Date]),
    Dim_Date[Inpast] = TRUE()
)

## Dynamic KPI Selector

S_YTD =
SWITCH(
    SELECTEDVALUE(slc_Values[Values]),
    "Sales",        [YTD_Sales],
    "Quantity",     [YTD_Quantity],
    "Gross profit", [YTD_GrossProfit]
)

S_PYTD =
SWITCH(
    SELECTEDVALUE(slc_Values[Values]),
    "Sales",        [PYTD_Sales],
    "Quantity",     [PYTD_Quantity],
    "Gross profit", [PYTD_GrossProfit]
)

## KPI Comparison

YTD vs PYTD = [S_YTD] - [S_PYTD]

## Dynamic Titles

_Report Title =
"Plant Co. " &
SELECTEDVALUE(slc_Values[Values]) &
" Performance " &
SELECTEDVALUE(Dim_Date[Date].[Year])

_Column Chart Title =
SELECTEDVALUE(slc_Values[Values]) & " YTD vs PYTD | Month"

_Waterfall Title =
SELECTEDVALUE(slc_Values[Values]) & " YTD vs PYTD | Month - Country - Product"

_Scatter Title =
"Account Profitability Segmentation | GP% and " &
SELECTEDVALUE(slc_Values[Values])




