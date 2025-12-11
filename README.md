# Chicago-FHV-Demand-Forecasting
PySpark ML project forecasting Chicago ride-hailing demand (Uber/Lyft/Taxi) at 15-minute intervals across 77 neighborhoods. Analyzes 500M+ trips from the Chicago Data Portal with NOAA weather data. Random Forest model achieves R²=0.78. Finds time patterns dominate demand; weather has minimal impact.

## Overview

This project analyzes over 500 million trip records from the Chicago Data Portal to build a demand forecasting model that helps:
- **Drivers** identify high-demand areas and optimal times to maximize earnings
- **Riders** anticipate demand patterns to avoid surge pricing and ensure quick pickups

## Key Results

- **Model Performance**: Random Forest Regressor achieves R² = 0.78 with RMSE of 32.43 rides
- **Strong Predictability**: 65%+ of community areas show RMSE of 5-10 rides
- **Time is King**: Demand correlates 0.99 with 15-min prior and 0.80 with same time yesterday
- **Weather Myth Busted**: Temperature and precipitation show minimal impact on demand

## Data Sources

| Dataset | Source | Records |
|---------|--------|---------|
| TNP Trips (2018-2022) | Chicago Data Portal | ~300M |
| Taxi Trips (2013-2023) | Chicago Data Portal | ~212M |
| Weather Data | NOAA Integrated Surface Dataset | ~24K hourly |

*Analysis focused on post-pandemic data: February 2021 – December 2022*

## Methodology

1. **Data Processing**: PySpark for large-scale ETL on Google Cloud Dataproc
2. **Feature Engineering**: Temporal features (hour, day, month), weather lags, community area encoding
3. **Model**: Random Forest Regressor with 50 trees, max depth 8
4. **Train/Test Split**: Temporal split (~74% train, 26% test)

## Key Findings

- **Top Demand Areas**: Near North Side, Loop, O'Hare, West Town, Lake View
- **TNP Dominance**: Post-pandemic, TNPs dramatically outpace traditional taxis
- **Pricing Insight**: Taxis cheaper for trips under 15 miles; TNPs preferred for convenience
- **Consistent Patterns**: Strong daily/weekly demand cycles enable reliable forecasting

## Tech Stack

- **Processing**: PySpark, Google Cloud Dataproc
- **ML**: PySpark MLlib (RandomForestRegressor, VectorAssembler, Pipeline)
- **Visualization**: Matplotlib, Seaborn
- **Environment**: Jupyter Notebooks, Google Colab

## Project Structure

```
├── Final-Chicago-FHV-Demand-Forecasting.ipynb  # Final/Main analysis notebook
├── LICENSE # MIT
├── Phase1-Chicago-Ride-Hailing-vs-Taxi.ipynb # Phase 1 analysis notebook (Informed "Final" analysis)
├── README.md
```

## Team

QST 843 - Team 8 (Boston University Questrom School of Business)
- Olivia Chen
- Eric Dahlberg
- Pratik Mahajan
- Brendan Wilcox
- Roxy Zhang

## References

1. Alphabet Inc. (n.d.). Google Gemini. Google. https://gemini.google.com/

2. Anthropic PBC. (n.d.). Claude.AI. Anthropic. https://www.anthropic.com/

3. City of Chicago. (2023, March 29). Transportation network providers - trips (2018 - 2022): City of Chicago: Data Portal. Chicago Data Portal. https://data.cityofchicago.org/Transportation/Transportation-Network-Providers-Trips-2018-2022-/m6dm-c72p/about_data

4. City of Chicago. (2024, February 7). Taxi trips (2013-2023): City of chicago: Data Portal. Chicago Data Portal. https://data.cityofchicago.org/
Transportation/Taxi-Trips-2013-2023-/wrvz-psew/about_data

5. National Oceanic and Atmospheric Administration. (n.d.). Integrated Surface Dataset (Global) (Version Superseded). National Centers for Environmental Information (NCEI). https://www.ncei.noaa.gov/access/search/data-search/global-hourly

6. OpenAI. (n.d.). ChatGPT. OpenAI. https://openai.com/

7. Soltanieh Ha, M. (2025). BA843 E1 Big Data Analytics for Business (Fall 25). Lectures 1-13. Boston; Boston University: Questrom School of Business.
