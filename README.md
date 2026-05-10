# Urban Logistics Demand Forecasting – Melbourne

## 📊 Project Overview
This project focuses on analysing and forecasting urban freight demand patterns in Melbourne using historical multi-year logistics data. The goal is to understand temporal demand behaviour and build predictive models to support city planning, traffic management, and freight optimisation.

The study applies statistical and machine learning approaches, including SARIMA, Prophet, and LSTM, to model complex time-series patterns in urban logistics demand.

---

## 🎯 Objectives
- Analyse hourly and daily logistics demand patterns
- Identify peak congestion periods and low-traffic windows
- Evaluate weekday, weekend, holiday, and event impacts
- Build predictive models for demand forecasting
- Compare traditional statistical models with deep learning (LSTM)

---

## 📁 Dataset
- Source: Melbourne urban logistics/traffic dataset
- Format: Multi-year compressed ZIP files (2021–2024)
- Granularity: Hourly vehicle counts (van + truck movements)

> Note: Raw dataset files are stored in the `data/` directory.

---

## ⚙️ Project Workflow

### 1. Data Preparation
- Extraction of multi-year ZIP files
- Standardisation of schema across years
- Handling missing values and datetime formatting
- Merging into a unified time-series dataset

### 2. Exploratory Data Analysis (EDA)
- Hourly demand trends
- Day-of-week patterns
- Heatmap analysis (hour × weekday)
- Holiday and event impact analysis

### 3. Feature Engineering
- Hour of day
- Day of week
- Weekend indicator
- Holiday/event flags

### 4. Forecasting Models
- SARIMA (baseline statistical model)
- Prophet (trend + seasonality decomposition)
- LSTM (deep learning sequence model)

---

## 📈 Model Performance

| Model   | MAE   | RMSE  |
|----------|------|-------|
| SARIMA   | 43.42 | 70.16 |
| Prophet  | 34.62 | 49.55 |
| **LSTM** | **14.07** | **22.45** |

👉 LSTM outperformed all baseline models, capturing structural shifts in demand more effectively.

---

## 🔍 Key Insights

### ⏰ Temporal Patterns
- Peak demand occurs at **11:00 AM**
- Strong congestion window: **9 AM – 1 PM**
- Overnight demand (12 AM – 5 AM) is minimal

### 📅 Day-of-Week Trends
- **Wednesday** is the busiest day
- **Sunday** is the quietest
- Weekends show ~58% lower demand than weekdays

### 🎉 Holiday & Event Effects
- Public holidays reduce demand by ~70%
- Major events (AFL Grand Final, F1, Australian Open) cause mild demand surges
- Demand patterns are highly predictable and event-driven

---

## 🏙️ City Planning Recommendations
- Prioritise loading zone management during **weekday mornings (9 AM–1 PM)**
- Schedule roadworks during **weekends and public holidays**
- Reduce enforcement intensity during low-demand periods
- Prepare for predictable surges during major Melbourne events
- Update planning models to reflect post-2025 increased demand baseline

---

## 🧠 Key Takeaway
Urban logistics demand in Melbourne is highly structured, time-dependent, and event-sensitive. Deep learning models (LSTM) significantly improve forecasting accuracy by capturing nonlinear temporal patterns and structural shifts.

---

## 🛠️ Tech Stack
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Statsmodels (SARIMA)
- Prophet
- TensorFlow / Keras (LSTM)

---

## 🚀 Future Improvements
- Incorporate real-time traffic data
- Add external variables (weather, fuel prices)
- Deploy model as a forecasting API
- Extend to multi-city comparison

---

## 📌 Author
Yuvarani D  
Master’s in Data Science – Deakin University  
