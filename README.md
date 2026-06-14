A cross-sectional regression study identifying the macroeconomic drivers of GDP per capita growth across 52 Asia-Pacific economies during the 2020 COVID-19 crisis, using World Bank World Development Indicators data.
 
---
 
## Overview
 
Asia-Pacific economies contracted by just 0.4% in 2020 compared to a global contraction of ~3.1%, making them a compelling case for understanding what underpins economic resilience during a crisis. This project builds and validates an OLS regression model to identify which macroeconomic factors significantly explain variation in GDP per capita growth across the region.
 
**Key finding:** Of the six candidate predictors tested, current account balance (% of GDP) and gross capital formation (% of GDP) emerged as the significant determinants of GDP per capita growth in 2020, while inflation, exports, labour force participation, and fiscal balance were not statistically significant in the Asia-Pacific context during the pandemic.
 
---
 
## Repository Structure
 
```
├── dataset.csv                    # Raw World Bank WDI data (52 countries, 2020)
├── Dataset_Cleaned.csv            # Cleaned, analysis-ready dataset
├── Dataset_Cleaning.Rmd           # Full data cleaning pipeline (R)
├── Main_Econometrics_Project.Rmd  # Regression modelling and diagnostics (R)
└── EC6062_Project_Report_final.pdf  # Full written report
```
 
---
 
## Methodology
 
### Data
- **Source:** World Bank World Development Indicators (WDI)
- **Scope:** 52 Asia-Pacific countries, cross-section for 2020
- **Dependent variable:** GDP per capita growth (annual %)
- **Independent variables:** Inflation, fiscal balance, current account balance, gross capital formation, labour force participation rate, exports (all as % of GDP where applicable)
### Data Cleaning (R — `tidyverse`, `janitor`, `countrycode`)
A nine-step cleaning pipeline handled:
- Wide-to-long reshaping via `pivot_longer()`
- Metadata row removal and column standardisation to `snake_case`
- ISO3 country code assignment via `countrycode()`
- Duplicate resolution and outlier removal (IQR method on GDP growth)
- Missingness thresholding — columns with >40% missing values dropped
### Regression Analysis
- **Baseline model:** Full six-predictor OLS regression
- **Diagnostics:** F-test, VIF (multicollinearity), individual t-tests, joint hypothesis testing, Ramsey RESET test (functional form)
- **Final model:** Refined specification retaining significant predictors
- **Heteroscedasticity checks:** Breusch-Pagan test, White test, residuals vs fitted plot — all confirmed homoscedasticity, validating OLS standard errors
---
 
## Results
 
The final model identified two statistically significant predictors at the 5% level:
 
| Variable | Direction | Interpretation |
|---|---|---|
| Current account balance (% GDP) | Positive | Net capital inflows associated with stronger growth |
| Gross capital formation (% GDP) | Positive | Higher investment spending linked to GDP growth |
 
**Policy implication:** Asia-Pacific governments prioritising investment-friendly conditions and current account management are better positioned for resilience during crisis periods.
 
**Limitations:** Single-year cross-sectional data may overstate pandemic-era effects; omitted variables (institutional quality, healthcare capacity, pandemic response) are acknowledged. Panel data across multiple years would improve generalisability.
 
---
 
## Tools & Technologies
 
- **R** — data cleaning, EDA, regression modelling
- **Packages:** `tidyverse`, `janitor`, `countrycode`, `lmtest`, `sandwich`, `car`, `broom`, `ggplot2`, `kableExtra`
- **R Markdown** — reproducible analysis and reporting
