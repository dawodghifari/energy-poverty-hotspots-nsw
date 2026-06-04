# Identifying Energy Poverty Hotspots in NSW

Machine learning analysis identifying NSW suburbs at risk of energy poverty, by modelling the relationship between zone-substation electricity consumption and climate data — suburbs whose actual usage deviates significantly from climate-predicted usage are flagged as at-risk.

## Approach

1. **Data engineering** — ingested six years (2019–2024) of 15-minute zone-substation load data across NSW suburbs, plus Bureau of Meteorology weather-station observations and NSW locality shapefiles; built a missing-data summary per suburb and applied targeted cleaning/imputation before merging climate and power series.
2. **Exploratory analysis** — correlation matrices, rolling-mean usage trends, monthly box plots, and usage histograms.
3. **Modelling** — Random Forest, LightGBM, and XGBoost regressors predict expected consumption from climate features; deviation between predicted and actual usage drives a per-suburb **energy-poverty risk score**.
4. **Outputs** — suburb hotspot probabilities, extreme-demand-day risk probabilities, and feature-importance analysis for policymaker interpretation.

![Evaluation metrics](assets/evaluation_metrics.png)

## Repo contents

| Path | Description |
|---|---|
| `notebooks/energy_poverty_analysis.ipynb` | Full pipeline: load → clean → merge → EDA → models → risk maps |
| `assets/suburb_hotspot_probabilities.csv` | Final per-suburb risk output |
| `assets/extreme_day_risk_probabilities.csv` | Extreme-demand-day risk output |
| `docs/ENGG2112_Project_Report.pdf` | 15-page report |
| `docs/ENGG2112_Final_Presentation.pdf` | Slide deck |

**Data sources (not redistributed):** Ausgrid zone-substation load data, BOM weather observations, NSW locality boundaries (Spatial Services). See the report for details.

## Context

Multi-disciplinary Engineering project (ENGG2112, University of Sydney, 2025 — course mark: 88 HD).

**Team:** Dawod Ghifari (first author — data pipeline, power/climate merging, modelling), Max Legzdin, Imran Fareez Azmy, Phoebe Lee.
