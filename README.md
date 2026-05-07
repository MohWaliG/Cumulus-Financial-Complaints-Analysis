# Cumulus Financial — Consumer Complaints Analysis

> An interactive Excel + Power Pivot capstone project analysing **71,146 CFPB consumer complaint records (2011–2020)** to surface dispute drivers, product-level risk, and resolution-quality gaps for **Cumulus Financial**.

![Excel](https://img.shields.io/badge/Microsoft%20Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Power Pivot](https://img.shields.io/badge/Power%20Pivot-F2C811?style=flat&logo=microsoft&logoColor=black)
![Power Query](https://img.shields.io/badge/Power%20Query-376C2D?style=flat&logo=microsoft&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=flat&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat)

---

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Dataset Overview](#-dataset-overview)
- [Tools & Skills](#-tools--skills)
- [Methodology](#-methodology)
- [Dashboard Preview](#-dashboard-preview)
- [Key Findings](#-key-findings)
- [Recommendations](#-recommendations)
- [Data Limitations](#-data-limitations)
- [Repository Structure](#-repository-structure)
- [Author](#-author)

---

## 📊 Project Overview

This project was completed as part of **The Data Immersed (TDI) Sapphire Cohort Excel Capstone**. It transforms a nine-year regulatory complaints dataset from the U.S. **Consumer Financial Protection Bureau (CFPB)** into an interactive executive dashboard for **Cumulus Financial** — a multi-line financial services organisation.

The deliverable is a fully dynamic single-page Excel dashboard powered by a **Power Pivot star-schema data model**, **14 DAX measures**, **10 pivot tables**, **11 KPI cards**, **6 dynamic charts**, and **6 slicer controls**, enabling multi-dimensional exploration of complaint patterns across years, products, states, consumer groups, and resolution types.

---

## 🎯 Business Problem

Despite a strong **98.09% timely response rate**, Cumulus Financial faces a persistent consumer-satisfaction challenge:

- **19.13%** of resolved complaints are formally **disputed** by consumers.
- **72.04%** of complaints are closed with **explanation only** — no financial or corrective relief.
- Vulnerable consumer groups (Older Americans, Service Members) consistently dispute resolutions at higher rates than the general population.

The analysis seeks to answer: **Where is resolution quality breaking down, and what targeted interventions would reduce disputes most effectively?**

---

## 🗂 Dataset Overview

| Attribute | Value |
|---|---|
| **Source** | Consumer Financial Protection Bureau (CFPB) Complaint Database |
| **Period** | December 2011 – October 2020 |
| **Raw records** | 75,513 |
| **Cleaned records** | 71,146 |
| **Structure** | Star schema — 1 fact table + 2 dimension tables |

**Tables:**
- **Complaints** (fact table) — 71,146 rows × 14 columns
- **Products** (dimension) — 49 rows × 3 columns (8 parent product categories)
- **Issues** (dimension) — 230 rows × 3 columns (88 unique issues)

---

## 🛠 Tools & Skills

| Category | Tools / Techniques |
|---|---|
| **Data Cleaning & Transformation** | Power Query Editor, conditional columns, type standardisation, null handling |
| **Data Modelling** | Power Pivot star schema, relationship management, Date dimension table |
| **Calculated Logic** | DAX measures (CALCULATE, DIVIDE, SAMEPERIODLASTYEAR, ALL, VAR/RETURN) |
| **Analysis** | 10 pivot tables, cross-tabulation, time-intelligence, segmentation analysis |
| **Visualisation** | Excel dashboard design, slicers, KPI cards, line / bar / donut / clustered charts |
| **Documentation** | Microsoft Word (project documentation), structured executive reporting |

---

## 🔄 Methodology

```
Raw CFPB Data → Power Query Cleaning → Power Pivot Data Model →
DAX Measures → Pivot Tables → Interactive Dashboard → Insights & Recommendations
```

**1. Data Cleaning (Power Query)**
- Corrected column-header typo (`Date Sumbited` → `Date Submitted`).
- Standardised ZIP code data type to preserve leading zeros and partial-mask formats (e.g., `906XX`).
- Replaced structural nulls with meaningful labels: `General Consumer`, `Not Applicable`, `No Public Response`, `Not Recorded`.
- Removed an erroneous filter step in the Issues table that had reduced 230 rows to 48.

**2. Calculated Columns**
- Added 9 calculated columns including `Year`, `Month-Year`, `Days to Resolve`, `Resolution Category`, and binary flags (`Is Disputed`, `Is Timely`, `Is Monetary Relief`).
- Mapped 8 raw CFPB resolution values into 5 analytical buckets: *Monetary Relief, Non-Monetary Relief, Explanation Only, No Relief, Pending*.

**3. Data Modelling**
- Built star schema with relationships on `Product ID` and `Issue ID`.
- Added a Power Pivot Date table for time-intelligence DAX functions.

**4. DAX Measures (14 total)**
- Core volume measures (`Total Complains`, `Total Disputed`).
- Rate measures (`Dispute Rate`, `Timely Response Rate`, `Monetary Relief Rate`, `Explanation Rate`).
- Time intelligence (`YoY Growth` using `SAMEPERIODLASTYEAR`).
- Segment isolations for vulnerable groups.

**5. Dashboard Construction**
- Single-page interactive dashboard with three visual zones: header (slicers + branding), KPI band, and chart canvas.
- Cumulus Financial deep-navy brand palette.

---

## 📸 Dashboard Preview

> *Add dashboard screenshot here — `assets/dashboard-preview.png`*

**Eleven KPI metrics tracked:**

| KPI | Value |
|---|---|
| Total Complaints | 71,146 |
| Total Disputed | 7,218 (19.13%) |
| Timely Response Rate | 98.09% |
| Untimely Response Rate | 1.91% |
| Explanation Rate | 72.04% |
| Monetary Relief Rate | 15.62% |
| Monetary Relief Count | 11,114 |
| No Relief Count | 1,995 |
| YoY Growth | 13.35% |
| Average Days to Resolve | ~3 days |
| % of Total Complaints | 100% |

**Six dynamic charts:** Complaint Volume by Year, Complaint Volume by Channel, Timely Response Rate by Consumer Group, Complaints by Consumer Group, Product Complaints by Consumer Group, Complaint Volume by Resolution Type.

**Six slicers:** Consumer Disputation, Product, Response on Time, Year, Consumer Group, Resolution Category.

---

## 🔍 Key Findings

### 1. Resolution Quality Crisis
**72.04%** of all complaints (51,252 cases) are closed with **explanation only** — no compensation, no corrective action. This is the primary driver of the 19.13% dispute rate. Cases with monetary relief dispute at roughly **9.7%**, half the overall rate, proving compensation is the most effective dispute-reduction lever.

### 2. Product Concentration Risk
**Credit cards** account for **26.38% of all complaints** (18,768 cases) — the single highest-complaint product. Combined with *Credit card or prepaid card*, card products represent **39.63%** of total complaint volume.

### 3. Vulnerable Consumer Disparity
| Consumer Group | Dispute Rate |
|---|---|
| Service Members | **20.86%** |
| Older Americans | **20.32%** |
| General Consumers | 18.70% |

Credit card complaints are the dominant burden on Older Americans, representing **39.59%** of all their cases.

### 4. Operational Response Imbalance
**Vehicle loan or lease** complaints carry a **12.06% untimely response rate** — more than **6× the 1.91% overall average** — indicating a specific staffing or process gap in that team.

### 5. Geographic Concentration
**California, New York, Florida, and Texas** generate **43.90%** of all complaints. California alone records the highest dispute rate among top states at **21.54%**.

### 6. Temporal Trend & System Maturity
Complaint volume grew from 341 (2011) to 10,296 (2018, peak). Average resolution time improved from 3.53 to 2.48 days — but the explanation-only rate climbed to **76.80%** in 2018, suggesting throughput speed was prioritised over resolution substance as the system scaled.

---

## 💡 Recommendations

| # | Recommendation | Target Outcome |
|---|---|---|
| 1 | Increase monetary relief authorisation thresholds for front-line officers | Lift monetary relief rate from 15.62% → **25%**; reduce dispute rate to ~16% |
| 2 | Establish dedicated resolution protocol for Older Americans & Service Members | Bring vulnerable-group dispute rates **below** the general consumer benchmark |
| 3 | SLA remediation programme for the Vehicle Loan complaint team | Reduce vehicle loan untimely rate from 12.06% → **<3%** within two quarters |
| 4 | Root-cause review of top 5 credit card complaint issues | 15% complaint reduction = ~**2,817 fewer cases** annually |
| 5 | Deploy regional resolution resources in CA, NY, FL, TX | Targeted reduction of high-volume state disputes |
| 6 | Mandatory supervisor review for high-dispute issue closures | Block premature explanation-only closure on Cash advance (38.10%), Arbitration (28.12%), Balance transfer fee (26.23%), Credit decision (25.52%) |

---

## ⚠️ Data Limitations

- **Consumer Disputed field** was discontinued by CFPB after 2016 — dispute calculations are scoped to 2011–2016 records (38,568 known cases).
- **2020 data is partial** (January–October only); year-over-year comparisons should be read with this caveat.
- **ZIP codes** for low-population areas are partially masked (e.g., `906XX`) for privacy and cannot support granular geographic analysis.
- **Cleaned dataset** contains 71,146 records (down from 75,513 raw) — the cleaned set is the authoritative source for all reported figures.

---

## 📁 Repository Structure

```
Cumulus-Financial-Complaints-Analysis/
│
├── data/
│   └── Financial_Consumer_Complaints.xlsx       # Source dataset
│
├── dashboard/
│   └── Cumulus_Financial_Dashboard.xlsx         # Final interactive Excel dashboard
│
├── documentation/
│   └── Cumulus_FinancialProject_Documentation.docx
│
├── assets/
│   └── dashboard-preview.png                    # Dashboard screenshot
│
├── README.md
└── LICENSE
```

---

## 👤 Author

**Mohammed Wali Galkaye**
Data Analyst & AI Automation Specialist | Urban & Regional Planner

Project completed under: **The Data Immersed (TDI) — Sapphire Cohort Excel Capstone**, May 2026.

🔗 **Connect:**

- LinkedIn: [Wali Mohammed](https://linkedin.com/in/wali-mohammed-544206370)
- X (Twitter): [@MohdWaliGalkaye](https://x.com/MohdWaliGalkaye)

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

The CFPB Consumer Complaint Database is publicly available and used here for educational purposes under fair use.
