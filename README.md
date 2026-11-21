# World Development Indicators (WDI): Descriptive Statistical Analysis

## Project Overview

This project presents a descriptive statistical analysis of major macroeconomic indicators across six selected economies using the World Bank's World Development Indicators (WDI) dataset.

The analysis covers **2000–2023** and examines economic performance, macroeconomic trends, distributions, variation, and relationships between key economic variables.

The objective is to compare the macroeconomic profiles of India, China, the United States, Brazil, Germany, and South Africa through statistical summaries and interactive visualizations.

**Scope:** This is an exploratory and descriptive analysis. It does not perform Principal Component Analysis (PCA), regression, hypothesis testing, or causal inference.

## Countries Covered

| Country | ISO3 Code |
|---|---|
| India | IND |
| China | CHN |
| United States | USA |
| Brazil | BRA |
| Germany | DEU |
| South Africa | ZAF |

**Analysis period:** 2000–2023

## Macroeconomic Indicators

The notebook examines the following 12 indicators:

| No. | Indicator | WDI Indicator Code |
|---:|---|---|
| 1 | GDP Growth | `NY.GDP.MKTP.KD.ZG` |
| 2 | Inflation | `FP.CPI.TOTL.ZG` |
| 3 | Unemployment | `SL.UEM.TOTL.ZS` |
| 4 | GDP per Capita | `NY.GDP.PCAP.CD` |
| 5 | Trade (% of GDP) | `NE.TRD.GNFS.ZS` |
| 6 | FDI Net Inflows (% of GDP) | `BX.KLT.DINV.WD.GD.ZS` |
| 7 | Government Consumption (% of GDP) | `NE.CON.GOVT.ZS` |
| 8 | Exports (% of GDP) | `NE.EXP.GNFS.ZS` |
| 9 | Imports (% of GDP) | `NE.IMP.GNFS.ZS` |
| 10 | Gross Capital Formation (% of GDP) | `NE.GDI.TOTL.ZS` |
| 11 | Gross Domestic Savings (% of GDP) | `NY.GDS.TOTL.ZS` |
| 12 | Domestic Credit to Private Sector (% of GDP) | `FS.AST.PRVT.GD.ZS` |

## Technologies and Libraries

- **Python** — core programming language
- **Pandas** — data manipulation and analysis
- **NumPy** — numerical computations
- **Plotly Express and Graph Objects** — interactive visualizations
- **SciPy** — statistical calculations
- **OpenPyXL** — Excel workbook export
- **Jupyter Notebook** — analytical environment

## Analysis Workflow

### 1. Data Loading and Configuration

- Load the World Bank WDI CSV dataset.
- Configure countries, indicators, and the analysis period.
- Identify available country and indicator codes.
- Validate required dataset columns.

The main input file is the World Bank `WDICSV` dataset. `WDICountry` and `WDISeries` files are optional and provide supporting metadata.

### 2. Data Preparation

- Filter the dataset for the selected countries and indicators.
- Reshape the data into a country-year panel.
- Convert observations to numeric values.
- Organize the data for comparative analysis.

### 3. Data Quality and Coverage

- Calculate observed and missing values.
- Examine indicator-level data coverage.
- Compare data availability across countries.
- Identify indicators with limited observations.

**Missing values are retained as missing in the primary analysis.** The notebook does not silently interpolate or impute observations.

### 4. Descriptive Statistics

For each indicator, the notebook calculates:

- Number of observations (N)
- Mean and median
- Standard deviation and variance
- Minimum and maximum
- First quartile (Q1) and third quartile (Q3)
- Range and interquartile range (IQR)
- Coefficient of variation (CV)
- Skewness
- Excess kurtosis

### 5. Country-Level Comparison

The analysis compares country-level means, medians, standard deviations, observation counts, indicator coverage, and latest available observations.

### 6. Interactive Visualizations

The notebook generates 15 descriptive visualizations:

