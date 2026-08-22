# 🌬️ Real-Time Air Quality Forecasting & Analytics System (MLOps)

> **End-to-End MLOps Pipeline for 72-Hour $PM_{2.5}$ Forecasting**

An end-to-end MLOps-based Air Quality Forecasting and Analytics System designed to predict $PM_{2.5}$ concentrations for the next 72 hours (3 days) using real-time environmental data.

The system integrates Open-Meteo API, Hopsworks Feature Store, XGBoost Regression, Hopsworks Model Registry, and an interactive Gradio Dashboard into a complete machine-learning lifecycle.

---

## 🖼️ Dashboard & Analytics Preview

### Real-Time AQI Predictions & Overview Metrics

<img width="1644" height="561" alt="AQI Dashboard Overview" src="https://github.com/user-attachments/assets/fb6a4a00-b4ed-42d9-b106-f17fe1160d38" />

### XGBoost Feature Importance & Forecast Dataset Sample

<img width="1704" height="403" alt="Feature Importance and Data Sample" src="https://github.com/user-attachments/assets/f005ae06-5d50-496a-ac63-4c4c49bba846" />

---

## 📌 Project Overview

Air pollution forecasting requires reliable environmental data, reproducible feature management, machine-learning models, and an accessible interface for interpreting predictions.

This project implements a complete pipeline that:

* Collects environmental data from the Open-Meteo Air Quality API.
* Processes and engineers environmental and temporal features.
* Stores features in Hopsworks Feature Store.
* Performs historical data backfilling for model development.
* Retrieves training data through Hopsworks Feature Query Service.
* Trains an XGBoost Regressor for $PM_{2.5}$ prediction.
* Evaluates the trained model using regression metrics.
* Registers the trained model in Hopsworks Model Registry.
* Generates 72-hour $PM_{2.5}$ forecasts.
* Calculates air-quality alert levels.
* Provides feature-importance analysis.
* Visualizes predictions through an interactive Gradio Dashboard.

---

## 🎯 Project Objectives

* Develop a reproducible MLOps pipeline for air-quality forecasting.
* Predict hourly $PM_{2.5}$ concentrations for the next 72 hours.
* Centralize feature management using Hopsworks Feature Store.
* Automate model training and model registration.
* Provide interpretable feature-importance analysis.
* Deliver real-time forecasts through an interactive web dashboard.

---

## 🏗️ System Architecture

```text
┌──────────────────────────┐
│     Open-Meteo API       │
│  Real-Time AQI Data      │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│   Feature Engineering    │
│ PM10 • Dust • CO • PM2.5 │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ Hopsworks Feature Store  │
│      aqi_features        │
└────────────┬─────────────┘
             │
    Historical Data / Feature View
             │
             ▼
┌──────────────────────────┐
│   XGBoost Regressor      │
│     Model Training       │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ Hopsworks Model Registry │
│    Trained Model         │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│  72-Hour Forecasting     │
│      Pipeline            │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    Gradio Dashboard      │
│ Forecast • Alerts •      │
│ Analytics • Charts       │
└──────────────────────────┘
```

---

## ☁️ Hopsworks Infrastructure

| Component             | Configuration                   |
| --------------------- | ------------------------------- |
| **Hopsworks Project** | `aqi_predictor_pearls`          |
| **Project Workspace** | `Pearls_AQI_Predictor`          |
| **Feature Group**     | `aqi_features`                  |
| **Feature Store**     | Hopsworks Feature Store         |
| **Model Registry**    | Hopsworks Model Registry        |
| **Feature Query**     | Hopsworks Feature Query Service |
| **Forecast Horizon**  | 72 hours                        |

---

## 🌍 Target Variable & Features

### Target Variable

* **$PM_{2.5}$ Concentration**: Unit: $\mu g/m^3$
* Fine particulate matter ($\le 2.5\ \mu m$) serving as the primary ambient air quality metric.

### Model Features

| Feature           | Description                           |
| ----------------- | ------------------------------------- |
| `pm10`            | $PM_{10}$ concentration ($\mu g/m^3$) |
| `dust`            | Atmospheric dust concentration        |
| `carbon_monoxide` | Carbon monoxide ($CO$) concentration  |

---

## 📈 Model Performance & Evaluation

| Metric                             |                 Score |
| ---------------------------------- | --------------------: |
| **$R^2$ Score**                    |            **0.9492** |
| **Mean Absolute Error (MAE)**      |  **7.16 $\mu g/m^3$** |
| **Root Mean Squared Error (RMSE)** | **11.28 $\mu g/m^3$** |

* **$R^2 = 0.9492$**: Indicates that the XGBoost model explains approximately $94.92%$ of the variance in target $PM_{2.5}$ values.
* **MAE = 7.16**: Average magnitude of prediction errors.

---

## 🚨 Air-Quality Alert System

The system maps predicted $PM_{2.5}$ values into standardized health alert levels:

* 🟢 **Good**
* 🟡 **Moderate**
* 🟠 **Unhealthy for Sensitive Groups**
* 🔴 **Unhealthy**
* 🟣 **Very Unhealthy**
* ⚫ **Hazardous**

---

## 🖥️ Environment Configuration (Windows)

During Windows setup, the execution directory was redirected to solve path conflicts:

```powershell
New-Item -ItemType Directory -Force C:\tmp
$env:TEMP="C:\tmp"
$env:TMP="C:\tmp"

# Verify Temporary Directory
python -c "import tempfile; print(tempfile.gettempdir())"
# Expected Output: C:\tmp

# Hopsworks Connection Verification
python -c "import hopsworks; p=hopsworks.login(); print('PROJECT:', p.name)"
# Expected Output: PROJECT: aqi_predictor_pearls
```

---

## 🛠️ Technology Stack

| Category                      | Technology                               |
| ----------------------------- | ---------------------------------------- |
| **Programming Language**      | Python 3.12                              |
| **MLOps Platform**            | Hopsworks AI                             |
| **Feature Store & Registry**  | Hopsworks Feature Store / Model Registry |
| **Machine Learning**          | XGBoost, Scikit-Learn                    |
| **Data Processing**           | Pandas, NumPy                            |
| **Data Source**               | Open-Meteo Air Quality API               |
| **Visualization & Interface** | Matplotlib, Gradio                       |

---

## 📁 Project Structure

```text
Realtime-AQI-Prediction-MLOps/
│
├── app.py
├── README.md
├── requirements.txt
│
├── data/
├── models/
├── notebooks/
└── src/
    ├── data/
    ├── features/
    ├── training/
    ├── prediction/
    └── visualization/
```

---

## 🚀 Installation & Running

### 1. Clone Repository

```bash
git clone https://github.com/Kanwal888/Realtime-AQI-Prediction-MLOps.git
cd Realtime-AQI-Prediction-MLOps
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run Dashboard

```bash
python app.py
```

---

## 👩‍💻 Author

**Kanwal Syed**

*Real-Time Air Quality Forecasting & Analytics System*

**GitHub:**
https://github.com/Kanwal888/Realtime-AQI-Prediction-MLOps
