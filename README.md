# 📊 Student Lifestyle & Stress Analysis (Excel Project)

An Excel workbook that imports, cleans, analyses and visualises a student lifestyle dataset (daily hours spent on study, extracurriculars, sleep, social life and physical activity, plus GPA and stress level).

📁 **Deliverable:** `Student_Lifestyle_Stress_Analysis.xlsx` (start on the `Dashboard` sheet)

## ✅ Task coverage

| Sr. | Task | Sheet(s) | What was done |
|---|---|---|---|
| 1️⃣ | 📥 Dataset Selection & Import | `Raw_Data`, `Cleaning_Log` | 213 records imported unchanged. |
| 2️⃣ | 🧹 Data Cleaning & Preparation | `Clean_Data`, `Cleaning_Log` | Fixed shifted headers, removed 1 incomplete record, checked duplicates (0), flagged outliers, set data types, added derived columns. |
| 3️⃣ | 🧮 Create Pivot Tables | `Pivots` | Four formula-driven summaries (COUNTIFS / AVERAGEIFS). |
| 4️⃣ | 🔍 Advanced Formulas | `Advanced_Formulas`, `Clean_Data` | VLOOKUP vs INDEX-MATCH, reverse lookups, two-way lookup, nested-IF `Risk_Flag`. |
| 5️⃣ | 📈 Data Visualization | `Charts`, `Dashboard` | 8 charts, color scales, data bars, threshold highlighting. |
| 6️⃣ | 🎛️ Interactive Dashboard | `Dashboard` | 3 dropdown filters drive KPIs, tables and charts; dynamic named ranges. |
| 7️⃣ | 📝 Documentation | `README` sheet, `Lookups`, this file | Sheet guide, naming conventions, assumptions. |

## 🗂️ Sheet guide

| Sheet | Purpose |
|---|---|
| 📖 `README` | In-workbook documentation. |
| 🎛️ `Dashboard` | Filters (yellow cells), KPI tiles, chart data and 4 charts. |
| 📥 `Raw_Data` | Data exactly as supplied (do not edit). |
| 🧾 `Cleaning_Log` | Live cleaning checks and the list of structural fixes. |
| ✨ `Clean_Data` | Analysis table `tbl_Students` (212 students) with derived columns. |
| 🧮 `Pivots` | Pivot-style summary tables. |
| 🔍 `Advanced_Formulas` | Lookup tools and formula logic. |
| 📈 `Charts` | Four charts built from `Pivots`. |
| ⚙️ `Lookups` | Band tables, dropdown lists, risk thresholds (editable). |

## 🎥 Video Demonstration

[![Watch Video](https://img.shields.io/badge/🎥-Watch_Video-red?style=for-the-badge)]([https://drive.google.com/file/d/1FvaRePRLKLKudx00dU6BR1QMPsuATuBr/view?usp=sharing](https://drive.google.com/file/d/1p5JsZ9NBVTg4v-vzn-Nlxng1W6UjImm0/view?usp=sharing))

## 🧹 Data cleaning notes

- 🔀 **Shifted headers:** in the source, `Student_ID` held a 1–213 row counter and every following header sat one column too early. Corrected order: Row_No, Student_ID, Study, Extracurricular, Sleep, Social, Physical, GPA, Stress_Level. After re-aligning, the five hour columns total exactly 24 for every student.
- ❌ **Incomplete record:** Student_ID 657 has no GPA or stress value and was removed (not imputed).
- ⚠️ **Outliers:** Students 546 and 616 report more than 11 hours of physical activity per day. Kept (their hours still total 24) and highlighted.
- 👯 **Duplicates:** none found.

## 🧩 Derived columns (`Clean_Data`)

| Column | Logic |
|---|---|
| ⏱️ `Total_Hours` | Sum of the five hour columns. |
| 🎓 `GPA_Band` | Approximate-match VLOOKUP on `Lookups`. |
| 📚 `Study_Band` | Approximate-match VLOOKUP on `Lookups`. |
| 🚦 `Risk_Flag` | 🔴 High Risk if sleep < 6 h and study ≥ 8 h; 🟡 Watch if sleep < 6 h, or physical < 1 h, or (High stress and GPA < 3.0); 🟢 otherwise Normal. |
| ✔️ `Hours_Check` | OK if daily hours total 24. |

## 🏷️ Naming conventions

- 📄 Sheets: `Title_Case_With_Underscores`
- 📋 Table: `tbl_Students`
- 🔗 Named ranges: `n_<column>` (dynamic data ranges), `f_<filter>` (dashboard criteria), `a_<name>` (assumption inputs)
- 🎨 Colors: 🟨 blue bold text on yellow = editable input; ⬛ black = formula; 🟧 orange cell = flagged outlier

## 🚀 How to use

1. 🎛️ Open the `Dashboard` and choose Stress Level, GPA Band and Study Band from the yellow dropdowns.
2. 🔍 On `Advanced_Formulas`, enter any Student_ID (445–656) to compare VLOOKUP and INDEX-MATCH results.
3. ⚙️ On `Lookups`, change band boundaries or risk thresholds to re-score all students.
4. ➕ To add data, append rows to `tbl_Students`; the named ranges expand automatically.

## 🧱 Adding native PivotTables and Slicers

These cannot be pre-built by script, but take about a minute in Excel:

1. 🧮 Click a cell in `Clean_Data` → Insert → PivotTable. Put `Stress_Level` in Rows and average `GPA` in Values.
2. 🔘 Select the table or PivotTable → Insert → Slicer → tick `Stress_Level`, `GPA_Band`, `Study_Band`.
3. 📅 A Timeline slicer does not apply because the dataset has no date column; the dashboard dropdowns serve the same purpose.

## 💡 Key findings

- 👥 212 students analysed; 52.8% are in the High stress group.
- 📈 Average GPA rises with study hours, from 2.79 (under 6 h) to 3.44 (9 h and above).
- 🎓 Average GPA by stress level: 🟢 Low 2.79, 🟡 Moderate 2.99, 🔴 High 3.26.
- 🚨 14 students (6.6%) are flagged High Risk by the illustrative rule above.

## 📌 Assumptions

- Column mapping was inferred from the 24-hour check described above.
- Risk thresholds are illustrative and editable in `Lookups`.
- No external validation of the dataset was performed.
