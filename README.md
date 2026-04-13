# NutriMap: Food Vulnerability Dashboard

**NAFSI - NourishNet Student Data Challenge 2026 | Track 2: NourishNet**  
**Team: NutriHog of Ozark | University of Arkansas, Fayetteville**

---

## 🔴 Live Dashboard
👉 **https://rushilagad.github.io/NutriHog-of-Ozark/**

---

## Team
| Name | Institution | Email |
|---|---|---|
| Rushikesh Lagad | University of Arkansas | rlagad@uark.edu |
| Dikshya Pathak | University of Arkansas | dpathak@uark.edu |
| Dayoung In | UC San Diego | dain@ucsd.edu |

---

## Overview

NutriMap is a county-level food vulnerability intelligence system covering 3,221 US counties. It integrates Census ACS 2021, CDC PLACES 2023, and USDA geospatial data to:

- Construct a validated **NutriVulnerability Index (NVI)**
- Train three cross-validated **ML classifiers**
- Perform **spatial hotspot clustering** (DBSCAN)
- Apply a **greedy intervention optimizer**
- Deliver an interactive **React dashboard** for families, donors, and volunteers

---

## Key Results

| Metric | Value |
|---|---|
| Counties analyzed | 3,221 |
| NVI Cronbach alpha | 0.928 ✅ |
| Best AUROC (Logistic Regression) | 0.9349 [95% CI: 0.926–0.943] |
| AUPRC | 0.8846 |
| DBSCAN clusters | 80 (silhouette = 0.481) |
| Optimizer advantage | +6.48 SD above 1,000 random placements (100th percentile) |
| Priority intervention sites | 15 |

---

## Repository Structure

```
NutriHog-of-Ozark/
├── index.html                  # React app entry point (CDN React 18 + Leaflet)
├── app.js                      # Full React application (JSX, compiled in-browser)
├── data.js                     # 55 DC/MD/VA counties + 24 real organizations
├── styles.css                  # Dark green theme, responsive layout
├── .nojekyll                   # GitHub Pages bypass
├── NutriHog_Of_Ozarks.ipynb    # Full ML pipeline notebook
├── NutriHog_Final_Report.pdf   # Final submission report (12 pages)
├── NutriMap_dashboard.html     # Folium interactive map (analytical backend)
├── PROMPTS.md                  # Kiro prompt engineering log
├── requirements.txt            # Python dependencies
└── figures/                    # Generated pipeline figures (6 PNGs)
```

---

## React Dashboard — Quickstart

No installation required. Open directly in any browser:

```
# Option 1 — Open index.html directly in Chrome/Firefox
# Option 2 — Local server
python -m http.server 8080
# then visit http://localhost:8080
```

**Stack:** React 18 (CDN) · Leaflet 1.9 · Babel Standalone · CartoDB Dark Matter tiles  
No npm, no build step, no server needed.

---

## Jupyter Notebook — Quickstart

```bash
# Step 1 — Install dependencies
pip install -r requirements.txt

# Step 2 — Launch
jupyter notebook

# Step 3 — Open and run
# NutriHog_Of_Ozarks.ipynb → Kernel → Restart & Run All
```

The notebook auto-downloads all data from public federal APIs on first run. A synthetic fallback dataset is used automatically if APIs are unavailable.

**APIs used:**
- US Census ACS 2021: https://api.census.gov/data/2021/acs/acs5
- CDC PLACES 2023: https://data.cdc.gov/resource/swc5-untb.csv
- USDA TIGER 2021: https://www2.census.gov/geo/docs/maps-data/data/gazetteer/2021_Gazetteer/

---

## Data Sources

| Source | Variables | Coverage |
|---|---|---|
| Census ACS 2021 (5-yr) | Poverty, income, unemployment, % under 18, vehicle access | 3,221 counties |
| CDC PLACES 2023 | Obesity, diabetes prevalence | County-level |
| USDA TIGER 2021 | County geographic centroids (lat/lon) | National |
| USDA Food Environment Atlas | Food access indicators | County-level |
| Feeding America – Map the Meal Gap | Food insecurity rates, meal gap estimates | County-level |
| Capital Area Food Bank | Distribution partners, priority areas | MD/DC/VA |
| Maryland Food Bank | County hunger & distribution data | Maryland |
| EPA Excess Food Opportunities Map | Food recovery organizations | National |
| 211 Maryland / State Open Portals | Community food assistance programs | MD/DC/VA |

---

## ML Results

| Model | AUROC | 95% CI | AUPRC | F1 |
|---|---|---|---|---|
| **Logistic Regression ★** | **0.9349** | 0.926–0.943 | 0.8846 | 0.8425 |
| Random Forest | 0.9310 | 0.922–0.939 | 0.8773 | 0.8423 |
| XGBoost | 0.9203 | 0.910–0.929 | 0.8573 | 0.8306 |

---

## NVI Components

| Feature | Weight | Direction |
|---|---|---|
| Poverty rate | 30% | Higher = worse |
| Unemployment rate | 20% | Higher = worse |
| SNAP participation rate | 15% | Higher = worse |
| % Population under 18 | 15% | Higher = worse |
| Food insecurity rate | 10% | Higher = worse |
| Median household income | 10% | Lower = worse |

---

## Prompt Engineering

The React dashboard was built using **Kiro** (AWS agentic IDE). Full prompt sequence documented in:  
📄 **[PROMPTS.md](./PROMPTS.md)**

---

## License

MIT License — Copyright 2026 NutriHog of Ozark — Dayoung In, Dikshya Pathak, Rushikesh Lagad
