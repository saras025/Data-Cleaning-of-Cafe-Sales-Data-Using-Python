# Data-Cleaning-of-Cafe-Sales-Data-Using-Python

# ☕ Cafe Sales Data Engineering & Business Analytics Series

## 📌 Project Overview
This repository contains a two-part data analytics project based on a **10,000-record cafe transactional dataset**. 

- **Part 1 (Current):** Python-based data cleaning, mathematical imputation, schema standardization, and feature engineering.
- **Part 2 (Upcoming):** Power BI interactive dashboard focusing on payment channel analysis, category margins, and executive decision-making.

---

## 🛠️ Part 1: Data Cleaning & Preprocessing (Python & Pandas)

### Problem Statement
Raw transactional data often contains corrupt string placeholders, missing temporal records, and incomplete financial metrics. Simply dropping rows (`df.dropna()`) would destroy over **2,800+ transactions**, leading to inaccurate total revenue calculations.

### Key Highlights & Impact
- **100% Volume Retention:** Retained all **10,000 original rows** by leveraging domain-logic imputations instead of dropping records.
- **Zero Nulls Achieved:** Successfully resolved **6,826 missing values** across financial, date, and categorical fields.
- **Type Safety & Schema Expansion:** Converted raw `object` string fields to proper `float64` and `datetime64[ns]` formats, expanding the schema from 8 to 12 columns.

---

## 📐 Data Cleaning Methodology

1. **Data Type Casting:**
   - Converted financial fields (`Quantity`, `Price Per Unit`, `Total Sales`) to `float64`.
   - Converted date strings to standard `datetime64[ns]` format.

2. **Row-Level Mathematical Imputation:**
   - Applied algebraic logic to restore missing financial metrics without altering variance:
     $$\text{Total Sales} = \text{Quantity} \times \text{Price Per Unit}$$

3. **Product-Based Median Lookups:**
   - Handled remaining missing price fields by executing `.groupby('Item')` and imputing menu-item-specific median prices.

4. **Sequential Temporal Recovery:**
   - Repaired date gaps using ordered forward filling (`ffill()`).
   - Derived temporal features: `Transaction Month` and `Transaction weekday`.

5. **String Standardization & Feature Engineering:**
   - Unified text formatting and consolidated inconsistent placeholders (`"Nan"`, `"Unknown"`, `"ERROR"`) into `"Unspecified"`.
   - Engineered two derived dimensions for downstream analysis:
     - `Item Category`: `Drink` vs. `Eatable`
     - `Payment Category`: `Online` vs. `Offline`

---

## 📊 Before & After Pipeline Comparison

| Metric / Dimension | Raw Dataset (Before) | Cleaned Dataset (After) |
| :--- | :--- | :--- |
| **Total Rows** | 10,000 | **10,000 (0 Rows Dropped)** |
| **Total Null Values** | 6,826 | **0** |
| **Column Count** | 8 | **12 (4 Features Engineered)** |
| **Data Types** | 8 `object` strings | Correct `float64`, `datetime64[ns]`, `object` |
| **Data File** | `dirty_cafe_sales.csv` | `cleaned_cafe_sales.csv` |

---

## 💡 Key Business Findings (Exploratory Data Analysis)

(Updating Soon)

* Before Data Cleaning Results
<img width="1486" height="590" alt="Screenshot 2026-09-09 220314" src="https://github.com/user-attachments/assets/f993b38c-27ec-431f-86f7-0075fdd49b6e" />

* After Data Cleaning Results 
<img width="1452" height="660" alt="Screenshot 2026-09-09 220143" src="https://github.com/user-attachments/assets/0c9dbd53-e957-4cb2-852d-7d26ce250ebf" />

---
