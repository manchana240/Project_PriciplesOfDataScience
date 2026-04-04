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

## Approach

### 1. Data Collection
- Source: Kaggle Indian Domestic Flights dataset
- Stored securely in Azure Blob Storage container

### 2. Data Preprocessing (ETL)
- Add class column to both raw data files and merged economy and business class datasets
- Cleaned price column (removed comma formatting)
- Parsed flight duration from string to numeric minutes
- Cleaned stop column (removed embedded whitespace)
- Extracted departure and arrival hours from time strings
- Derived day of week, month, and weekend indicator

### 3. Exploratory Data Analysis
- Price distribution by airline and class
- Correlation heatmap across numeric features
- Boxplot analysis by number of stops per class
- Average price by departure hour
- Average price by day of week
- Date range verification

### 4. Feature Engineering
- Created time of day buckets (morning/afternoon/evening/night)
- Mapped stop categories to numeric values (0/1/2)
- Applied one-hot encoding to categorical columns
- Dropped irrelevant identifier columns

### 5. Clustering Analysis
- Applied K-Means clustering
- Used Elbow Method to identify optimal k=4
- Standardised features using StandardScaler
- Identified four clusters are : Budget, Standard Economy, Long Haul Economy, Premium

### 6. Predictive Modelling
- Algorithm: Random Forest Regressor
- Train/Test Split: 80% / 20%
- Hyperparameters: n_estimators=100, max_depth=20

## Results

### Clustering — 4 Price Segments Identified
| Cluster | Label | 
|---|---|
| 3 | Budget Short-Haul | 
| 0 | Standard Economy | 
| 2 | Long-Haul Economy | 
| 1 | Business Premium | 

### Model Performance — Random Forest Regressor
| Metric | Value | Interpretation |
|---|---|---|
| R² | 0.973 | Model explains 97.3% of price variance |
| RMSE | 3,714 INR | Average prediction error |
| MAE | 2,326 INR | Typical everyday prediction error |

## Business Impact
- The model enables stakeholders to predict flight prices within ± 2,326 INR on average, helping to make informed booking decisions. 
- Airlines can use cluster insights for targeted pricing strategies across four identified market segments.
- Travel agencies can integrate the Azure ML endpoint to automate fair price alerts for customers.
- 
## Recommendations 
1.	Expand the Dataset for a Longer Time Range     
The current dataset covers approximately one month of flight data, which limits the model’s ability to understand seasonal price changes such as holiday peaks, festival periods, or Climatic season fluctuations in India. Using at least a full year of historical flight data in future versions would allow the model to better learn these seasonal trends and deliver more accurate price predictions throughout the year.
2.	Introduce Booking Lead Time into the Model    
How far in advance the ticket is purchased plays an important role in flight pricing. However, the current dataset is missing booking dates, so it cannot capture the time gap between booking date and travel date It is recommended to capture the booking date feature in future data collection, as the fares of flights booked weeks prior usually differ significantly from last-minute bookings price.
3. Include Seat Availability as a Feature    
Airlines continuously change ticket prices based on how many seats are still available. As more seats get sold (demand increases) then availability(supply) goes down, normally prices go up. This seat availability feature is missing from the current dataset. If included it will improve the model’s accuracy definitely. Accessing airline APIs or using real time data collection methods could help capture seat availability along with price data.
4.	Deploy Model as a Real-Time Azure ML Endpoint    
Currently, the trained Random Forest model is stored as a .pkl file in Azure Blob Storage. The next step is to deploy it as a real-time inference endpoint using Azure ML managed online endpoints. This will make the model available as a REST API, so travel agencies, booking sites, and airline systems can get price predictions quickly and programmatically.
5.	Implement Automated Data Pipeline    
Right now, collecting data, cleaning, and model training is happening manually using Jupyter notebooks. Automating this process with Azure Data Factory for scheduled data ingestion and Azure ML Pipelines for model retraining would help keep the model up to date with changing pricing patterns and remove the need for manual work. 
7.	Design a Dashboard for End Users    
To get the most out of this model, it would help to create a web-based dashboard where travelers and travel agents can enter flight details and get instant price predictions. This dashboard could use Power BI connected to the Azure ML endpoint or be a custom web app hosted on Azure App Service. 

