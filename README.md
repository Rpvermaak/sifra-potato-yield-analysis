# The Sifra Paradox: Multi-Site Potato Yield Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Rpvermaak/sifra-potato-yield-analysis/blob/main/notebooks/Notebook_B_Comparative_Analysis_%26_Modeling.ipynb)
[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**A data-driven investigation into why Sifra potatoes failed in one season but excelled in the next.**

---

## Executive Summary

A commercial potato producer in South Africa's Soutpansberg region experienced puzzling yield results: **complete failure** with the Sifra variety in 2024, followed by **excellent performance** in 2025. This project uses satellite imagery and remote sensing data to uncover the environmental factors behind this "Sifra Paradox."

### Key Findings

| Finding | Evidence |
|---------|----------|
| **Location matters most** | The North farm (Rain Shadow) consistently outperforms the South farm (Mist Belt) across all years |
| **Humidity is the culprit** | The 2024 failure coincides with the mist season (June-July), supporting late blight as a factor |
| **Recovery shows better timing** | 2025 success shows more sustainable growth patterns, suggesting improved seasonal timing |

### Recommendations

1. **Prioritize North farm for Sifra** — Lower disease pressure from drier conditions
2. **Use disease-resistant varieties in South** — High humidity favors fungal diseases
3. **Implement fungicide protocols May-July** — Target the critical mist season window
4. **Monitor with satellite NDVI** — Early stress detection enables rapid intervention

---

## Project Context

### The Study Area

The Soutpansberg mountain range in Limpopo Province, South Africa creates two distinct micro-climates:

| Location | Climate Type | Characteristics |
|----------|--------------|-----------------|
| **South Farm** | Mist Belt | Higher humidity, cooler temperatures, frequent fog |
| **North Farm** | Rain Shadow | Drier conditions, warmer nights, more sunlight |

**Coordinates:**
- South Farm (Mist Belt): `-23.1148, 29.5100`
- North Farm (Rain Shadow): `-22.8111, 29.4217`

### The Question

> *Why did Sifra potatoes fail in 2024 but excel in 2025, despite similar management practices?*

---

## Data Sources & Methodology

This analysis reconstructs environmental conditions using freely available remote sensing data—no proprietary farm records required.

### Data Sources

| Source | Data Type | Parameters | Access |
|--------|-----------|------------|--------|
| **ESA Sentinel-2** | Satellite Imagery | NDVI (vegetation health) | [Google Earth Engine](https://earthengine.google.com/) |
| **NASA POWER** | Weather Reanalysis | Temperature, precipitation, humidity, solar radiation | [NASA POWER API](https://power.larc.nasa.gov/) |
| **SoilGrids** | Soil Properties | pH, nitrogen, clay content | [SoilGrids.org](https://soilgrids.org/) |

### Key Metrics Explained

#### NDVI (Normalized Difference Vegetation Index)

NDVI measures plant health using satellite imagery. It compares how plants reflect different wavelengths of light:

```
NDVI = (Near-Infrared − Red) / (Near-Infrared + Red)
```

| NDVI Value | Interpretation |
|------------|----------------|
| **> 0.6** | Healthy, dense canopy |
| **0.3 - 0.6** | Moderate vegetation |
| **< 0.3** | Sparse/stressed vegetation |

#### Why NDVI Works for Potato Monitoring

- Healthy potato leaves absorb red light for photosynthesis
- They reflect near-infrared light strongly
- A sudden NDVI drop indicates stress (disease, drought, or nutrient deficiency)

---

## How to Reproduce This Analysis

### Prerequisites

```bash
# Clone the repository
git clone https://github.com/Rpvermaak/sifra-potato-yield-analysis.git
cd sifra-potato-yield-analysis

# Install dependencies
pip install -r requirements.txt
```

### Required Packages

```
pandas>=1.5.0
matplotlib>=3.6.0
seaborn>=0.12.0
earthengine-api>=0.1.300
geemap>=0.20.0
```

### Data Collection Steps

1. **Satellite Data (NDVI)**
   - Authenticate with Google Earth Engine: `earthengine authenticate`  
   - Run `Notebook_A_Data_Acquisition_Multi-Site_Yield_Analysis.ipynb`
   - Define field boundaries using polygon coordinates
   - Extract Sentinel-2 NDVI time series for each field

2. **Weather Data**
   - Use NASA POWER API to fetch daily meteorological data
   - Parameters: T2M_MAX, T2M_MIN, PRECTOTCORR, RH2M, ALLSKY_SFC_SW_DWN
   - Date range: Match your satellite observations

3. **Analysis**
   - Run `Notebook_B_Comparative_Analysis_&_Modeling.ipynb`
   - All visualizations and statistics generate automatically

### Running the Notebooks

```bash
# Option 1: Jupyter Lab
jupyter lab notebooks/

# Option 2: VS Code
code notebooks/Notebook_B_Comparative_Analysis_&_Modeling.ipynb

# Option 3: Google Colab (click the badge at top of notebook)
```

---

## Project Structure

```
.
├── notebooks/
│   ├── Notebook_A_Data_Acquisition_Multi-Site_Yield_Analysis.ipynb
│   ├── Notebook_B_Comparative_Analysis_&_Modeling.ipynb
│   ├── outputs/
│   │   └── Data sets/
│   │       ├── final_master_potato_dataset.csv
│   │       ├── northern_potato_fields.csv
│   │       └── southern_potato_fields.csv
│   └── images/
│       ├── Southern_fields_2025.png
│       └── Northen_fields_label_2025.png
│
├── README.md
├── requirements.txt
└── LICENSE
```

---

## Key Visualizations

### Year-over-Year NDVI Comparison

The main analysis compares NDVI (crop health) across three years:

- **Blue (2023)**: Baseline year
- **Orange (2024)**: The "failure" year — note the boom-bust pattern
- **Green (2025)**: The "recovery" year — more sustainable growth

The charts reveal that **2024's failure followed a classic disease pattern**: rapid early growth, then collapse during the humid mist season (June).

### What the Data Shows

| Observation | South Farm | North Farm |
|-------------|------------|------------|
| **2024 Pattern** | Sharp peak then crash | High peak, moderate decline |
| **2025 Pattern** | Lower but sustained | Consistent healthy range |
| **Best Performance** | 2025 | 2024 (ironically) |

---

## Conclusions

### Answering "The Sifra Paradox"

The analysis reveals that **location matters more than seasonal variation**:

1. **The North Farm (Rain Shadow) is better suited for Sifra potatoes** due to lower humidity and reduced disease pressure.

2. **The 2024 "failure" in the South was likely caused by late blight** during the mist season (June-July), when humidity peaks.

3. **The 2025 "recovery" shows improved timing** — crops avoided the worst of the mist window or received better disease management.

### Implications for Precision Agriculture

This project demonstrates how **free satellite data can provide actionable farm insights**:

- No expensive sensors required
- Weekly monitoring possible with Sentinel-2 (5-day revisit)
- Early stress detection enables timely intervention
- Historical analysis reveals patterns invisible to ground observation

---

## Future Work

- [ ] Integrate actual yield data to validate NDVI correlations
- [ ] Add Growing Degree Days (GDD) analysis for planting optimization
- [ ] Build automated early warning system for NDVI drops
- [ ] Expand to other potato varieties and crops

---

## Author

**Ruben Vermaak**  
Data Analyst | Agricultural Technology

- GitHub: [@Rpvermaak](https://github.com/Rpvermaak)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- **ESA Copernicus Programme** for Sentinel-2 open data
- **NASA POWER** for accessible weather reanalysis
- **Google Earth Engine** for cloud-based geospatial processing

---

*Last updated: February 2026*
