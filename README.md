# global-emission-dashboard
Interactive CO₂ emissions dashboard using Python and Power BI to visualize global fossil fuel trends (2002–2022)
A PDF copy of the Power BI dashboard showcasing the final visual layout and insights is included for quick reference.

## 🚀 Motivation

The project was built to explore global CO₂ emissions over the past two decades and understand the impact of fuel types, geography, and population growth on climate change. It also demonstrates Power BI and DAX capabilities for insightful environmental data storytelling.

## 📁 Data Sources

- **CO₂ Emissions Dataset**:  
  [Kaggle – Global Fossil CO₂ Emissions by Country (2002–2022)](https://www.kaggle.com/datasets/thedevastator/global-fossil-co2-emissions-by-country-2002-2022)

- **Population Dataset** (for per capita calculations):  
  [DataHub – Core Population Dataset](https://datahub.io/core/population)

> 🧪 Python preprocessing code is available in `Code.ipynb`, which merges emissions and population data before importing into Power BI.


## 🧠 DAX Highlights

Some of the custom DAX measures created include:

- `TopCoalEmitter` – returns the country with the highest coal emissions (2002–2021)
- `TopOilEmitter`, `TopGasEmitter`, `TopCementEmitter`, `TopOilEmitter`

These were used to power the KPI cards and highlight top contributors by fuel type.

## 💡 Power BI Skills Showcased

- Custom themes and formatting
- Multi-chart dashboards (bar, line, area, map)
- Dynamic filtering using slicers
- DAX measures for business logic
- KPI cards and conditional visual filtering
