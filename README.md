# SA Fuel Price Prediction — 2024 Trend Analysis & Q1 2025 Forecast

Linear regression analysis of South African fuel prices across 2024, with forward predictions for Q1 2025. Covers Petrol 95 ULP, Diesel (0.05% Sulphur), and LPG.

---

## Overview

This script takes monthly ZAR/litre price data for the full 2024 calendar year, computes descriptive statistics per fuel type, fits OLS linear regression to identify trends, predicts prices for January–March 2025, and saves a two-panel visualisation to disk.

---

## What It Does

**Descriptive statistics** per fuel type:
- Starting and ending price
- Year-on-year change (ZAR and %)
- Mean, minimum, maximum, peak month

**Trend analysis via OLS linear regression** (`scipy.stats.linregress`):
- Monthly rate of change (slope)
- Trend direction: UPWARD / DOWNWARD / STABLE
- R² (trend strength / goodness of fit)

**Q1 2025 predictions** — extrapolated from 2024 regression line for months 13, 14, 15.

**Visualisation** — saved as `sa_fuel_price_analysis.png`:
- Panel 1: Historical 2024 price lines (all three fuel types)
- Panel 2: Trend lines extended into Q1 2025

---

## Key Results (2024 Data)

| Fuel Type | Jan 2024 | Peak | Dec 2024 | Trend | R² |
|---|---|---|---|---|---|
| Petrol 95 ULP | R20.50 | R22.15 (Aug) | R20.95 | Downward | — |
| Diesel 0.05% | R20.20 | R22.05 (Jul) | R20.75 | Downward | — |
| LPG | R12.50 | R13.85 (Jul) | R12.70 | Downward | — |

All three fuel types peaked mid-year and declined through Q4 2024.

**Q1 2025 Predictions (from regression):**
```
                    Jan 2025    Feb 2025    Mar 2025
Petrol (95 ULP):    R20.xx      R20.xx      R20.xx
Diesel (0.05%):     R20.xx      R20.xx      R20.xx
LPG:                R12.xx      R12.xx      R12.xx
```
*(Exact values printed at runtime — depend on fitted regression coefficients)*

---

## Requirements

```bash
pip install pandas numpy matplotlib scipy
```

```bash
python fuel_price_prediction.py
```

**Output:** `sa_fuel_price_analysis.png` (300 DPI, saved to working directory)

---

## Data Notes

- Prices are simulated to reflect realistic 2024 SA fuel price trends
- All prices in ZAR per litre
- Monthly frequency (`MS` — month start)
- The model uses a simple linear fit; real SA fuel prices are influenced by rand/dollar exchange rates, Brent crude, and regulated government adjustments — factors not captured here

---

## Structure

```
fuel_price_prediction.py
├── Data construction     # pandas DataFrame, 12-month arrays
├── Descriptive stats     # Per fuel type: range, mean, min/max
├── OLS regression loop   # scipy.stats.linregress per fuel type
├── Predictions           # Months 13–15 extrapolation
└── Visualisation         # matplotlib 2-panel figure + PNG save
```

---

## Extending the Model

Replace the hardcoded `petrol_prices`, `diesel_prices`, and `lpg_prices` arrays with real scraped or downloaded data from the Department of Mineral Resources and Energy (DMRE) or the Automobile Association (AA) of South Africa to make predictions live and accurate.
AUTHOR 
**RETSHIDISTSWE SEBEKEDI**
sebekediretshidisitswe@gmail.com
