# **Cross Country Solar Farm Analysis**

This project analyzes solar sensor data from multiple West African countries to identify the best regions for solar farm development. It involves cleaning, exploring, and comparing datasets to extract actionable insights. The goal is to support strategic decisions for sustainable solar energy investments. Additionally, it includes building an interactive dashboard to visualize findings clearly.

---

##  Project Structure

```
solar-challenge-week1/
├── .github/
├── app/
│   ├── main.py
│   ├── comparison.py
│   ├── utils.py
│   └── README.md
├── dashboard_screenshot/
├── notebooks/
│   ├── benin_eda.ipynb
│   ├── compare_countries.ipynb
│   ├── sierraleone_eda.ipynb
│   ├── togo_eda.ipynb
│   └── README.md
├── src/
│   ├── comparison_utils.py
│   └── solar_eda.py
├── data/
│   ├── benin_clean.csv
│   ├── sierraleone_clean.csv
│   └── togo_clean.csv
├── tests/
├── .gitignore
├── requirements.txt
└── README.md
```

---

##  Project Objectives

### Main goal  
Here are the Project Objectives in a clear, concise form:

      Profile, clean, and explore solar datasets from Benin, Sierra Leone, and Togo to understand data quality and patterns.

      Compare solar radiation metrics across countries to identify regions with the highest solar potential.

      Use statistical analysis and visualizations to provide actionable insights for solar farm expansion.

      Develop an interactive dashboard to communicate findings effectively and support data-driven decision making.

---

### Initial Setup and Project Structure

- [x] Set up GitHub repository with clear folder structure  
- [x] Define modular code layout (`src/`, `notebooks/`, `data/`, `tests/`)  
- [x] Add `.gitignore` to exclude local artifacts  
- [x] Create and document environment dependencies (`requirements.txt`)  
- [x] Create a shared data cleaning script for reuse across notebooks  

---

### Profiling, Cleaning, and EDA

For each country's dataset:

- [x] Perform summary statistics and null checks  
- [x] Clean via outlier clipping and median imputation  
- [x] Generate cleaned dataset: `data/<country>_clean.csv`  
- [x] Produce exploratory charts for trends and correlation analysis  
- [x] Enable notebook reproducibility and versioned cleaning code  

---

### Cross-Country Comparison

- [x] Load cleaned datasets for Benin, Sierra Leone, and Togo  
- [x] Plot boxplots of GHI, DNI, and DHI across countries  
- [x] Generate a summary statistics table (mean, median, std)  
- [x] Run ANOVA statistical test on GHI values  
- [x] Add 3 key markdown observations about country differences  
- [x] Include a bar chart ranking average GHI by country  

---

### Bonus Task - Streamlit Dashboard

- [x] Build an interactive dashboard using Streamlit  
- [x] Enable multipage layout:  
  - `main.py` → country-specific solar insights  
  - `comparison.py` → cross-country metric analysis  
- [x] Visualize EDA summaries with:  
  - GHI boxplots  
  - Time series plots  
  - Scatter charts  
  - Summary tables  
- [x] Add interactive widgets:  
  - Country selector  
  - Metric dropdown  
- [x] Store code under `app/` folder  
- [x] Document dashboard usage in `app/README.md`  
- [x] Add screenshots in `dashboard_screenshot/`  

---

## 1. Setup environment

```bash
git clone https://github.com/aprilyab/Cross Country Solar Farm Analysis.git
cd Cross Country Solar Farm Analysis
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```


## 3. Open and run a country notebook

| Notebook Type    | Country / Topic     | Path                          | Output CSV                  |
|------------------|--------------------|-------------------------------|-----------------------------|
| Country EDA      | 🇧🇯 Benin          | `notebooks/benin_eda.ipynb`    | `data/benin_clean.csv`       |
| Country EDA      | 🇸🇱 Sierra Leone    | `notebooks/sierraleone_eda.ipynb` | `data/sierraleone_clean.csv` |
| Country EDA      | 🇹🇬 Togo            | `notebooks/togo_eda.ipynb`     | `data/togo_clean.csv`        |
| Cross-Country | Comparison (All)   | `notebooks/compare_countries.ipynb` | —                           |

*Note: CSV outputs are generated locally and are not committed (see `.gitignore`).*

---

##  Launch the Dashboard

Make sure the cleaned CSVs are present in the `data/` directory.

From the project root, run:


      streamlit run app/main.py
```

Use the sidebar to:

- [x] Select a country (Country Insights page)  
- [x] Switch to "Cross-Country Comparison" page  

---

##  Cleaning Pipeline

Implemented in `src/solar_eda.py`:

| Step                       | Description                                  |
|----------------------------|----------------------------------------------|
| Drop fully-null columns     | Removes columns like 'Comments'               |
| Fix negative night-time irradiance | Sets negative GHI/DNI/DHI to 0 at night  |
| Z-score filtering          | Drops rows with sensor Z-score > 3             |
| Median imputation          | Fills missing values in core fields             |
| Feature engineering       | Adds 'Hour', 'Month', and 'HasRain' flags       |



---

##  EDA Highlights

Each notebook contains:

- [x] Summary statistics + null audit  
- [x] Irradiance/temperature time series  
- [x] Diurnal and monthly patterns  
- [x] Outlier and missing-value handling  
- [x] Wind rose and histograms  
- [x] Correlation heatmaps  
- [x] Bubble charts (e.g., GHI vs Tamb)  
- [x]  Cross-country boxplots and summary stats (Task 3)  
- [x]  GHI country ranking bar chart (Task 3)  
- [x]  ANOVA test results for GHI (Task 3)  

---

##  Contribution Summary

| Feature                  | Implemented                                |
|--------------------------|--------------------------------------------|
| Cleaning pipeline        |  `SolarCleaner` in `solar_eda.py`        |
| Country EDA notebooks    |  3 countries + comparison                 |
| Cross-country comparison |  `compare_countries.ipynb` added          |
| Modular code design      |  `utils.py` shared logic                   |
| Statistical tests        |  One-way ANOVA for GHI                     |
| Dashboard + visual summaries |  Interactive Streamlit app with shared utils |
| Git commits & PR hygiene |  Followed Git feature branching           |

