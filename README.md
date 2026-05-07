# 🫀 Hypertension Cardiology Center — Clinical Analytics Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-0A3D7C?style=for-the-badge&logo=microsoft&logoColor=white)
![Vega](https://img.shields.io/badge/Vega--Lite-E24B4A?style=for-the-badge&logo=vega&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-1D9E75?style=for-the-badge)

> A comprehensive 2-page clinical analytics dashboard built in Power BI to identify predictors of BP control failure and determine the most effective antihypertensive drug class by patient comorbidity profile — using real-world structured patient data from a hypertension cardiology centre.

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Problem Statements](#-problem-statements)
- [Dataset](#-dataset)
- [Dashboard Pages](#-dashboard-pages)
- [Key Findings](#-key-findings)
- [DAX Measures & Calculated Columns](#-dax-measures--calculated-columns)
- [Visuals Inventory](#-visuals-inventory)
- [Color & Design System](#-color--design-system)
- [Custom Visuals](#-custom-visuals)
- [How to Use](#-how-to-use)
- [Recommendations](#-recommendations)
- [Project Structure](#-project-structure)
- [Author](#-author)

---

## 🔍 Project Overview

This project delivers a **clinical-grade Power BI dashboard** for the Hypertension Cardiology Center, analysing 350 patient records across 16 variables. The dashboard is designed for a **mixed audience** — clinical staff, hospital administrators, and researchers — and is structured around two core clinical problem statements.

The report is built entirely on a single dataset with no external data sources, using advanced DAX measures, calculated columns, conditional formatting, and a fully custom patient risk register built in **Deneb (Vega)**.

---

## ❓ Problem Statements

### Problem 1
> **What predicts BP control failure at 3 months, and can we identify high-risk patients at the point of prescription?**

### Problem 2
> **Which antihypertensive drug class delivers the best outcomes for patients with specific comorbidity profiles?**

---

## 📊 Dataset

| Attribute | Detail |
|---|---|
| **File** | `Hypertension_Cardiology_Center_Dataset.xlsx` |
| **Rows** | 350 patients |
| **Columns** | 16 variables |
| **Period** | January – December 2024 |
| **Missing values** | None (100% complete) |
| **Outcome variable** | `BP_Controlled_After_3_Months` (Yes/No) |

### Variable Dictionary

| Column | Type | Range / Values |
|---|---|---|
| `Patient_ID` | Text | HTN0001 – HTN0350 |
| `Age` | Integer | 30 – 85 years |
| `Gender` | Categorical | Male / Female |
| `Diabetes_Mellitus` | Binary | Yes / No |
| `Chronic_Kidney_Disease` | Binary | Yes / No |
| `Dyslipidemia` | Binary | Yes / No |
| `Obesity` | Binary | Yes / No |
| `Baseline_Systolic_BP` | Integer | 140 – 190 mmHg |
| `Baseline_Diastolic_BP` | Integer | Numeric (mmHg) |
| `Antihypertensive_Class` | Categorical | 6 drug classes |
| `Medication_Adherence` | Ordinal | Good / Moderate / Poor |
| `Followup_Systolic_BP` | Integer | Numeric (mmHg) |
| `Followup_Diastolic_BP` | Integer | Numeric (mmHg) |
| `BP_Controlled_After_3_Months` | Binary | Yes (33) / No (317) |
| `Number_of_Visits` | Integer | 1 – 6 |
| `Registration_Date` | Date | Jan 1 – Dec 31, 2024 |

---

## 📑 Dashboard Pages

### Page 1 — Problem 1: BP Control Failure & Risk Prediction

| Zone | Visual |
|---|---|
| Top bar | 4 slicers: Age Group, Date Hierarchy, Risk Category, Gender |
| Key Insights | Dynamic Key Insight 1 text measure |
| KPI row | Total Patients · BP Control Rate · High-Risk Patients · Standard-Risk Control Rate · Avg Systolic Reduction |
| Middle left | Risk Stratification Matrix (Heatmap: SBP Tier × Adherence) |
| Middle centre | Heatmap recommendation card |
| Middle right | Age Group Impact on Control Rate (bar chart + parameter selector) |
| Bottom | High-Risk Patient Flags — Point-of-Prescription Risk Register (Deneb custom table) |
<img width="769" height="499" alt="Pg1" src="https://github.com/user-attachments/assets/e86976ab-60c3-4f3c-abc2-e5752afaf685" />

### Page 2 — Problem 2: Drug Class Efficacy by Comorbidity

| Zone | Visual |
|---|---|
| Top bar | Same 4 slicers + navigation button |
| Key Insights | Dynamic Key Insight 2 text measure |
| KPI row | Same 5 KPI cards |
| Row 1 (4 charts) | Best Drug: Diabetic · Dyslipidemia · CKD · Obesity patients |
| Row 1 recommendations | 4 dynamic Rx recommendation cards |
| Bottom left | Scatter Plot: BP Control Rate vs Avg Systolic Reduction per drug |
| Bottom centre | Comorbidity Profile vs BP Control — Drug Class Interaction (clustered column) |
| Bottom right | Comorbidity Burden vs Control Rate (bar chart) |
| Footer | Overall drug class recommendation card |
<img width="773" height="498" alt="Pg2" src="https://github.com/user-attachments/assets/010479e4-f563-4c00-977f-ec784e676300" />

---

## 💡 Key Findings

### Problem 1 — BP Control Failure Predictors

| Finding | Value |
|---|---|
| Overall BP control rate | **9.43%** — critically low |
| Poor adherence control rate | **1.77%** — single strongest predictor |
| Good adherence control rate | **15.24%** |
| High-risk patients (270) control rate | **4.44%** |
| Standard-risk patients (80) control rate | **26.25%** |
| Risk gap | **6× better** in standard-risk group |
| Critical cell (Poor adherence + SBP >170) | **0% control** (39 patients) |
| Best cell (Good adherence + SBP <160) | **48.39% control** |
| Strongest age group | **40–55 years** — 12.26% control |

### Problem 2 — Drug Class Efficacy

| Drug Class | Control Rate | Avg SBP Reduction | Best For |
|---|---|---|---|
| **Combination Therapy** | **21.05%** | **21.68 mmHg** | Diabetes (25%), Dyslipidemia (25.93%), Obesity (18.42%) |
| Thiazide Diuretic | 13.11% | 13.90 mmHg | **CKD patients (17.65%)** |
| Beta Blocker | 9.84% | 12.89 mmHg | Non-CKD (15.4%) |
| ARB | 5.88% | 11.12 mmHg | Second-line only |
| Calcium Channel Blocker | 5.17% | 12.59 mmHg | — |
| **ACE Inhibitor** | **0.00%** | 15.91 mmHg | **Avoid — 0% across all profiles** |

> ⚠️ **ACE Inhibitor Paradox:** ACE Inhibitor achieves the 2nd highest BP reduction (15.91 mmHg) but 0% BP control — the drug lowers BP but never reaches the controlled threshold. Urgent protocol review required for all 45 ACE Inhibitor patients.

---

## 🧮 DAX Measures & Calculated Columns

### Calculated Columns

```dax
-- 1. Comorbidity Count (0–4)
Comorbidity_Count =
    (IF([Diabetes_Mellitus] = "Yes", 1, 0))
  + (IF([Chronic_Kidney_Disease] = "Yes", 1, 0))
  + (IF([Dyslipidemia] = "Yes", 1, 0))
  + (IF([Obesity] = "Yes", 1, 0))

-- 2. Risk Score (0–8 composite index)
Risk_Score =
    IF([Medication_Adherence] = "Poor", 3,
        IF([Medication_Adherence] = "Moderate", 1, 0))
  + IF([Baseline_Systolic_BP] >= 170, 2,
        IF([Baseline_Systolic_BP] >= 160, 1, 0))
  + [Comorbidity_Count]

-- 3. Risk Category
Risk_Category =
    IF(
        [Medication_Adherence] = "Poor"
        || [Baseline_Systolic_BP] >= 170
        || [Comorbidity_Count] >= 3,
        "High Risk", "Standard Risk"
    )

-- 4. Systolic Reduction
Systolic_Reduction = [Baseline_Systolic_BP] - [Followup_Systolic_BP]

-- 5. Diastolic Reduction
Diastolic_Reduction = [Baseline_Diastolic_BP] - [Followup_Diastolic_BP]

-- 6. Age Group
Age_Group =
    IF([Age] <= 40, "Under 40",
        IF([Age] <= 55, "40-55",
            IF([Age] <= 70, "56-70", "Above 70")))

-- 7. SBP Tier
SBP_Tier =
    IF([Baseline_Systolic_BP] >= 170, ">170 mmHg (Severe)",
        IF([Baseline_Systolic_BP] >= 160, "160-170 mmHg (Moderate)",
            "140-160 mmHg (Mild)"))
```

### Key Measures

```dax
-- Core outcome measures
Total_Patients = COUNTROWS('HypertensionData')

BP_Control_Rate =
    DIVIDE(
        CALCULATE(COUNTROWS('HypertensionData'),
            [BP_Controlled_After_3_Months] = "Yes"),
        COUNTROWS('HypertensionData'), 0) * 100

Patients_Controlled =
    CALCULATE(COUNTROWS('HypertensionData'),
        [BP_Controlled_After_3_Months] = "Yes")

High_Risk_Count =
    CALCULATE(COUNTROWS('HypertensionData'),
        [Risk_Category] = "High Risk")

High_Risk_Control_Rate =
    CALCULATE([BP_Control_Rate], [Risk_Category] = "High Risk")

Standard_Risk_Control_Rate =
    CALCULATE([BP_Control_Rate], [Risk_Category] = "Standard Risk")

Avg_Systolic_Reduction = AVERAGE('HypertensionData'[Systolic_Reduction])

Avg_Diastolic_Reduction = AVERAGE('HypertensionData'[Diastolic_Reduction])

Risk_Control_Gap = [Standard_Risk_Control_Rate] - [High_Risk_Control_Rate]

-- Risk matrix label (used in heatmap cells)
Risk_Matrix_Label =
VAR Rate = [BP_Control_Rate]
VAR RiskLevel =
    IF(Rate >= 0.15, "Low risk",
        IF(Rate >= 0.08, "Mod risk",
            IF(Rate >= 0.03, "High risk",
                IF(Rate > 0, "Very high", "Critical"))))
RETURN "~" & FORMAT(Rate, "0.00%") & " " & RiskLevel
```

---

## 📐 Visuals Inventory

### Page 1 — Problem 1 Visuals (11 total)

| # | Visual | Type | Fields |
|---|---|---|---|
| 1 | Total Patients | KPI Card | `Total_Patients` |
| 2 | BP Control Rate | KPI Card | `BP_Control_Rate` |
| 3 | High-Risk Patients | KPI Card | `High_Risk_Count` |
| 4 | Standard-Risk Control Rate | KPI Card | `Standard_Risk_Control_Rate` |
| 5 | Avg Systolic Reduction | KPI Card | `Avg_Systolic_Reduction` |
| 6 | Risk Stratification Matrix | Matrix Heatmap | Rows: `SBP_Tier` · Cols: `Medication_Adherence` · Values: `Risk_Matrix_Label` |
| 7 | Age Group Impact on Control Rate | Clustered Bar | X: `Age_Group` · Y: `BP_Control_Rate` |
| 8 | High-Risk Patient Risk Register | Deneb (Vega) Table | 10 columns sorted by `Risk_Score` DESC |
| 9 | Key Insight 1 | Text Card | `Key_Insight_1` measure |
| 10 | Heatmap Recommendation | Text Card | `Rec_P1_Heatmap_SBPAdherence` |
| 11 | Age Group Recommendation | Text Card | `Rec_P1_AgeGroup` |

### Page 2 — Problem 2 Visuals (11 total)

| # | Visual | Type | Fields |
|---|---|---|---|
| 1–5 | KPI Cards (shared) | KPI Card | Same 5 measures |
| 6 | Best Drug — Diabetic | Clustered Bar | Filter: `Diabetes_Mellitus = "Yes"` |
| 7 | Best Drug — Dyslipidemia | Clustered Bar | Filter: `Dyslipidemia = "Yes"` |
| 8 | Best Drug — CKD | Clustered Bar | Filter: `CKD = "Yes"` |
| 9 | Best Drug — Obesity | Clustered Bar | Filter: `Obesity = "Yes"` |
| 10 | Scatter: Control Rate vs SBP Reduction | Scatter Plot | X: `BP_Control_Rate` · Y: `Avg_Systolic_Reduction` · Legend: `Antihypertensive_Class` |
| 11 | Drug Class Interaction | Grouped Column | X: `Antihypertensive_Class` · Y: `Avg_Systolic_Reduction` + `Avg_Diastolic_Reduction` |
| 12 | Comorbidity Burden vs Control | Bar Chart | X: `Comorbidity_Count` · Y: `BP_Control_Rate` |
| 13 | Key Insight 2 | Text Card | `Key_Insight_2` measure |
| 14–17 | Rx Recommendation Cards (4) | Text Cards | `Rec_Diabetic_Drug`, `Rec_CKD_Drug`, `Rec_Dyslipidemia_Drug`, `Rec_Obesity_Drug` |
| 18 | Overall Drug Recommendation | Text Card | `Rec_P2_DrugClassOverall` |

---

## 🎨 Color & Design System

### Brand Colors (1–8)

| # | Name | Hex | Usage |
|---|---|---|---|
| 1 | Navy | `#0A3D7C` | Header, dominant brand |
| 2 | Blue | `#185FA5` | Primary accent, links |
| 3 | Sky Blue | `#378ADD` | Charts, bars |
| 4 | Ice Blue | `#B5D4F4` | Borders, light fills |
| 5 | Pale Blue | `#EBF4FB` | Panel backgrounds |
| 6 | Charcoal | `#1A2E44` | Headings, dark text |
| 7 | Mid Gray | `#5A7A9E` | Body text, subtitles |
| 8 | Light Gray | `#E8EDF3` | Page background, gridlines |

### Sentiment Colors

| State | Hex | Usage |
|---|---|---|
| Negative | `#A32D2D` | BP uncontrolled, High Risk, ACE 0% |
| Positive | `#0F6E56` | BP controlled, Good adherence |
| Neutral | `#854F0B` | Moderate adherence, amber alerts |

### Divergent Scale (Risk Matrix)

`#E24B4A` → `#F5D5C0` → `#FAEEDA` → `#C0DD97` → `#1D9E75`

Min (0% control) → Middle (8–14%) → Max (≥17% control)

### Typography

| Role | Font | Size | Color |
|---|---|---|---|
| Report title | Arial Bold | 13pt | `#FFFFFF` |
| Section headings | Arial Bold | 11pt | `#0A3D7C` |
| Visual titles | Arial Bold | 8.5pt | `#1A2E44` |
| Body / labels | Arial Regular | 8–9pt | `#5A7A9E` |
| KPI values | Arial Bold | 22–36pt | Sentiment color |
| DAX / hex codes | Courier New | 7.5pt | `#1A2E44` |

---

## 🛠 Custom Visuals

**Fields used for the matrix:** `Patient_ID`, `Age`, `Gender`, `Antihypertensive_Class`, `Baseline_Systolic_BP`, `Medication_Adherence`, `Comorbidity_Count`, `Risk_Score`, `Risk_Category`, `BP_Controlled_After_3_Months` + 5 color measures

---

### Setup Steps

**1. Load the data**
```
Home → Get Data → Excel Workbook
→ Select Hypertension_Cardiology_Center_Dataset.xlsx
→ Rename table to 'Hypertension_Data'
```

**2. Power Query transformations**
```
- Registration_Date → Date type
- All Yes/No columns → Text type
- Age, BP columns → Whole Number type
- Close & Apply
```

**3. Create calculated columns** (in this order)
```
Comorbidity_Count → Risk_Score → Risk_Category →
Systolic_Reduction → Diastolic_Reduction → Age_Group → SBP_Tier
```

**4. Create Measures table**
```
Enter Data → Name it 'Measures'
→ Add all DAX measures listed above
```

**5. Build visuals**
- Follow the Visuals Inventory table above
- Apply conditional formatting rules using `BP_Control_Rate` as the base field
- Install Deneb from AppSource and paste the Vega spec for the patient table

**6. Apply the background**
```
Export Slide 1 from HCC_PowerBI_Background_ColorTemplate.pptx as PNG
→ Power BI → View → Wallpaper → Upload PNG → Transparency: 0%

```
Background 1:
<img width="1920" height="1250" alt="background0" src="https://github.com/user-attachments/assets/24783298-1653-4aaa-a715-0fcf91286068" />

Background 2:
<img width="1920" height="1250" alt="background1" src="https://github.com/user-attachments/assets/2dd29e19-aa3d-4120-952e-80bb2e4c1e93" />

---

### Slicers
| Slicer | Field | Style |
|---|---|---|
| Age Group | `Age_Group` | Dropdown |
| Date Hierarchy | `Registration_Date` hierarchy | Dropdown |
| Risk Category | `Risk_Category` | Dropdown |
| Gender | `Gender` | Dropdown |

---

## 📌 Recommendations

### Problem 1 — BP Control Failure

1. **Deploy Risk_Score at prescription** — Score ≥5 (Poor adherence + SBP ≥170 + ≥3 comorbidities) achieves near-zero control. Mandatory specialist escalation required.
2. **Adherence programme** — Poor adherence is the single strongest predictor (1.77% control). Implement SMS reminders and structured counselling before drug escalation.
3. **Comorbidity escalation protocol** — Zero-comorbidity patients achieve 17.65% control. Escalate to Combination Therapy and 2-week follow-up for patients with ≥3 comorbidities.
4. **SBP severity awareness** — Good adherence + SBP <160 achieves 48.39% control vs 0% for Poor adherence + SBP >170. Both factors must be addressed simultaneously.
5. **Age-targeted care** — Patients aged 70+ achieve near-zero control. Introduce simplified once-daily regimens and carer-assisted adherence support.

### Problem 2 — Drug Class Selection

1. **Combination Therapy as default first-line** — 21.05% control, 21.68 mmHg reduction. Best for Diabetic (25%), Dyslipidemia (25.93%), and Obese (18.42%) patients.
2. **Thiazide Diuretic for CKD patients** — Outperforms Combination Therapy in CKD (17.65% vs 11.54%). Monitor electrolytes closely.
3. **Urgent ACE Inhibitor protocol review** — 0% control in all 45 patients across all comorbidity profiles. Switch to Combination Therapy or ACE + Thiazide combination.
4. **Avoid Beta Blocker in obese patients** — 3.70% control rate — the lowest drug-comorbidity combination in the dataset.
5. **Avoid CCB for dyslipidemia patients** — 3.23% control rate. Combination Therapy is 8× more effective.

---

## 📁 Project Structure

```
hypertension-analytics-dashboard/
│
├── 📊 Data/
│   └── Hypertension_Cardiology_Center_Dataset.xlsx
│
├── 📋 Report/
│   ├── HCC_PowerBI_Report.pbix
│   └── Hypertension_Treatment_Outcome_Risk_Analytics_Dashboard.pdf
│
├── 🎨 Design/
│   └── HCC_PowerBI_Background_ColorTemplate.pptx
│
├── 📄 Documentation/
│   ├── HCC_PowerBI_Report.docx          ← Full analytical report with all DAX
│   └── README.md                         ← This file
│
└── 🧮 DAX/
    ├── calculated_columns.dax
    ├── measures_core.dax
    ├── measures_kpi_text.dax
    ├── measures_recommendations.dax
    └── vega_spec_patient_table.json
```

---

## 👤 Author

**Built as part of a clinical data analytics challenge by [Zion Tech Hub](https://www.linkedin.com/company/zion-tech-hub/posts/?feedView=all) and [Godsent Ndoma](https://www.linkedin.com/in/godsent-ndoma-7b919322b/) **
Dataset: Hypertension Cardiology Center · 350 patients · Jan–Dec 2024
Tools: Power BI Desktop · DAX · Excel
Created By: [Emmanuel Idowu](https://www.linkedin.com/in/emmanuel-idowu-analyst/)
---

## 📜 License

This project is for educational and portfolio purposes.
Dataset is anonymised synthetic clinical data.

---

*If this project helped you, consider leaving a ⭐ on the repository.*
