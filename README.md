# CAT-Predictor-ML: High-Altitude Clear Air Turbulence Forecasting

[![Aviation Safety](https://img.shields.io/badge/Aviation-Safety-blue)](https://github.com/KadirGokdeniz/CAT-Predictor-ML)
[![AUC Score](https://img.shields.io/badge/AUC-0.904-success)](https://github.com/KadirGokdeniz/CAT-Predictor-ML)
[![Status](https://img.shields.io/badge/Status-Under%20Review-yellow)](https://github.com/KadirGokdeniz/CAT-Predictor-ML)

## 🎯 Project Overview
This project pioneers a machine learning framework to predict high-altitude Clear Air Turbulence (CAT) with remarkable accuracy (AUC: 0.904). By integrating aircraft aerodynamics with meteorological data, we've established a new benchmark for turbulence prediction in aviation safety.

### Key Achievements
- **Superior Detection**: 86.6% POD for moderate-to-severe turbulence
- **Multi-Source Integration**: Combined ERA5 reanalysis, PIREPs, and BADA aerodynamic parameters
- **Operational Relevance**: Identified critical spatiotemporal patterns for flight planning optimization

<p align="center">
  <img src="/assets/spatial.png" alt="CAT Hotspots" width="600"/>
  <br>
  <em>Spatial Distribution of CAT Reports and TI3 Index Across US Airspace (2022-2024)</em>
</p>

<p align="center">
  <img src="/assets/cat_distribution.png" alt="Hourly & Monthly Distribution" width="500"/>
  <br>
  <em>Hourly & Monthly CAT Distribution</em>
</p>
## 🔬 Scientific Innovation

Our approach delivers three core advancements:

### 1. Aircraft-Specific Dynamics
- Incorporated drag force, lift-to-drag ratio, and wing loading to quantify turbulence impact
- Improved moderate-to-severe turbulence detection by 2.1% (POD from 0.845 to 0.866)
- Reduced false negatives by 12% in critical severe turbulence scenarios

### 2. Atmospheric Predictors
- Identified TI3 turbulence index and Richardson number as key indicators
- Feature importance analysis revealed geographic coordinates (17.5%) and wind dynamics as dominant predictors
- Optimized model captured non-linear relationships in upper tropospheric instability

### 3. Seasonal & Diurnal Patterns
- Winter months exhibited highest CAT frequency, with 2023-2024 peaking at ~1100 MOD CAT incidents
- Evening hours (15:00-21:00) demonstrated 3.5× higher turbulence reports across all seasons
- Jet stream seasonal shifts strongly correlated with turbulence patterns (R² = 0.74)

## 📊 Methodology & Results

### Data Integration Architecture
```
┌────────────┐    ┌────────────┐    ┌────────────┐
│    ERA5    │    │   PIREPs   │    │    BADA    │
│ Reanalysis │    │  Database  │    │ Aerodynamics│
└─────┬──────┘    └─────┬──────┘    └─────┬──────┘
      │                 │                 │
      ▼                 ▼                 ▼
┌─────────────────────────────────────────────┐
│        Feature Engineering & Selection       │
└─────────────────────┬───────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────┐
│             Gradient Boosting Models         │
└─────────────────────┬───────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────┐
│         Spatiotemporal CAT Prediction        │
└─────────────────────────────────────────────┘
```

### Performance Metrics

| Model         | Dataset          | AUC   | POD   | FAR   | CSI   | TSS   |
|---------------|------------------|-------|-------|-------|-------|-------|
| XGBoost       | All Categories   | 0.901 | 0.796 | 0.154 | 0.695 | 0.652 |
| XGBoost+Aero  | All Categories   | **0.904** | **0.809** | 0.158 | **0.703** | **0.657** |
| XGBoost       | MOD-SEV Only     | 0.928 | 0.845 | 0.139 | 0.743 | 0.708 |
| XGBoost+Aero  | MOD-SEV Only     | **0.928** | **0.866** | 0.150 | **0.753** | **0.716** |
| LightGBM+Aero | All Categories   | 0.902 | 0.815 | 0.166 | 0.701 | 0.652 |
| Random Forest | All Categories   | 0.889 | 0.785 | 0.170 | 0.676 | 0.624 |
| AdaBoost      | All Categories   | 0.893 | 0.770 | 0.161 | 0.682 | 0.633 |

<p align="center">
  <img src="/assets/feature.png" alt="Feature Importance" width="500"/>
  <br>
  <em>Feature Importance Rankings from XGBoost Model</em>
</p>

## 🌍 Impact & Applications

### Aviation Safety Enhancement
- **Proactive Risk Management**: Early identification of CAT enables strategic route planning
- **Operational Efficiency**: Reduced fuel consumption and emissions from unnecessary diversions
- **ICAO Compliance**: Results compatible with standardized EDR turbulence metrics

### Climate Adaptation Framework
- Model framework adaptable to shifting jet stream patterns due to climate change
- Potential to address the documented increase in CAT frequency and intensity
- Baseline established for tracking long-term atmospheric stability trends

### Beyond Aviation
- Methodology applicable to autonomous aerial vehicle navigation systems
- Potential extensions to wind energy optimization and atmospheric science research
- Pattern recognition approach transferable to other complex fluid dynamics problems

## 🛠️ Technical Specifications

### Turbulence Diagnostics Implemented
- TI1, TI2, TI3 (Elrod's turbulence indices)
- Richardson number and Brunt-Väisälä frequency
- Vertical wind shear and horizontal divergence
- Potential vorticity gradient
- Dutton's empirical index
- Relative vorticity squared

### Aerodynamic Parameters
- Maximum lift force and load factor
- Drag force and lift-to-drag ratio
- Wing loading and aspect ratio
- Buffet coefficient integration

### Machine Learning Pipeline
- Stratified cross-validation (5-fold)
- Hyperparameter optimization via grid search
- Bayesian optimization for learning rate
- Model ensembling for final predictions

## ⚠️ Code Availability
The codebase is temporarily restricted due to journal review processes. Full release is planned following publication (expected Q2 2025).

## 📑 Citation
```bibtex
@article{gokdeniz2024cat,
  title={Predictive Modeling of High-Altitude Clear Air Turbulence in the United States: A Machine Learning Approach},
  author={Gökdeniz, Kadir and Ülkü, İrem},
  journal={Under Review},
  year={2024}
}
```

## 📧 Contact

**Kadir Gökdeniz**  
Email: kadirgokdeniz@hotmail.com  
LinkedIn: [linkedin.com/in/kadirgokdeniz](https://linkedin.com/in/kadirgokdeniz)  
GitHub: [github.com/KadirGokdeniz](https://github.com/KadirGokdeniz)

## 🙏 Acknowledgments
- This research was supported by the Presidency of Defence Industries of the Republic of Turkey under the SAYZEK-ATP program
- EUROCONTROL for providing access to the BADA dataset
- Technical mentorship from Tolga Baştürk