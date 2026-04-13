# Global CO₂ Emissions Tracker Dashboard

**Data Analytics & Visualisation Project**  
**Gautami Thakur | University of Galway, 2025**

An end-to-end data project tracking global fossil fuel CO₂ emissions from 2002–2021 — from raw data to an interactive Power BI dashboard. Built to explore how fuel type, geography, and population growth shape the global emissions picture over two decades.

---

## Overview

This project combines Python-based data engineering with Power BI visualisation to produce a clean, interactive dashboard for exploring CO₂ emissions trends worldwide. The pipeline covers data cleaning, ISO country code mapping, population join for per-capita calculations, and a multi-page Power BI report with DAX-powered KPIs and dynamic filtering.

---

## Repository Structure

```
├── Code.ipynb                          # Full Python preprocessing pipeline
├── GCB2022v27_MtCO2_flat.csv          # Raw emissions dataset (Global Carbon Budget 2022)
├── population.csv                      # Population data for per-capita calculations
├── emissions_with_population.csv       # Final cleaned & merged dataset (Power BI input)
├── Emissions Dashboard 1.pbix          # Power BI dashboard file
└── Copy of Dashboard.pdf               # PDF export of the final dashboard
```

---

## Data Sources

| Dataset | Source |
|---|---|
| Global Fossil CO₂ Emissions by Country (2002–2022) | [Kaggle – Global Fossil CO₂ Emissions](https://www.kaggle.com/datasets/thedevastator/global-fossil-co2-emissions-by-country-2002-2022) |
| World Population Data | [DataHub – Core Population Dataset](https://datahub.io/core/population) |

The raw emissions dataset covers 200+ countries across fuel types: **Coal, Oil, Gas, Cement, Flaring**, and Total. The population dataset was joined to enable per-capita emissions analysis.

---

## Python Preprocessing Pipeline (`Code.ipynb`)

The notebook handles the full data engineering workflow before Power BI import:

### 1. Exploratory Data Analysis
- Shape, schema, and data type inspection
- Missing value audit across all columns
- Year range validation (1750–2022 raw → filtered to 2002–2021)
- Summary statistics for all emission columns
- Country-level trend sampling (e.g. India total emissions over time)

### 2. Data Cleaning
- Filtered to 2002–2021 (20-year analysis window)
- Removed aggregated rows (`International Transport`)
- Dropped redundant columns (`Other`, `Per Capita` — recalculated cleanly)
- Dropped rows with missing `Total` emissions

### 3. ISO Country Code Mapping
- Merged with Plotly's ISO country code reference to add `ISO 3166-1 alpha-3` codes
- Enabled accurate choropleth map rendering in Power BI

### 4. Population Join & Per-Capita Calculation
- Merged population data by `Country` + `Year`
- Computed `Emissions_per_capita = Total / Population`
- Exported final dataset as `emissions_with_population.csv`

---

## Power BI Dashboard

The `.pbix` file and PDF export contain a multi-visual interactive dashboard covering:

- **Global emissions trend** (2002–2021) — line and area charts
- **Emissions by fuel type** — Coal, Oil, Gas, Cement, Flaring breakdowns
- **Country-level choropleth map** — powered by ISO codes
- **Top emitters by fuel type** — bar charts with dynamic ranking
- **Per-capita emissions** — normalised view accounting for population size
- **KPI cards** — top emitters per fuel type, powered by DAX measures
- **Slicers** — filter by country, year range, and fuel type

### DAX Highlights

Custom measures created to power the KPI cards:

| Measure | Description |
|---|---|
| `TopCoalEmitter` | Country with highest cumulative coal emissions |
| `TopOilEmitter` | Country with highest cumulative oil emissions |
| `TopGasEmitter` | Country with highest cumulative gas emissions |
| `TopCementEmitter` | Country with highest cumulative cement emissions |

---

## Key Insights

- Coal remains the dominant emissions source globally, concentrated heavily in Asia
- Per-capita emissions tell a very different story from absolute totals — smaller nations often rank disproportionately high
- Gas and cement emissions have grown steadily while flaring trends vary by region
- The 2008 financial crisis and COVID-19 (2020) are visible as dips in global totals

---

## Tech Stack

- **Python** — Pandas for data cleaning, merging, and feature engineering
- **Power BI** — Dashboard design, DAX measures, interactive visualisation
- **DAX** — Custom KPI measures and aggregations
- **Jupyter Notebook** — Reproducible preprocessing pipeline

---

## How to Run

1. Clone this repository
2. Open `Code.ipynb` and run all cells to regenerate `emissions_with_population.csv`
3. Open `Emissions Dashboard 1.pbix` in Power BI Desktop
4. Refresh the data source to point to your local `emissions_with_population.csv`
5. Explore the dashboard — or view the static `Copy of Dashboard.pdf` for a quick preview
