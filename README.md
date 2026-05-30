# 👶 Tennessee Childcare Cost Analysis

**Analysis of childcare cost trends in Tennessee from 2008–2018 using the National Database of Childcare Prices, framed as a data-driven policy communication project advocating for universal pre-K.**

> DSC 640 — Data Visualization | Bellevue University | By Matthew Rice

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Policy Context](#policy-context)
- [Dataset](#dataset)
- [Analysis](#analysis)
- [Key Findings](#key-findings)
- [Communication Strategy](#communication-strategy)
- [Assumptions and Limitations](#assumptions-and-limitations)
- [Ethical Considerations](#ethical-considerations)
- [Repository Structure](#repository-structure)
- [Requirements](#requirements)
- [How to Run](#how-to-run)
- [Author](#author)

---

## Project Overview

This project uses county-level childcare pricing data to examine how the cost of infant, toddler, and preschool care in Tennessee has changed over a decade. The analysis is designed not just as an academic exercise, but as the analytical foundation for a multi-format public communications campaign — translating data into accessible, policy-relevant messaging for Tennessee voters and working families.

**Primary question:** How have childcare costs in Tennessee trended from 2008 to 2018, and what do those trends mean for families and public policy?

---

## Policy Context

Ticket sales, concessions, and parking made up 41% of total MLB revenue in 2023 — but childcare is a different kind of infrastructure. In Tennessee, access to affordable pre-K is both a family issue and a broader economic issue:

- Rising childcare costs create barriers to workforce participation, particularly for mothers
- Preschool-age care (ages 3–5) represents a critical developmental window with long-term educational consequences
- Market-rate childcare costs in many Tennessee counties exceed what lower- and middle-income families can afford without public support

The analysis positions **universal pre-K not as a luxury, but as essential public infrastructure** — comparable to roads, utilities, and public schools — and uses the data to support that argument for a voter audience.

---

## Dataset

**Source:** [National Database of Childcare Prices](https://www.dol.gov/agencies/wb/topics/featured-childcare)  
**Provider:** U.S. Department of Labor, Women's Bureau  
**File:** `nationaldatabaseofchildcareprices.xlsx`  
**Coverage:** County-level annual estimates, all U.S. states, 2008–2018

### Key Fields Used

| Field | Description |
|---|---|
| `State_Name` | State name (filtered to Tennessee) |
| `StudyYear` | Year of data collection (2008–2018) |
| `MCInfant` | Median market-rate cost for infant care |
| `MCToddler` | Median market-rate cost for toddler care |
| `MCPreschool` | Median market-rate cost for preschool-age care |
| `TotalChildCareCost` | Derived field: sum of infant + toddler + preschool costs |

Data is aggregated from the county level to the state level by year for trend analysis.

---

## Analysis

The notebook filters the national dataset to Tennessee, engineers a `TotalChildCareCost` feature by summing across all three age groups, then aggregates by year to produce statewide totals. A line chart visualizes the resulting trend from 2008 to 2018.

**Transformation steps:**
1. Load national Excel dataset
2. Filter to `State_Name == "Tennessee"`
3. Derive `TotalChildCareCost = MCInfant + MCToddler + MCPreschool`
4. Group by `StudyYear` and sum total costs
5. Plot year-over-year trend

---

## Key Findings

- **Preschool-age childcare costs in Tennessee rose from approximately $27,000 in 2008 to roughly $36,000 in 2018** — a ~33% increase over the decade studied
- The trend is **sustained and consistent**, with no years of meaningful cost reduction
- Cost growth in the preschool category is especially notable given this age group represents a critical developmental period and the point at which many parents return to full workforce participation
- Rising costs may be **disproportionately affecting lower- and middle-income families**, reinforcing educational inequity across communities

---

## Communication Strategy

This project was designed as a **multi-format communications campaign** targeting Tennessee voters. The same underlying data is adapted across three distinct mediums:

| Medium | Format | Purpose |
|---|---|---|
| **Infographic** | Static visual | Clear, shareable summary of cost trends and the case for universal pre-K |
| **Reel** | Short video | Emotionally resonant storytelling combining statistics with real-world family scenarios |
| **Billboard** | Large-format print | Bold, simplified message — one statistic, one call to action |

**Target audience:** Tennessee voters, particularly parents, working families, and community members concerned about education and economic opportunity. Content is designed to be analytically credible but accessible — no technical jargon.

---

## Assumptions and Limitations

- Costs are aggregated across counties to produce statewide totals, which may obscure meaningful urban/rural variation in childcare pricing
- **Nominal dollar values are used** — no inflation adjustment was applied, meaning real cost growth is likely understated
- The dataset ends at 2018; trends since then, including potential acceleration post-pandemic, are not captured
- It is assumed the dataset accurately reflects prevailing market rates for childcare during the surveyed years

**Open questions for future analysis:**
- How do costs compare to Tennessee median household income by year?
- What is the urban vs. rural breakdown of childcare cost growth?
- How have costs continued to trend since 2018?

---

## Ethical Considerations

The dataset is publicly available, aggregated at the county and state level, and contains no personally identifiable information. No privacy, legal, or regulatory concerns are associated with its use.

All transformations — including state filtering, cost aggregation, and annual grouping — are explicitly documented. No data points were removed without acknowledgment. The analysis is disclosed as part of a policy advocacy framing, and readers should interpret findings in that context.

---

## Repository Structure

```
Childcare-Cost-Analysis/
│
├── notebooks/
│   └── DSC640_MatthewRice_Milestone1.ipynb    # Analysis and visualization notebook
│
└── README.md
```

> **Note:** `nationaldatabaseofchildcareprices.xlsx` is not included in this repository. Download it from the [U.S. Department of Labor](https://www.dol.gov/agencies/wb/topics/featured-childcare) and update the file path in the notebook before running.

---

## Requirements

```
pandas
matplotlib
openpyxl
```

Install dependencies:
```bash
pip install pandas matplotlib openpyxl
```

> `openpyxl` is required to read `.xlsx` files via `pd.read_excel()`.

---

## How to Run

1. Clone the repository:
```bash
git clone https://github.com/Bizarroxela/Childcare-Cost-Analysis.git
cd Childcare-Cost-Analysis
```

2. Download the dataset from the U.S. Department of Labor and update the file path in the notebook:
```python
df = pd.read_excel('/your/path/nationaldatabaseofchildcareprices.xlsx')
```

3. Launch the notebook:
```bash
jupyter notebook notebooks/DSC640_MatthewRice_Milestone1.ipynb
```

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Bizarroxela/Childcare-Cost-Analysis/blob/main/notebooks/DSC640_MatthewRice_Milestone1.ipynb)

---

## Author

**Matthew Rice** — [@Bizarroxela](https://github.com/Bizarroxela)

*Part of an applied data science portfolio covering data visualization, policy analytics, sports analytics, healthcare analytics, and machine learning.*
