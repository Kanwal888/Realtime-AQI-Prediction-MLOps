# Realtime-AQI-Prediction-MLOps
End-to-End AQI Prediction System with Hopsworks &amp; XGBoost
# 🌬️ Real-Time Air Quality Forecasting & Analytics System (MLOps)

An end-to-end MLOps architecture for predicting Air Quality Index (PM2.5) for the next 72 hours (3 days). Built with **Hopsworks Feature Store**, **XGBoost**, and an interactive **Gradio Dashboard**.

---

## 🔑 Hopsworks & Project Setup Details

* **Hopsworks Project Name**: `Pearls_AQI_Predictor` / `aqi_predictor_pearls`
* **API Key Name**: `Pearls_AQI_Predictor`
* **Generated API Key**: `XNK3PoVOnMZpkS2o.8CJxdmTW56nYgDuwCzdL61SrEzQULogJeFhOXnREoc5aQROxvnnsYCqldlJfWwTW`

---

## 🛠️ Windows Environment & Temporary Directory Fix

During setup on Windows environments, temporary path issues (`/tmp` directory errors) were resolved by re-routing environment variables in PowerShell prior to Hopsworks login:

```powershell
New-Item -ItemType Directory -Force C:\tmp
$env:TEMP="C:\tmp"
$env:TMP="C:\tmp"

# Verification
python -c "import tempfile; print(tempfile.gettempdir())"
# Expected Output: C:\tmp

# Hopsworks Authentication Verification
python -c "import hopsworks; p=hopsworks.login(); print('PROJECT:', p.name)"
# Expected Output: PROJECT: aqi_predictor_pearls






