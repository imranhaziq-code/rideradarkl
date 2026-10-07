# 🚆 RideRadar KL

### Smarter Cities Through Smarter Transit Data

RideRadar KL is a public transportation analytics and predictive modeling project focused on the **Klang Valley transit ecosystem in Malaysia**.

The project uses historical public transportation ridership data to analyse demand patterns across major urban transit services, including **LRT, MRT and Monorail**, and applies **XGBoost regression** to predict ridership based on temporal features.

The latest version extends the original analysis into an interactive **Streamlit dashboard**, allowing users to explore overall Klang Valley ridership trends as well as individual rail-line performance and predictions.

---

## 📌 Project Overview

Urban public transportation demand changes according to factors such as day of the week, month, seasonality and long-term travel patterns. Understanding these patterns can help provide better insights into how public transport systems are being utilised.

**RideRadar KL** aims to:

* Analyse historical public transportation ridership in Klang Valley
* Identify temporal and behavioural ridership patterns
* Compare ridership across different transit modes
* Examine relationships between transportation services
* Build an XGBoost-based ridership prediction model
* Provide interactive visual analytics through a Streamlit dashboard
* Allow users to estimate ridership for selected historical or future dates

---

## 🎯 Objectives

1. **Data Preparation**
   Clean and filter public transportation ridership data to focus on Klang Valley services.

2. **Exploratory Data Analysis**
   Investigate yearly, monthly and day-of-week ridership patterns.

3. **Correlation Analysis**
   Examine relationships between different public transportation services.

4. **Predictive Modelling**
   Develop an XGBoost regression model using temporal features to predict daily ridership.

5. **Model Evaluation**
   Evaluate predictions using Mean Squared Error (MSE), Mean Absolute Error (MAE) and R².

6. **Interactive Data Product**
   Deploy the analysis as an interactive Streamlit dashboard for easier exploration and interpretation.

---

## 📊 Dataset

The project uses public transportation ridership data sourced from **data.gov.my and Prasarana**.

The dataset contains daily ridership records for various transportation services.

The analysis focuses on Klang Valley urban transportation services while excluding unrelated services outside the target scope.

### Data Preparation

The preprocessing workflow includes:

* Loading the ridership dataset
* Inspecting dataset structure and summary statistics
* Converting the `date` column into datetime format
* Filtering records from **2023 onwards**
* Removing transportation services outside the Klang Valley scope
* Sorting observations chronologically
* Exporting the cleaned dataset as `public_transport_ridership.csv`

---

## 🔍 Exploratory Data Analysis

RideRadar KL analyses ridership from several perspectives.

### Yearly Ridership

Examines changes in total ridership across different years to identify longer-term trends.

### Monthly Ridership

Visualises monthly passenger demand to identify fluctuations and changes throughout the year.

### Day-of-Week Analysis

Compares average ridership between:

* Monday
* Tuesday
* Wednesday
* Thursday
* Friday
* Saturday
* Sunday

This helps identify differences between weekday and weekend travel behaviour.

### Correlation Analysis

A correlation heatmap is used to examine the relationship between ridership across different transportation modes, including:

* LRT Kelana Jaya
* LRT Ampang
* Monorail KL
* MRT Putrajaya
* MRT Kajang
* Bus Rapid KL

---

## 🤖 Predictive Modelling

The updated version uses **XGBoost Regressor** for ridership prediction.

### Model

`XGBRegressor` is trained using temporal features extracted from the date:

| Feature     | Description                             |
| ----------- | --------------------------------------- |
| `dayofweek` | Day of the week represented numerically |
| `month`     | Month of the year                       |
| `year`      | Calendar year                           |
| `dayofyear` | Day number within the year              |

The dataset is sorted chronologically before being divided into training and testing sets.

A **80/20 train-test split without shuffling** is used to preserve the temporal ordering of the observations.

### Model Configuration

The current dashboard implementation uses:

```text
Objective: reg:squarederror
Number of estimators: 200
Learning rate: 0.1
```

---

## 📏 Model Evaluation

Model performance is evaluated using three regression metrics:

### Mean Squared Error (MSE)

Measures the average squared difference between actual and predicted ridership.

