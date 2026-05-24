# Analyzing Real Estate Market with CAPM
### A Comparative Study of House Prices and Rents in Major US Cities

**Authors:** Vaishnavi V. Mane | Gaurav Arvind Singh  
**Date:** April 2023 | University of Maryland, Baltimore County

---

## Objective
Apply the Capital Asset Pricing Model (CAPM) to the US real estate market to identify the best cities for real estate investment by analyzing risk-adjusted returns on both rental income and home values across 5 major US cities.

---

## Datasets

| Dataset | Source | Coverage | Size |
|---|---|---|---|
| Zillow Observed Rent Index (ZORI) | Zillow | Mar 2015 – Feb 2023 | 511 regions × 401 columns |
| Zillow Home Value Index (ZHVI) | Zillow | Jan 2000 – Feb 2023 | 896 regions × 283 columns |
| Risk-Free Rate | FRED API | Apr 2015 – Feb 2023 | Daily → converted to monthly |

**Geographic levels:** National, Metropolitan, County, City, and Zip Code (510 MSAs analyzed)

---

## Methodology

### 1. Data Collection & Cleaning
- Downloaded ZORI and ZHVI datasets from Zillow's public data portal
- Pulled daily risk-free rate (Treasury yield) from FRED API
- Handled missing (NaN) values across both datasets
- Converted daily risk-free rates to monthly using mean aggregation

### 2. Data Transformation
- Reshaped wide-format time series into long format for analysis
- Computed monthly returns for both rent indices and home values
- Calculated excess returns: `Excess Return = Asset Return - Risk-Free Rate`

### 3. CAPM Application
Applied the CAPM formula to real estate:

```
ER_i = R_f + β_i (ER_m - R_f)
```

Where:
- `ER_i` = Expected return of the city's real estate market
- `R_f` = Risk-free rate (FRED Treasury yield)
- `β_i` = Beta of the city relative to the US national market
- `(ER_m - R_f)` = Market risk premium

### 4. Computed Metrics (5 Cities: NY, Chicago, Dallas, LA, DC)
- **Beta (β):** Sensitivity of city returns relative to national market
- **Alpha (α):** Excess return above CAPM-predicted return
- **Security Market Line (SML):** Plotted for both rents and home values

---

## Key Results

| City | Beta (Value) | Alpha (Value) | Beta (Rent) | Alpha (Rent) |
|------|-------------|--------------|-------------|-------------|
| New York, NY | 0.642 | +0.060 | 1.481 | -0.370 |
| Chicago, IL | 0.654 | -0.107 | 1.065 | -0.170 |
| Dallas, TX | 1.157 | -0.046 | 1.147 | -0.040 |
| Los Angeles, CA | 1.165 | -0.167 | 0.801 | +0.085 |
| Washington, DC | 0.804 | -0.125 | 1.147 | -0.040 |

### Insights
- **New York** shows positive alpha on home values (+0.06) — home values are slightly undervalued relative to CAPM prediction, suggesting investment opportunity
- **Los Angeles** shows positive alpha on rents (+0.085) — rental market offers excess returns above market expectation
- **Dallas and LA** have high betas (>1.1) on home values — higher risk but market-aligned returns
- **New York rent market** has the highest beta (1.48) — most sensitive to national rent market movements

---

## Tools & Technologies
- **Python:** Pandas, NumPy, Matplotlib, SciPy
- **Data Sources:** Zillow Public Data, FRED API
- **Statistical Methods:** CAPM, Beta/Alpha computation, OLS Regression, Security Market Line
- **Visualization:** Time series plots, SML charts, excess return analysis

---

## Files
- `Combined_FDS_Project.ipynb` — Full analysis notebook (data loading, cleaning, CAPM computation, visualizations)
- `Presentation_CAPM.pptx` — Final project presentation

---

## How to Run

```bash
# Install dependencies
pip install pandas numpy matplotlib scipy fredapi

# Launch notebook
jupyter notebook Combined_FDS_Project.ipynb
```

> **Note:** FRED API key required for risk-free rate data. Get a free key at https://fred.stlouisfed.org/docs/api/api_key.html

---

## Academic Context
This project was completed as part of the Data Science program at the University of Maryland, Baltimore County (UMBC), applying financial modeling concepts to real estate market analysis.
