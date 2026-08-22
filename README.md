# Realtime-AQI-Prediction-MLOps
End-to-End AQI Prediction System with Hopsworks &amp; XGBoost

# 🌬️ Real-Time Air Quality Prediction & Analytics System

An end-to-end MLOps architecture for predicting Air Quality Index (PM2.5) for the next 72 hours (3 days). Built with **Hopsworks Feature Store**, **XGBoost**, and an interactive **Gradio Dashboard**.

---

## 🚀 Key Features Implemented

* **Feature Pipeline Development**
  * Fetches real-time weather and pollutant data (PM10, Dust, Carbon Monoxide) from Open-Meteo API.
  * Computes temporal and derived environmental features.
  * Ingests processed features into **Hopsworks Feature Store** (`aqi_features`).

* **Historical Data Backfill**
  * Historical feature backfilling executed for historical baseline generation.
  * Prepared comprehensive training data set with dynamic time splits.

* **Training Pipeline Implementation**
  * Retrieved feature views directly from Hopsworks Feature Store.
  * Trained **XGBoost Regressor** with hyperparameter evaluation.
  * Persisted model artifacts directly into **Hopsworks Model Registry**.

* **Interactive Web Application Dashboard**
  * Real-time inference pipeline loads trained XGBoost model artifacts for 3-day forecasting.
  * Live **Gradio Interactive Dashboard** displaying metrics, alert badges, trend graphs, and data tables.

* **Advanced Analytics & Explainability**
  * Automated **Feature Importance analysis** highlighting major contributors (PM10, Dust, CO).
  * Dynamic air quality alert levels (Moderate, Unhealthy, Hazardous) based on particulate thresholds.

---

## 📊 Model Evaluation Performance

| Metric | Score |
| :--- | :--- |
| **$R^2$ Score** | **0.9492** |
| **MAE** | **7.16 µg/m³** |
| **RMSE** | **11.28 µg/m³** |

---

## 🛠️ Tech Stack & Tools

* **Language**: Python 3.12
* **Feature Store & Registry**: Hopsworks AI
* **Machine Learning**: XGBoost, Scikit-Learn
* **Data Processing**: Pandas, NumPy
* **Visualization & Frontend**: Matplotlib, Gradio

---

## 🖥️ How to Run the Project

1. **Clone the Repository**:
   ```bash
   git clone [https://github.com/your-username/aqi-prediction-system.git](https://github.com/your-username/aqi-prediction-system.git)
   cd aqi-prediction-system