### Mean Absolute Error (MAE)

Measures the average absolute difference between actual and predicted ridership.

### R² Score

Measures how well the model explains the variation in the target ridership values.

The dashboard displays these metrics for each analysed transportation service.

---

## 🖥️ Interactive Streamlit Dashboard

The main output of RideRadar KL is an interactive Streamlit application.

### Main Dashboard

The overall dashboard provides high-level Klang Valley ridership insights through:

* **Total Ridership**
* **Average Daily Ridership**
* **Latest Monthly Growth**
* **Peak Day**
* Yearly ridership trends
* Monthly ridership trends
* Average ridership by day of week
* Transportation-mode correlation heatmap
* XGBoost prediction results

### Individual Rail-Line Analysis

Users can select individual rail services from the sidebar to perform a more detailed analysis.

Each rail-line page provides:

* Daily ridership trend
* Custom date-range filtering
* Yearly ridership trend
* Monthly ridership trend
* Average ridership by day of week
* XGBoost prediction performance
* Actual vs predicted ridership
* MSE, MAE and R² metrics

### 🔮 EasyFinder

The individual rail-line pages also include **EasyFinder**, which allows users to select a date and generate an estimated ridership value.

Users can select:

* A historical date for prediction
* A future date for forecasting

The application generates the required temporal features automatically and passes them to the trained XGBoost model.

---

## 🏗️ Project Workflow

```text
Public Transportation Dataset
            ↓
      Data Preprocessing
            ↓
   Klang Valley Filtering
            ↓
   Exploratory Data Analysis
            ↓
   Feature Engineering
            ↓
       XGBoost Model
            ↓
       Model Evaluation
            ↓
    Streamlit Dashboard
            ↓
Interactive Ridership Insights
```

---

## 🗂️ Project Structure

```text
RideRadarKL/
│
├── RideRadarKL.ipynb
│       └── Complete data science workflow
│
├── app.py
│       └── Streamlit dashboard application
│
├── public_transport_ridership.csv
│       └── Cleaned ridership dataset
│
├── requirements.txt
│       └── Python dependencies
│
└── README.md
        └── Project documentation
```

---

## 🛠️ Technologies Used

### Programming Language

* Python

### Data Processing

* Pandas
* NumPy

### Data Visualisation

* Matplotlib
* Seaborn
* Plotly

### Machine Learning

* XGBoost
* Scikit-learn

### Application Development

* Streamlit

### Statistical Modelling

* SARIMAX was explored as a statistical baseline during the modelling stage.

### Development Environment

* Jupyter Notebook

---

## 💡 Key Features

| Feature                   | Description                                        |
| ------------------------- | -------------------------------------------------- |
| 📊 Ridership Analytics    | Analyse historical Klang Valley transit demand     |
| 📈 Trend Analysis         | Explore yearly and monthly ridership patterns      |
| 📅 Temporal Analysis      | Compare ridership across days of the week          |
| 🔗 Correlation Analysis   | Examine relationships between transportation modes |
| 🤖 XGBoost Prediction     | Predict daily ridership using temporal features    |
| 📏 Model Evaluation       | Evaluate predictions using MSE, MAE and R²         |
| 🚆 Rail-Line Analysis     | Analyse individual Klang Valley rail services      |
| 🔮 EasyFinder             | Estimate ridership for selected dates              |
| 🖥️ Interactive Dashboard | Explore results through Streamlit                  |

---

## 🌏 Project Motivation

Public transportation plays an important role in supporting mobility across the Klang Valley. By combining public transportation data with data science and predictive modelling, RideRadar KL demonstrates how historical ridership data can be transformed into an interactive analytical tool.

Rather than presenting ridership data as static statistics, the project provides an accessible way to **explore trends, compare transportation services and investigate potential future demand**.

---

## 👨‍💻 Author

**Imran Haziq Bin Khairul Anuar**

Bachelor of Computer Science (Data Science)
Department of Information Systems
Universiti Malaya

---

## 📜 Disclaimer

RideRadar KL is an academic and data science project developed for analytical and educational purposes.

Predictions generated by the application are model-based estimates and should not be interpreted as official ridership forecasts by Prasarana or any Malaysian public transportation authority.
