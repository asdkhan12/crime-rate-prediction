# crime-rate-prediction

_Data Science Lifecycle project to forecast monthly crime rates in Washington, DC._

---

## Table of Contents

1. [Overview](#overview)  
2. [Repository Structure](#repository-structure)  
3. [Prerequisites](#prerequisites)  
4. [Data Pipeline Setup](#data-pipeline-setup)  
5. [Running the Notebook](#running-the-notebook)  
6. [Expected Outputs](#expected-outputs)  
7. [Contact & Contributions](#contact--contributions)  

---

## Overview

This repository contains a fully reproducible data pipeline and analysis notebook that:

1. Combines five years (2021–2025) of DC crime-incident CSVs  
2. Cleans and aggregates incidents by census tract and month  
3. Merges in tract shapefiles and population data  
4. Performs exploratory analysis, clustering, and baseline modeling  
5. Generates maps and visualizations for Sprint 3 deliverables  

Anyone can follow these steps to reproduce the entire workflow and extend it to new data.

---

## Repository Structure


```bash
crime-rate-prediction/
├── data/
│   ├── raw/                   # Zip archive and raw CSVs
│   │   └── CrimeDB.zip        # All crime-incident CSVs (2021–2025)
│   ├── shapefiles/            # Census-tract shapefile components
│   │   ├── tl_2022_11_tract.shp
│   │   ├── tl_2022_11_tract.dbf
│   │   ├── tl_2022_11_tract.shx
│   │   └── …
│   └── processed/             # Pipeline outputs
│       ├── dc_crime_master.csv
│       ├── dc_crime_clean.csv
│       └── dc_total_population.csv
├── notebooks/
│   └── Data_Science_Lifecycle_Project_Pipeline.ipynb
├── environment.yml            # Conda environment spec
├── requirements.txt           # pip dependencies
├── README.md                  # This file
└── LICENSE
```
## Prerequisites

- **Git** (to clone this repo)  
- **Python 3.8+**  
- **Conda** (recommended) or a virtual environment  
- Optionally, **Jupyter Lab** or **Notebook**

---

## Data Pipeline Setup

1. **Clone the repository**  
   ```bash
   git clone https://github.com/<your-username>/crime-rate-prediction.git
   cd crime-rate-prediction

2. **Create the environment**  
   Using Conda (preferred):  
   ```bash
   conda env create -f environment.yml
   conda activate crime-rate-pred

3. **Unzip the raw data**
   ```bash
   unzip data/raw/CrimeDB.zip -d data/raw/
   ```
  You should now have: 
   ```bash
data/raw/Crime_Incidents_in_2021.csv
data/raw/Crime_Incidents_in_2022.csv
data/raw/Crime_Incidents_in_2023.csv
data/raw/Crime_Incidents_in_2024.csv
data/raw/Crime_Incidents_in_2025.csv
```
4. **Place supporting files**

Copy all shapefile components (.shp, .dbf, .shx, etc.) into data/shapefiles/.

Ensure data/processed/dc_total_population.csv (ACS B01003 total population) is present.

Add any additional SES CSVs (e.g. median income S1903, poverty rate S1701) into data/processed/.

5. **Launch Jupyter Lab**
```bash
jupyter lab
```
6. **Execute cells in order** 
Section 1: Data ingestion and concatenation

Section 2: Cleaning, filtering, de-duplicating, and aggregating by tract/month

Section 3: Merge population CSV and shapefiles

Section 4: Exploratory analysis (offense counts, seasonal trends, boxplots)

Section 5: K-Means clustering of monthly crime patterns

Section 6: Baseline modeling (Linear Regression, Random Forest, Gradient Boosting; MAE, RMSE, R²)

Section 7: Spatial autocorrelation (Moran’s I, LISA)