1. Indicator data coverage bar chart
2. Country-indicator coverage heatmap
3. GDP growth trends over time
4. Inflation trends over time
5. Unemployment trends over time
6. GDP per capita index (first observed year = 100)
7. GDP growth distribution using violin plots
8. Inflation distribution using histograms and violin plots
9. Relative dispersion across indicators using standardized box plots
10. Pearson correlation heatmap
11. GDP growth versus gross capital formation
12. Trade openness versus GDP growth
13. FDI net inflows distribution by country
14. Latest available country profile using standardized values
15. Country-by-year GDP growth heatmap

### 7. Automated Descriptive Interpretation

The notebook generates data-led descriptive statements about:

- Indicators with the highest and lowest data coverage
- Indicators with the largest raw standard deviation
- Highest defined coefficient of variation
- Countries with the highest and lowest average GDP growth
- The most asymmetric indicator distribution
- Strongest pairwise Pearson correlations, including pairwise sample sizes

These statements describe observed patterns and associations; they do not establish causality.

### 8. Exporting Results

The notebook exports analytical tables to an Excel workbook named:

`WDI_Descriptive_Statistics_Tables.xlsx`

The workbook contains five sheets:

1. `Overall Descriptives`
2. `Coverage`
3. `Country Statistics`
4. `Country Coverage`
5. `Latest Values`

## Repository Structure

A suggested repository layout is:

```text
WDI-Descriptive-Analysis/
├── WDI_Detailed_Descriptive_Analysis.ipynb
├── README.md
├── WDI_CSV/
│   ├── WDICSV.csv
│   ├── WDICountry.csv        # optional
│   └── WDISeries.csv         # optional
└── WDI_Descriptive_Statistics_Tables.xlsx  # generated output
```

The notebook requires the main `WDICSV` dataset. The metadata files are optional. The Excel workbook is generated when the export cell runs.

## Installation and Execution

### Prerequisites

- Python 3.10 or later
- Jupyter Notebook or JupyterLab
- World Bank WDI downloaded dataset

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

Replace the URL and repository name with your own GitHub details.

### 2. Install dependencies

```bash
pip install pandas numpy plotly scipy openpyxl jupyter
```

The notebook also includes a cell that installs `plotly`, `scipy`, and `openpyxl`.

### 3. Download the WDI dataset

Download the World Development Indicators dataset from the [World Bank DataBank](https://databank.worldbank.org/source/world-development-indicators) and extract the files.

### 4. Configure the data folder

Open the notebook and update `DATA_FOLDER` in the configuration cell to the directory containing the WDI files:

```python
DATA_FOLDER = r"path/to/your/WDI_CSV"
```

For example, on Windows:

```python
DATA_FOLDER = r"C:\Users\YourName\Downloads\WDI_CSV"
```

Use a path on your own computer; the example path is not portable.

### 5. Run the notebook

```bash
jupyter notebook
```

Open `WDI_Detailed_Descriptive_Analysis.ipynb` and execute the cells in order. The notebook produces descriptive tables, interactive charts, automated interpretations, and the Excel output workbook.

## Methodological Considerations and Limitations

1. **Descriptive analysis only:** Trends, differences, and correlations do not establish causal relationships.
2. **Unequal data coverage:** Indicators and countries can have different numbers of available observations. Interpret results alongside sample sizes and coverage.
3. **No silent imputation:** The main analysis uses observed values and leaves missing observations missing.
4. **GDP per capita:** The selected series is in current US dollars and is affected by inflation and exchange-rate movements. It is not a constant-price measure of real income.
5. **Mixed units:** GDP per capita is in US dollars, while most other indicators are percentages. Raw standard deviations across different units are not directly comparable.
6. **Correlation:** Pearson correlation measures linear association, can be affected by outliers, and does not imply causation.
7. **Country sample:** The six selected economies are a focused comparative case study, not a representative sample of all countries.
8. **WDI revisions:** Results may change when the World Bank revises historical observations.

## Data Source

**World Bank — World Development Indicators (WDI)**

- [World Development Indicators dataset](https://databank.worldbank.org/source/world-development-indicators)
- [WDI documentation](https://datatopics.worldbank.org/world-development-indicators/)

---

**Project type:** Exploratory Data Analysis (EDA) · Descriptive Statistics · Comparative Macroeconomic Analysis  
**Language:** Python  
**Environment:** Jupyter Notebook
