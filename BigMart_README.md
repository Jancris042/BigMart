
# 📊 BigMart Sales Analysis — Data Cleaning & Power BI Visualization

This project analyzes BigMart’s sales data and presents key insights through a comprehensive **Power BI dashboard**. It covers the entire **data cleaning procedure**, from handling missing and zero values in Excel to creating impactful visuals that show how outlet types, sizes, and product features drive revenue.

---

## ✅ Project Summary

- **Dataset:** Train_Raw.csv  
- **Records:** 8,524 rows × 12 columns  
- **Tools:** Excel (data cleaning) & Power BI (visualization)

---

## ⚙️ Data Cleaning Procedure

Below is the exact method used to clean the dataset for accurate analysis.

---

### 1️⃣ Handle Missing `Item_Weight`

- **Problem:** 1,463 missing `Item_Weight` entries.
- **Solution:** Fill blanks with the **average weight for each `Item_Type`.**

**Excel Formula:**  
=AVERAGEIFS(B2:B8524, D2:D8524, "Snack Foods")

✔ If needed, ignore zero weights:  
=AVERAGEIFS(B2:B8524, D2:D8524, "Snack Foods", B2:B8524, "<>0")

**Replace logic with `VLOOKUP`:**  
=IF(B2="", VLOOKUP(E2, $M$2:$N$20, 2, FALSE), B2)

- `B2` = Item_Weight  
- `E2` = Item_Type  
- `$M$2:$N$20` = Lookup table for `Item_Type` and its average weight.

---

### 2️⃣ Handle Missing `Outlet_Size`

- **Problem:** 2,410 blanks in `Outlet_Size`.
- **Solution:** Fill blanks with the **most common size** for each `Outlet_Type`.

**Example:**  
| Outlet_Type | Most Frequent Size |
|------------------|----------------------|
| Supermarket T1 | Small |
| Supermarket T2 | Medium |
| Grocery Store | Small |

**Count mode size:**  
=COUNTIFS(Outlet_Type_Range, "Supermarket T1", Outlet_Size_Range, "Small")

**Replace:** Use Filter → `(Blanks)` → Type mode → `Ctrl + Enter` to fill all at once.

---

### 3️⃣ Handle Zero `Item_Visibility`

- **Problem:** 526 rows with unrealistic `Item_Visibility = 0`.
- **Solution:** Treat zeros as missing and replace with the **mean `Item_Visibility` for each `Item_Type`.**

**Excel Formula:**  
=AVERAGEIFS(D2:D8524, E2:E8524, "Dairy", D2:D8524, "<>0")

**Replace logic with `VLOOKUP`:**  
=IF(D2=0, VLOOKUP(E2, $Q$2:$R$17, 2, FALSE), D2)

- `D2` = Item_Visibility  
- `E2` = Item_Type  
- `$Q$2:$R$17` = Lookup table for `Item_Type` and its average visibility.

---

## ⚡ Excel Tips Used

- **Double-click Fill Handle:** Quickly fill formula down the whole column.
- **`Go To Special → Blanks`:** Select all blank cells at once.
- **`Ctrl + D`:** Fill down.
- **`Ctrl + H`:** Find & Replace.
- **`AVERAGEIFS` & `VLOOKUP`:** Conditional averages and dynamic replacements.

---

## 📊 Power BI Dashboard

The cleaned data is visualized in Power BI, providing clear insights into BigMart’s performance:

### ✅ Revenue by Outlet Type
- **Supermarket T1:** Dominates with **₱12.9M**, far ahead of T3 (₱3.5M) and T2 (₱1.9M).
- **Grocery Stores:** Minimal revenue contribution.
- **Insight:** T1 outlets are the main revenue drivers.

### ✅ Market Share Distribution
- **Supermarket T1:** 65% share.
- **Grocery Stores:** 13%.
- **Supermarket T2 & T3:** 11% each.
- **Insight:** T1 outlets are central to BigMart’s business.

### ✅ Price by Outlet Size
- **Small outlets:** ₱9.0M
- **Medium outlets:** ₱7.5M
- **High outlets:** ₱2.1M
- **Insight:** Smaller outlets outperform larger ones in price volume.

### ✅ Fat Content Sales Split
- **Low Fat:** 64.73%
- **Regular:** 35.27%
- **Insight:** Consumers prefer healthier, low-fat options.

### ✅ Top 5 Individual Outlets
- **OUT027:** ₱3.5M (top performer).
- **OUT035, OUT049, OUT017, OUT013:** ₱2.1M–₱2.3M each.
- **Insight:** OUT027 stands out with significant revenue gap.

---

## 🚀 Key Findings

✅ **Supermarket T1** and **Small-sized outlets** are the highest revenue contributors.  
✅ **Low Fat products** dominate market share.  
✅ **Individual outlet performance** varies greatly, with OUT027 performing best.

---

## 🗂️ How to Reproduce

1. **Clean the data** in Excel using the steps and formulas above.
2. **Import cleaned data** into Power BI Desktop.
3. Build visuals using:
   - Pie charts (Market Share, Fat Content)
   - Bar charts (Revenue by Outlet Type, Price by Outlet Size)
   - Top N filters (Top 5 Outlets)

4. **Format visuals:** Remove white backgrounds under `Format > Effects > Background`.

---

## 📎 Author

BigMart Sales & Market Analysis  
**Contributor:** Jancris Paul Oporto | [oportojancrispaulavila25@gmail.com]

---

**✅ Ready to explore — Happy analyzing!**
