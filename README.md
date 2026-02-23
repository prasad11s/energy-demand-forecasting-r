# July Energy Demand Forecasting — eSC Energy

Predicting residential building hourly energy consumption (kWh) for July using machine learning models built in R. Built for eSC, a South Carolina residential electricity provider, to help manage peak demand under climate warming scenarios without infrastructure expansion.

**[Live Demo — Shiny App](https://prasadshimpi.shinyapps.io/eSc_july_pred/)**  
**[Project Report](https://github.com/prasad11s/IDS_Project/blob/main/Final_Energy_Usage_Report_With_Graphs.pdf)**

---

## Problem Statement

eSC faces increasing stress on energy infrastructure during July due to climate change driven temperature increases. Rather than building a new power plant, this project uses data science to quantify future demand risks and recommend cost-effective interventions.

---

## Key Results

| Model | RMSE (kWh) | R² Score |
|---|---|---|
| Linear Regression | 0.5825 | 0.290 |
| XGBoost | 0.5034 | 0.470 |
| **Random Forest (Selected)** | **0.4997** | **0.478** |

Random Forest was selected as the final model for deployment due to lowest RMSE, highest R², and built-in variable importance for stakeholder communication.

**Climate Scenario Finding:** A simulated 5°C temperature increase in July is projected to raise peak hourly energy demand by up to 22%, concentrated during 2 PM to 5 PM afternoon hours.

---

## Tech Stack

| Component | Tool |
|---|---|
| Language | R |
| Modeling | Random Forest, XGBoost, Linear Regression |
| Web App | R Shiny |
| Deployment | shinyapps.io |
| Data Processing | dplyr, tidyverse |
| Visualization | ggplot2 |

---

## Dataset

**Source:** eSC Energy (residential electricity provider, South Carolina)
- ~5,000 static house records
- ~8,000 hourly energy usage Parquet files
- ~8,000 county-level weather CSV files
- Filtered to July 2018 only
- Reduced from 270+ columns to ~40 relevant features
- Engineered features: lagged energy consumption, cooling degree hours, weekend indicators, hourly time bins

**Key finding from EDA:** Average daily energy usage was 34.6 kWh per home, with clear afternoon peaks between 2 PM and 5 PM. Temperature and house size were the strongest drivers.

---

## Live Shiny App Features

- **EDA Dashboard** — interactive graphs exploring energy usage patterns
- **Prediction Panel** — enter cooling setpoint, house size, occupants, income, and outside temperature to get predicted daily kWh
- **Sample Data Viewer** — browse the underlying dataset

---

## Project Structure

```
IDS_Project/
│
├── eSc_july_pred/                         # Shiny app files
├── 0.1_Understanding_data.Rmd             # Initial data exploration
├── 01_generate_function.R                 # Data generation functions
├── 02_prepare_building_map.R              # Building ID to county mapping
├── 03_batch_process_buildings.R           # Batch processing pipeline
├── 04_combine_all_outputs.R               # Combine processed outputs
├── 05_EDA.R                               # Exploratory data analysis
├── 07_modelling.R                         # Model training and evaluation
├── 7.1_final model_RF.R                   # Final Random Forest model
├── 09_5_degree warmer.R                   # +5°C climate scenario simulation
├── 10_1 degree coolsetpoint.R             # Setpoint adjustment simulation
├── final_rf_model.rds                     # Saved Random Forest model
├── final_combined_dataset.rds             # Processed dataset
├── building_id_county_map.csv             # Building to county mapping
└── Final_Energy_Usage_Report_With_Graphs.pdf  # Full project report
```

---

## How to Run Locally

```r
install.packages(c("shiny", "randomForest", "dplyr", "ggplot2", "DT", "xgboost"))

# Clone the repo, open eSc_july_pred/app.R in RStudio and click Run App
```

---

## Author

**Prasad Shimpi**  
MS Applied Data Science, Syracuse University  
[LinkedIn](https://linkedin.com/in/prasadshimpi) | [GitHub](https://github.com/prasad11s)
