# Project_PriciplesOfDataScience
Individual portfoloi project of Principles of Data Science Modules in M.Sc in Data Science

## Project Overview
This project applies a complete data science lifecycle to predict Indian domestic flight prices using machine learning. The dataset contains 300,261 flight records across 8 airlines, covering both economy and business class routes. The project was developed using Microsoft Azure cloud services and follows industry best practices for data engineering, exploratory analysis, and model deployment.

## Business Problem
Flight ticket prices change often because of factors like demand, seasonality, competition, fuel costs, and booking patterns. This unpredictability makes it challenging for travellers to know the right time to book otherwise it make travellers to pay more than necessary. Online travel agencies, price comparison sites, and corporate travel planners find it difficult to provide accurate guidance or manage travel budgets effectively. A flight price prediction model helps to reduce this uncertainty by forecasting future prices, so users make better booking decisions.

## Dataset
| Property | Details |
|---|---|
| Source | Kaggle — Indian Domestic Flights Dataset |
| Files | business.csv, economy.csv |
| Total Records | 300,261 |
| Features | 11 original + engineered features |
| Airlines | Air India, Vistara, IndiGo, SpiceJet, AirAsia, GO FIRST, TruJet, StarAir |
| Storage | Microsoft Azure Blob Storage |

## Project Structure
```
Project_PrinciplesOfDataScience/
├── notebooks/
│   ├── 1_etl.ipynb                  # Data cleaning and preprocessing
│   ├── 2_eda.ipynb                  # Exploratory data analysis
│   ├── 3_feature_engineering.ipynb  # Feature creation and encoding
│   ├── 4_clustering.ipynb           # K-Means clustering analysis
│   └── 5_model.ipynb                # Model training and evaluation
├── reports/
│   ├── price_distribution.png
│   ├── price_by_weekday.png
│   ├── price_by_stops_class.png
│   ├── price_by_departure_hour.png
│   ├── correlation_heatmap.png
│   └── airline_prices.png
├── data/
│   ├── raw_data/  
|       ├── business.csv              # Raw CSV files (stored in Azure Blob)   
|       ├── economy.csv              
│   └── processed_data/  
|       ├── flights_clean.csv         # Cleaned data (stored in Azure Blob)
|       ├── flights_model_ready.csv   # Training ready data (stored in Azure Blob)
├── .gitignore
└── README.md
```
