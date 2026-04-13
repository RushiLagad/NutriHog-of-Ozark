# NutriMap - NutriHog of Ozark

NAFSI x NourishNet Student Data Challenge 2026 | Track 2: NourishNet
University of Arkansas, Fayetteville

## Team
- Dayoung In (dain@ucsd.edu) - UC San Diego
- Dikshya Pathak (dpathak@uark.edu) - University of Arkansas
- Rushikesh Lagad (rlagad@uark.edu) - University of Arkansas

## Overview
NutriMap is a county-level food vulnerability intelligence system covering 3,221 US counties. It integrates Census ACS 2021, CDC PLACES 2023, and USDA geospatial data to construct a validated NutriVulnerability Index (NVI), train three ML classifiers, perform spatial hotspot clustering, apply a greedy intervention optimizer, and deliver an interactive Folium dashboard.

## Key Results
- Counties analyzed: 3,221
- NVI Cronbach alpha: 0.928 (PASS)
- Best AUROC: 0.9349 (Logistic Regression) [95% CI: 0.926-0.943]
- AUPRC: 0.8846
- DBSCAN clusters: 80 (silhouette = 0.481)
- Optimizer: +6.5 SD above 1,000 random placements (100th percentile)
- Priority sites selected: 15

## Files
- NutriHog_Of_Ozarks.ipynb - Main pipeline notebook (run Kernel > Restart and Run All)
- NutriHog_FinalReport.pdf - Final submission report
- NutriMap_dashboard.html - Interactive Folium map (open in any browser)
- requirements.txt - Python dependencies
- figures/ - All generated figures (6 PNGs)

## Quickstart
pip install -r requirements.txt
jupyter notebook NutriHog_Of_Ozarks.ipynb

## Data Sources (all open-access federal data)
- US Census ACS 2021 - poverty, income, unemployment, demographics
- CDC PLACES 2023 - obesity and diabetes prevalence
- USDA TIGER 2021 - county geographic centroids
- USDA Food Environment Atlas - food access indicators
- Feeding America Map the Meal Gap - food insecurity rates

## ML Results
- Logistic Regression: AUROC 0.9349 BEST
- Random Forest: AUROC 0.9310
- XGBoost: AUROC 0.9203

## NVI Components
- Poverty rate 30 percent
- Unemployment rate 20 percent
- SNAP participation rate 15 percent
- Percent population under 18 - 15 percent
- Food insecurity rate 10 percent
- Median household income 10 percent

## License
MIT License - Copyright 2026 NutriHog of Ozark - Dayoung In, Dikshya Pathak, Rushikesh Lagad
