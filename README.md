# 🌎 Urban Mobility & Economic Productivity Analysis — Latin America (2024)

## 🎯 Project Objective

Evaluate how **urban mobility relates to economic productivity** in major Latin American cities using real data from **TomTom Traffic Index** and **OECD Cities**. The goal is to identify which cities would benefit most from investment in transportation infrastructure.

---

## 📂 Datasets Used

| File | Description |
|---|---|
| `tomtom_traffic.csv` | Real-time and historical traffic data by city (congestion, travel times, jam counts) |
| `oecd_city_economy.csv` | Economic indicators by city (GDP per capita, unemployment, population, PM2.5) |

---

## 🧩 Analysis Stages

1. **Load and explore** — Load both datasets, inspect structure, data types, and first rows.
2. **Clean and prepare data** — Fix date formats, correct numeric separators, standardize column names to `snake_case`, and handle type conversions.
3. **Extract year and filter** — Extract year from timestamps and filter records for 2024 only using `.copy()` to preserve originals.
4. **Aggregate mobility data** — Group traffic data by `city`, `country`, and `year`, computing averages for key metrics (jams delay, travel times, jam count).
5. **Merge datasets** — Inner join traffic and economic data on `city` and `year` to retain only cities present in both sources.
6. **Visualize relationships** — Boxplot for traffic distribution, histogram for GDP per capita, and comparative bar chart.
7. **Export and document** — Export the final clean dataset and write an executive summary with findings and recommendations.

---

## ▶️ How to Run the Notebook

### Option A — Google Colab (recommended)

1. Open [Google Colab](https://colab.research.google.com/)
2. Go to **File → Upload notebook** and upload `S5_ladb_mobility_economy_project_student.ipynb`
3. Upload the CSV files to `/datasets/` via **File → Upload to session storage**
4. Run all cells with `Runtime → Run all`

### Option B — Local Jupyter Notebook

```bash
# 1. Clone the repository
git clone https://github.com/your-username/your-repo.git
cd your-repo

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn

# 3. Open the notebook
jupyter notebook S5_ladb_mobility_economy_project_student.ipynb
```

---

## 🔁 Reproduction Guide

1. Place both CSV files in the `/datasets/` directory
2. Run cells **in sequential order** — each step depends on the previous one
3. Key DataFrames built throughout the notebook:

| Variable | Content |
|---|---|
| `traffic` | Raw traffic data (1M+ rows) |
| `eco` | Economic indicators per city |
| `traffic_2024` | Traffic data filtered to year 2024 |
| `eco_2024` | Economic data filtered to year 2024 |
| `traffic_city_year_2024` | Average traffic metrics aggregated by city and year |
| `merged` | Final dataset — inner join of traffic + economy |

4. The final clean dataset is exported as `ladb_mobility_economy_2024_clean.csv`

---

## 🛠️ Required Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 🔍 Key Findings

- **No clear linear relationship** was found between GDP per capita and congestion levels across Latin American cities.
- **Bogotá** stands out as a priority city — high congestion combined with a lower GDP per capita compared to peers like Buenos Aires.
- Cities like **Mexico City** and **São Paulo** show the highest jam delays but vary significantly in economic output.
- High variability in traffic indicators exists even among cities within similar GDP ranges.

---

## 📊 Cities Covered (2024)

**15 cities across 7 countries:**
Argentina, Brazil, Chile, Colombia, Mexico, Peru, Uruguay

Buenos Aires, Belo Horizonte, Bogotá, Brasília, Curitiba, Fortaleza, Lima, Mexico City, Montevideo, Porto Alegre, Recife, Rio de Janeiro, Salvador, Santiago, São Paulo

---

## 📌 Notes

- Column `pm25_ug_m3` remains as `object` type in the raw data due to comma-as-decimal formatting — handle this before using it in numerical analysis.
- The inner join excludes cities not present in both datasets, ensuring data consistency.
- Outlier cities (e.g., Mexico City, Tokyo, New York) may skew global averages — consider filtering by region for regional analysis.

---

*Project developed as part of Sprint 5 — Data Analysis*
