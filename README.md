# Crime Patterns and Socioeconomic Conditions in Los Angeles
### A Geospatial and Predictive Analytics Approach

**DAT 490 Capstone Project — Summer 2026**  
**Team CSI: Census Spatial Investigators**  
Lucas Wendell · Allen George · Hannah Smith · Jaclyn Giddens

---

## Overview

Crime in Los Angeles is not randomly distributed. This project combines LAPD crime incident data (2020–2024) with census tract-level socioeconomic indicators from the 2024 American Community Survey to examine whether neighborhood conditions can predict crime type and explain the geographic distribution of crime across Los Angeles. Two research questions guide the analysis:

- **RQ1:** How do neighborhood-level socioeconomic characteristics predict whether a crime incident is violent or property-related?
- **RQ2:** Are high-crime census tracts spatially clustered in the City of LA, and do neighboring tracts share similar socioeconomic characteristics?

---

## Data Sources

| Source | Description |
|--------|-------------|
| [LAPD Crime Data 2020–2024](https://data.lacity.org/Public-Safety/Crime-Data-from-2020-to-2024/2nrs-mtv8) | ~1M incident records with crime classifications and geographic coordinates |
| [2024 ACS 5-Year Estimates](https://api.census.gov/data/2024/acs/acs5) | Census tract-level socioeconomic indicators pulled via `tidycensus` |

---

## Methods

### RQ1 — Predictive Classification
- K-Means Clustering (neighborhood socioeconomic profiling)
- Naive Bayes
- Elastic Net Regularization
- Random Forest
- XGBoost

### RQ2 — Spatial Analysis
- Global Moran's I (spatial autocorrelation)
- LISA (Local Indicators of Spatial Association)
- Ordinary Least Squares (OLS)
- Geographically Weighted Regression (GWR)
- Multiscale Geographically Weighted Regression (MGWR)

---

## Key Findings

- Educational attainment and income are the most consistent predictors of crime type across all four classification models
- XGBoost is the strongest crime type classifier (F1 = 0.833), though MCC scores across all models remain compressed (0.148–0.173), reflecting the challenge of class imbalance
- Violent crime is significantly spatially clustered in central and south LA, overlapping with areas of high socioeconomic vulnerability
- MGWR explains 69.3% of variance in violent crime rates, a 36.6% improvement over OLS
- Median income and no vehicle rate are significant predictors of violent crime across all census tracts

---

## Dependencies

All analysis was conducted in R. Key packages:

```r
# Data
tidycensus, tidyverse, sf

# Modeling
ranger, xgboost, glmnet, e1071

# Spatial Analysis
spdep, GWmodel, mgwr

# Visualization
ggplot2, tmap, patchwork
```

---

## Course Information

DAT 490 — Capstone Project  
Summer 2026
