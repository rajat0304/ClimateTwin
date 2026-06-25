# 🌍 AI-Powered Digital Twin of India's Climate
**ISRO Hackathon Proof of Concept (PoC) - Pilot Region: Maharashtra**

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![XGBoost](https://img.shields.io/badge/XGBoost-Machine%20Learning-orange)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-red)
![Status](https://img.shields.io/badge/Status-Hackathon_PoC-success)

## 📌 Problem Statement
Climate change requires proactive, data-driven decision-making. Traditional meteorological dashboards only display historical or current data. This project develops an **AI-Powered Digital Twin** of India's climate (piloted in Maharashtra) using national IMD datasets. It is not just a dashboard; it is a simulation engine capable of monitoring current states, predicting future weather, simulating "What-If" climate scenarios, and automatically generating risk-based recommendations.

## 🏗️ Core Architecture (The Digital Twin)
Our solution transitions from standard linear machine learning to a stateful Digital Twin architecture, comprising five core engines:

1. **State Management (`ClimateState`)**: Maintains the current physical state (Temperature, Rainfall, Date) of the pilot region.
2. **AI Prediction Engine**: Utilizes an XGBoost regression model (trained on IMD `.GRD` datasets) to predict short-term rainfall and temperature fluctuations.
3. **Climate Risk Engine**: Processes the `ClimateState` through domain-specific algorithms to calculate normalized risk indices (0-100%) for:
   * 🌊 Flood Risk
   * 🌡️ Heat Stress
   * 🏜️ Drought Risk
4. **What-If Simulation Engine**: Allows users to alter current environmental variables (e.g., +2°C temperature, +50mm rainfall) and cascades these changes through the Risk Engine to simulate future climate vulnerabilities.
5. **Recommendation Engine**: Automatically generates actionable advisories (e.g., Crop Advisory, Reservoir Management, Heatwave Alerts) based on the computed risk thresholds.

## 📊 Datasets Used
* **IMD Gridded Rainfall (.GRD)** - Daily precipitation data.
* **IMD Gridded Maximum Temperature (.GRD)** - Daily max temperature.
* **IMD Gridded Minimum Temperature (.GRD)** - Daily min temperature.
* *Note: Data was parsed, spatially clipped to the Maharashtra bounding box (33x37 grid), and aggregated into a state-level climate dataframe for this PoC.*

## 📂 Project Structure
```text
├── data/
│   ├── maharashtra_climate_twin.csv    # Extracted and engineered dataset
├── models/
│   ├── rainfall_xgb.pkl                # Trained XGBoost prediction model
│   ├── features.pkl                    # Model feature pipelines
├── core/
│   ├── engines.py                      # Contains ClimateState and ClimateRiskEngine classes
├── app.py                              # Main Streamlit Interactive Dashboard
├── IMD_Data_Processing.ipynb           # Colab notebook for .GRD parsing & Model Training
├── README.md
