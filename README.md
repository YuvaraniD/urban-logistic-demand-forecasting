# Urban Logistics Demand Forecasting – Melbourne

## 📊 Project Overview
This project analyses and forecasts urban freight demand patterns in Melbourne using transport activity sensor data as a proxy for last-mile delivery activity. The goal is to understand temporal and spatial demand behaviour and build predictive models to support city logistics planning, freight management, and traffic regulation.

The study applies statistical and deep learning approaches — **SARIMA**, **Prophet**, and **LSTM** — to model complex time-series patterns in urban logistics demand.

## 🎯 Objectives
- Analyse hourly, daily, and monthly logistics demand patterns
- Identify peak congestion periods and low-traffic windows
- Evaluate weekday, weekend, holiday, and event impacts
- Build and compare predictive models for demand forecasting
- Translate forecasts into actionable city planning recommendations

## 📁 Dataset
- **Source:** [Transport Activity Counts](https://data.melbourne.vic.gov.au/explore/dataset/transport-activity-counts/api/), City of Melbourne Open Data Portal
- **Period:** 2023 – 2026
- **Granularity:** Hourly vehicle counts across 36 sensor locations, filtered to vans and trucks only (proxy for delivery vehicles, since direct freight data isn't publicly available)

## ⚙️ Project Workflow
1. **Data Preparation** — combined yearly ZIP files, parsed timestamps, filtered to vans/trucks, engineered time features (hour, day, week, month)
2. **Exploratory Data Analysis** — hourly/daily/monthly trends, day-of-week × hour heatmap
3. **STL Decomposition & Anomaly Detection** — z-score anomaly detection on residuals
4. **Stationarity & Lag Testing** — ADF test, ACF/PACF analysis
5. **Spatial Analysis** — sensor-level and geographic demand concentration
6. **Forecasting** — SARIMA, Prophet, LSTM model comparison
7. **Planning Insights** — translating LSTM forecasts into operational recommendations

## 📈 Model Performance

| Model | MAE | RMSE | MAE % |
|---|---|---|---|
| SARIMA | 43.42 | 70.16 | 61.7% |
| Prophet | 34.62 | 49.55 | 49.2% |
| **LSTM** | **14.07** | **22.45** | **20.0%** |

LSTM outperformed both statistical baselines, achieving less than half the error of Prophet and a third of SARIMA. Its 168-hour (7-day) rolling input window allowed it to adapt to the late-2025 structural demand surge, while SARIMA and Prophet continued predicting from the lower historical baseline.

## 🔍 Key Insights

### ⏰ Temporal Patterns
![Hourly demand pattern](01_hourly_pattern.png)
- Demand is highest between **10am–12pm**, peaking around **11am**
- Vans drive the vast majority of demand variation; truck activity stays relatively flat throughout the day
- Overnight demand (12am–5am) is minimal, with a sharp ramp-up between 6am–9am

![LSTM predicted demand by hour](17_lstm_predicted_hourly.png)
- LSTM forecasts confirm the same pattern: peak demand of ~171 predicted vehicles/hour at 11am–12pm, more than double the all-day average (~70/hr)

### 📅 Day-of-Week Trends
![Day-of-week × hour heatmap](02_heatmap_dow_hour.png)
- **Wednesday** is the busiest day; **Sunday** is the quietest
- Weekend demand is **~42% of weekday demand** (a ~58% drop)
- Peak demand window is consistently **9am–1pm on weekdays**

### 📈 Monthly Trend & Structural Shift
![Monthly trend](03_monthly_trend.png)
- Demand grew rapidly in early 2023, stabilised through 2023–2025, then surged sharply in **late 2025** to a new, higher baseline

### 🔬 STL Decomposition
![STL decomposition](04_stl_decomposition.png)
- Confirms strong weekly seasonality and a clear late-2025 structural shift in the trend component

### 🚨 Anomaly Detection & Events
![Anomaly detection on daily series](05_anomaly_detection.png)
- **56 anomaly days** were detected across the dataset, **all** mapped to known Melbourne events or public holidays — zero unidentified anomalies
- **22 suppression days** (holidays) and **34 surge days** (major events)

![Anomalies by event type](06_anomaly_by_event.png)
- Christmas Day and Boxing Day show the lowest counts in the dataset
- F1 Grand Prix, Australian Open, AFL Grand Final, and Melbourne Cup consistently produce demand surges

### 🏙️ Spatial Concentration
![Demand by sensor location](08_spatial_demand_bars.png)
- Demand is extremely concentrated: the **top 3 sensors account for 94.2%** of all van + truck activity
- **Queens Bridge Street** alone accounts for **39.1%** of total activity

![Geographic distribution of demand](09_spatial_map.png)
- High-demand sensors cluster tightly along the **Southbank and CBD corridor**, confirming last-mile logistics activity is concentrated in Melbourne's inner-city commercial precinct

## 🏙️ City Planning Recommendations
- Prioritise loading zone availability and traffic management in the **CBD/Southbank corridor**, especially **9am–1pm on weekdays**
- Scale down enforcement and operations on **public holidays** (demand drops ~70%)
- Prepare enhanced logistics access for major recurring events (AFL Grand Final, F1 Grand Prix, Australian Open)
- Schedule road works and infrastructure upgrades on **weekends and public holidays**, when demand is lowest
- Update capacity planning models to reflect the **higher post-2025 demand baseline**
- Retrain the LSTM model periodically as new data becomes available

## 🧠 Key Takeaway
Urban logistics demand in Melbourne is highly structured, time-dependent, and event-driven rather than random. Deep learning (LSTM) significantly outperforms classical statistical models by capturing nonlinear temporal patterns and adapting to structural shifts in demand.

## 🛠️ Tech Stack
- **Languages:** Python
- **Data Processing:** Pandas, NumPy
- **Visualisation:** Matplotlib, Seaborn
- **Statistical Modelling:** Statsmodels (SARIMA, STL, ADF, ACF/PACF)
- **Forecasting:** Prophet
- **Deep Learning:** TensorFlow / Keras (LSTM)

## 🚀 Future Improvements
- Incorporate real-time traffic data
- Add external variables (weather, fuel prices)
- Deploy the model as a forecasting API
- Extend to multi-city comparison

## 📌 Author
**Yuvarani Dharmasivam**
Master of Data Science – Deakin University
