# 🌤 AirCast — AI-Powered Real-Time Air Quality Forecast
**by Skyphoria Team**

**AirCast** is an intelligent Streamlit web application that predicts short-term air quality indicators (PM2.5, O₃, NO₂, and AQI) across major North American cities.  
The system integrates live atmospheric and meteorological data from **Open-Meteo CAMS** with AI models trained on multi-year environmental datasets, including **NASA DONKI** space-weather observations.  
Its goal is to provide **interpretable, human-centered forecasts** that help people understand and respond to air quality risks in real time.

---

## 🚀 Key Features

- 🌎 **Real-Time Data Integration**  
  Continuously fetches hourly meteorological and pollutant data from the [Open-Meteo CAMS Air Quality API](https://open-meteo.com/en/docs/air-quality-api), ensuring up-to-date information.

- 🤖 **AI-Based Predictions**  
  Predicts near-term PM2.5 and O₃ concentrations using **LightGBM models** (`model_pm25.joblib`, `model_o3.joblib`) trained on 4 years of historical air quality and space-weather data.

- 📊 **Interactive Visualizations**  
  Displays dynamic charts for the next 72 hours of forecasted air quality indicators, with AQI, PM2.5, O₃, and NO₂ trends in an intuitive layout.

- 💬 **Human-Friendly Explanations**  
  Translates complex pollutant metrics into clear, actionable messages for the general public.  
  Each forecast includes **health category, risk color code, and personalized recommendations**.

- 🕐 **Ultra-Short-Term Nowcast (0–2h)**  
  Provides immediate nowcasting alerts based on exponential smoothing of recent air quality measurements.

- 💡 **Fully Deployed Web App**  
  Built and hosted on **Streamlit Cloud**, accessible instantly through any browser without installation.

---

## 🧠 Scientific Background

### Data Sources

| Source | Purpose | Access Point |
|:--------|:----------|:-------------|
| ☀️ **NASA DONKI** | Space-weather indices and solar event data | [api.nasa.gov/DONKI](https://api.nasa.gov/) |
| 🌫 **Open-Meteo CAMS Air Quality API** | Real-time air pollution and meteorological data | [air-quality-api.open-meteo.com](https://open-meteo.com/en/docs/air-quality-api) |
| 🌡 **NOAA / ERA5 (via Open-Meteo)** | Atmospheric and weather reanalysis data | integrated within Open-Meteo endpoints |

---

## 🧩 Machine Learning Models

Two **LightGBM regression models** are used for pollutant forecasting:

| Model | Target Variable | Description |
|:------|:----------------|:-------------|
| `model_pm25.joblib` | PM2.5 concentration (µg/m³) | Predicts fine particulate matter levels influencing AQI |
| `model_o3.joblib` | O₃ concentration (µg/m³) | Estimates near-surface ozone using meteorological inputs |

Models were trained using four years (2021–2025) of NASA + CAMS data, with cross-validation to ensure robustness against temporal drift and seasonality.

---

## 📘 Application Structure

aircast-ai/
├── app.py # Streamlit app source code
├── model_pm25.joblib # Trained LightGBM model for PM2.5
├── model_o3.joblib # Trained LightGBM model for O₃
├── requirements.txt # Python dependencies
└── README.md # Project documentation

---

## ⚙️ Installation Guide

### 1. Clone the Repository

```bash
git clone https://github.com/feridmirzeliyev/aircast-ai.git
cd aircast-ai


##  🌍 Deployment

The app is pre-configured for Streamlit Cloud.
To deploy:

Push your project to GitHub

Visit streamlit.io/cloud

Click “New App” → select your repository

Enter:

Main file path: app.py

Python version: >=3.9

Dependencies file: requirements.txt

Example hosted version:
🔗 https://aircast-ai.streamlit.app


## 🧩 Example Workflow

Select your city and region (e.g., Phoenix, Toronto, New York)

The app retrieves latest hourly air quality and meteorological data

AI models predict PM2.5 and O₃ concentrations for the next 72 hours

AQI is computed dynamically

The system provides interpretable forecasts + personalized health advice


## 🔬 Technical Details

Language: Python 3.10

Frameworks: Streamlit, LightGBM, scikit-learn, pandas, numpy

Data Update Frequency: Every hour (CAMS + Open-Meteo APIs)

Forecast Horizon: 0–72 hours

Regions Covered: North America (modifiable via latitude–longitude input)



## 👩‍💻 Developer 

Author: SkyPhoria Team


## 🙌 Acknowledgements

NASA DONKI API
 — space weather data (https://api.nasa.gov/)

Open-Meteo CAMS Air Quality API
 — real-time air composition data (https://open-meteo.com/en/docs/air-quality-api)

LightGBM
 — gradient boosting for machine learning

Streamlit
 — interactive app framework for data science


