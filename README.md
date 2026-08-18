# VARSHAA-X

### AI-Powered Rainfall Intelligence & Early Warning System

VARSHAA-X is an AI-driven rainfall intelligence platform designed to predict high-impact rainfall events, explain the factors behind predictions, and support location-aware risk awareness and decision-making.

---

## Problem Statement

Extreme and heavy rainfall events pose severe risks to urban infrastructure, transportation networks, agriculture, and local communities. Traditional weather monitoring systems often rely on static, regional thresholds that fail to capture localized risk variations. A single one-size-fits-all threshold is frequently insufficient because identical rainfall amounts can have vastly different consequences depending on local atmospheric moisture, terrain elevation, cloud characteristics, and vulnerability.

VARSHAA-X addresses this challenge by integrating environmental signal analysis, predictive risk scoring, explainable AI (XAI) feature attributions, and location-aware impact modeling into a unified decision-support platform.

---

## Key Features

- **Location-Aware Rainfall Prediction:** Dynamic prediction risk scoring synchronized across the entire application for any selected monitoring location.
- **Rainfall Forecast Visualization:** Native SVG-rendered trend lines displaying current intensity, peak expected rainfall, peak time, and forecast curves over a 1–6 hour horizon.
- **Environmental Signal Monitoring:** Real-time visibility into atmospheric moisture, cloud cover, surface temperature, wind patterns, and terrain elevation.
- **Explainable AI / Feature Attribution:** Transparent feature-influence breakdown (*prototype model attributions*) answering why a prediction was made in plain language.
- **Prediction Reliability Indicators:** Clear distinction between *Rain Event Probability* (likelihood of heavy rain) and *Model Reliability* (input consistency & operating range confidence).
- **Model Limitations & Failure-Mode Awareness:** Explicit documentation of operational constraints, edge cases, microburst vulnerabilities, and data latency risks.
- **Impact & Risk Assessment:** Interactive geospatial mapping combining rainfall risk with population exposure, road network vulnerability, and critical facility indicators.
- **What-If Impact Simulation:** Scenario simulation controls allowing operators to test hypothetical rainfall intensity, duration, and terrain sensitivity changes.
- **Historical Event Analysis:** Comparative climate-memory analogues pairing current predictions with historical pattern matches.
- **Alert & Action Planning:** Prioritized warning notifications accompanied by actionable response plans (drainage pre-positioning, road diversions, emergency readiness).
- **Persistent Global Location State:** Single source of truth location architecture that automatically updates all application views and persists across browser refreshes via `localStorage`.

---

## How It Works

The platform processes multi-parameter environmental signals through a unified pipeline:

```
Environmental Data (Moisture, Clouds, Temp, Wind, Elevation)
                          ↓
                  Prediction Engine
                          ↓
              Rainfall Risk Prediction (% & Risk Level)
                          ↓
           Explainable AI (Feature Attribution & XAI)
                          ↓
               Impact & Risk Assessment (Maps & Exposure)
                          ↓
           Alerts & Operational Decision Support
```

---

## Application Modules

### 1. Home / Command Center
Overview of active monitoring locations, high-impact risk indicators, quick action recommendations, and immediate forecast summary graphs.

### 2. Rainfall Prediction
Detailed prediction interface displaying current vs. peak expected rainfall, forecast timelines, model reliability indicators, and read-only environmental input grids.

### 3. Explainable AI
Interpretation center explaining the primary environmental factors driving the prediction, plain-language summary breakdowns, terminology definitions, failure modes, and a collapsible technical attribution table.

### 4. Impact & Risk Map
Geospatial map visualization rendering risk boundaries, population exposure statistics, vulnerable road segments, and critical infrastructure locations.

### 5. What-If Simulation
Interactive scenario builder allowing users to adjust rainfall intensity sliders, duration controls, and terrain sensitivity to observe simulated consequence cascades.

### 6. Historical Events
Climate memory log comparing current prediction parameters against historical heavy-rainfall analogues and pattern matches.

### 7. Alerts
Early warning hub displaying prioritized threat levels (Critical, High, Watch) alongside localized operational action plans.

### 8. Model & Performance
Technical diagnostic view providing model architecture details, confidence metrics, and feature sensitivity analyses.

---

## Explainable AI (XAI) Architecture

VARSHAA-X emphasizes transparency so operators understand the rationale behind automated risk alerts before taking operational action.

### Probability vs. Reliability Distinction
- **Rain Event Probability (e.g., 76%):** Represents the estimated likelihood of a heavy rainfall event occurring within the forecast window.
- **Model Reliability (e.g., HIGH / 76.4% input consistency):** Represents how trustworthy the prediction is, based on whether input data falls within expected operating distributions.

> **Note on Prototype Status:** Current feature explanations represent prototype feature-influence calculations. Production deployment is designed to connect these visual attributions to the trained machine learning model's actual SHAP (SHapley Additive exPlanations) and Grad-CAM attribution pipelines.

---

## Global Location Architecture

VARSHAA-X employs a single centralized state architecture (`window.VARSHAA_APP_STATE.location`):
- Selecting a location anywhere in the application (e.g., Ranchi, Bengaluru, Bhubaneswar, Mumbai, Delhi, Mysuru, Balasore, or custom places) updates **all pages simultaneously**.
- Selections are stored locally in the browser (`localStorage.setItem("varshaa_selected_location", ...)`), ensuring location continuity across page reloads.

---

## Technology Stack

- **Frontend Core:** HTML5, Vanilla JavaScript (ES6+), Vanilla CSS (Custom CSS variable tokens, flexbox/grid layouts).
- **Mapping & Geospatial:** [Leaflet.js](https://leafletjs.com/) (v1.9.4) with OpenStreetMap vector tiles.
- **Data Visualization:** Custom inline SVG rendering algorithms for responsive, zero-dependency forecast curves and historical charts.
- **State & Storage:** Native JavaScript browser `localStorage` API for state persistence.
- **Local Dev Server:** Built-in Python `http.server`.

---

## Running Locally

1. **Clone or Download the Repository:**
   ```bash
   git clone https://github.com/your-org/VARSHAA-X.git
   cd VARSHAA-X
   ```

2. **Start the Local Web Server:**
   Using Python 3:
   ```bash
   python -m http.server 8080
   ```

3. **Access the Application:**
   Open your browser and navigate to:
   ```
   http://localhost:8080
   ```

---

## Future Roadmap

- **Production ML Engine:** Integrating trained deep learning ensemble models (CNN + LSTM + XGBoost) for operational weather prediction.
- **Live Data Ingestion:** Connecting real-time Doppler weather radar (DWR) feeds and satellite meteorological API streams.
- **Production SHAP Pipeline:** Directly piping trained model SHAP values into the Explainable AI attribution interface.
- **Automated Dispatch:** Connecting alert triggers to SMS, WhatsApp, and emergency management agency push notification gateways.

---

### License & Attribution
Designed and developed for rainfall risk intelligence and decision-support prototyping.
