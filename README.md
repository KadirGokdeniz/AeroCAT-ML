# CAT-Predictor-ML: High-Altitude Clear Air Turbulence Forecasting

[![AUC Score](https://img.shields.io/badge/AUC-0.904-success)](https://github.com/KadirGokdeniz/CAT-Predictor-ML)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)

## Overview

Machine learning framework for predicting high-altitude Clear Air Turbulence (CAT) with 90.4% AUC accuracy. Integrates meteorological data, pilot reports, and aircraft aerodynamics to provide operational turbulence forecasts for aviation safety.

## Problem Statement

Clear Air Turbulence is a critical aviation challenge:
- Responsible for 71% of weather-related aircraft accidents
- $100-200M annual economic impact in the US
- Invisible to pilots and radar systems
- Increasing frequency due to climate change

## Key Features

- 86.6% POD for moderate-to-severe turbulence detection
- Multi-source integration: ERA5 reanalysis + PIREPs + BADA aerodynamics
- Aircraft-specific modeling accounting for different aircraft responses
- Spatiotemporal pattern recognition for flight planning optimization

## Performance Metrics

| Model | Dataset | AUC | POD | FAR | CSI |
|-------|---------|-----|-----|-----|-----|
| XGBoost+Aero | All Categories | **0.904** | **0.809** | 0.158 | **0.703** |
| XGBoost+Aero | MOD-SEV Only | **0.928** | **0.866** | 0.150 | **0.753** |
| LightGBM+Aero | All Categories | 0.902 | 0.815 | 0.166 | 0.701 |

## Dataset

- **Period**: 2022-2024
- **Region**: US Airspace (24°N-50°N, -125°E to -67°E)
- **Altitude**: 200-350 hPa (~30,000-43,000 ft)
- **Cases**: 38,426 balanced samples
- **Resolution**: 0.25° spatial, 1-hour temporal

### Data Sources

**ERA5 Reanalysis**: ECMWF meteorological data  
**PIREPs**: Iowa Environmental Mesonet pilot reports  
**BADA**: EUROCONTROL aircraft performance parameters

## Methodology

### Turbulence Diagnostics (14 parameters)
TI2, TI3, Richardson number, Brunt-Väisälä frequency, vertical wind shear, horizontal divergence, potential vorticity gradient, relative vorticity squared, divergence tendency, Dutton index, temperature gradient, potential temperature, wind speed

### Aerodynamic Parameters
Maximum lift force, load factor, drag force, lift-to-drag ratio, aspect ratio, wing loading

### Machine Learning
- Algorithms: XGBoost, LightGBM, Random Forest, AdaBoost
- 5-fold cross-validation, 70/30 train-test split
- Grid search + Bayesian optimization

## Key Findings

### Feature Importance
1. Longitude (11.0%) and Latitude (9.2%) - geographic influence
2. TI3 Index (7.8%) - atmospheric instability
3. Dutton Index (7.8%) - vertical wind shear
4. Drag Force (3.2%) - top aerodynamic parameter

### Temporal Patterns
- **Winter peak**: ~1,100 MOD CAT incidents (Dec-Feb)
- **Evening maximum**: 15:00-21:00 UTC (3.5× higher frequency)

### Geographic Hotspots
Southwest US, South-Central region, Eastern Seaboard, Northeast corridor

### Aerodynamic Impact
- POD improved from 0.845 to 0.866 for MOD-SEV (2.5% increase)
- 12% reduction in false negatives for severe turbulence

## Citation

```bibtex
@article{gokdeniz2025cat,
  title={Predictive Modeling of High-Altitude Clear Air Turbulence: 
         A Machine Learning Approach},
  author={Gökdeniz, Kadir and Ülkü, İrem},
  journal={Under Review},
  year={2025}
}
```

## Contributing

Priority areas: global data integration, real-time telemetry, deep learning approaches, operational deployment

## Acknowledgments

Supported by the Presidency of Defence Industries of Turkey (SAYZEK-ATP program) and EUROCONTROL (BADA database access)

## Contact

**Kadir Gökdeniz**  
Email: kadirgokdeniz@hotmail.com  
LinkedIn: [linkedin.com/in/kadirgokdeniz](https://www.linkedin.com/in/kadir-g%C3%B6kdeniz-16573127a/)  
GitHub: [github.com/KadirGokdeniz](https://github.com/KadirGokdeniz)

## License

MIT License - See LICENSE file for details
