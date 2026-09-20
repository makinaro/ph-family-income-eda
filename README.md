# Household Spending on Alcohol and Tobacco in the Philippines

Exploratory data analysis and modeling of household "vice" spending (alcohol and tobacco) using the Philippine Statistics Authority's **Family Income and Expenditure Survey (FIES) 2023**.

## Questions

1. How many Filipino households buy alcohol or tobacco, and how much do they spend?
2. How does vice spending change across income groups? Do poorer households spend a larger share of their budget?
3. How does it vary by region and between urban and rural areas?
4. Do households that spend heavily on vices spend less on education and health?
5. Can we predict whether a household buys tobacco, and how much a buying household spends?
6. What spending profiles do households fall into, and which profiles spend the most on vices?

## Data

| | |
|---|---|
| Source | [PSA Data Archive, FIES 2023](https://psada.psa.gov.ph/catalog/318) |
| File | `FIES PUF 2023 Volume1.CSV` (public use file, Volume 1) |
| Size | 163,268 households × 90 columns, ~142 MB |
| Unit | One row = one household |

The data file is **not included** in this repository because of its size. Download it from the PSA Data Archive and place it in the project root.

### Key columns

| Column | Description |
|---|---|
| `ALCOHOL`, `TOBACCO` | Annual household spending on alcoholic beverages and tobacco (₱) |
| `TOINC`, `TOTEX` | Total annual household income and expenditure (₱) |
| `FOOD`, `NFOOD` | Food and non-food expenditure (`TOTEX = FOOD + NFOOD`) |
| `WAGES`, `CASH_ABROAD`, `PENSION` | Income sources, including remittances from abroad |
| `FSIZE` | Family size |
| `W_REGN`, `URB` | Region code; urban (1) / rural (2) |
| `NPCINC` | National per-capita income decile (1 = poorest, 10 = richest) |
| `RFACT` | Household survey weight |

### Notes

- `ALCOHOL` and `TOBACCO` measure **household spending**, not individual smoking or drinking. A ₱0 value means the household did not buy these items, not that no one in the household smokes or drinks.
- All population-level figures are **weighted** with `RFACT`, which sums to ~27.5 million households.
- `TOTEX` and `NFOOD` already include alcohol and tobacco spending, so they are excluded from model features to avoid leakage.
- Volume 1 does not contain household-head characteristics (sex, age, education, occupation). These are in Volume 2 of the PUF.

## Project structure

```
ph-family-income-eda/
├── README.md
├── requirements.txt
├── fies_2023_vices_analysis.ipynb   # main analysis notebook
└── FIES PUF 2023 Volume1.CSV        # data (download separately)
```

## Notebook outline

1. Data Loading and Initial Inspection
2. Data Cleaning and Feature Engineering
3. Exploratory Data Analysis
4. Statistical Checks
5. Feature Preparation
6. Machine Learning: tobacco purchase (classification), spending amount (regression), and household spending profiles (K-Means clustering)
7. Summary and Recommendations

## Setup

Requires Python 3.10+.

**1. Create and activate a virtual environment**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Run the notebook**

```bash
jupyter notebook fies_2023_vices_analysis.ipynb
```

## Status

🚧 Scaffolding: section structure is in place and the analysis is in progress.
