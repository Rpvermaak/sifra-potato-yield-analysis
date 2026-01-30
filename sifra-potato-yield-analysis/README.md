# The Sifra Paradox: Solving Yield Volatility in Limpopo
![Project Header](visuals/header_map.png)

## 🛠️ The Business Case
A commercial producer in the Soutpansberg mountains experienced a 60% yield variance in Sifra potatoes over two seasons. This project uses **Remote Sensing (Sentinel-2)** and **Meteorological Reanalysis (NASA POWER)** to decode the environmental triggers behind this volatility.

### The "Natural Experiment"
- **Site A (South):** High-altitude mist belt (High humidity, low solar radiation).
- **Site B (North):** Rain shadow arid zone (High heat, high solar radiation).

## 📊 Key Findings (Preview)
* **The Blight Window:** Identified a 14-day high-humidity event in Season 1 that correlated with a 40% drop in NDVI.
* **Nitrogen Sensitivity:** Cross-referenced HZPC specs to show that over-fertilization likely exacerbated foliage growth during low-light periods.

## 🚀 Tech Stack
- **Languages:** Python (Pandas, GeoPandas)
- **Data Sourcing:** NASA POWER API, Google Earth Engine
- **Calculations:** NDVI (Normalized Difference Vegetation Index), GDD (Growing Degree Days)
- **Deployment:** Streamlit (Proposed Dashboard)

## 📚 Data Sources & References
| Source | Type | Utility |
| :--- | :--- | :--- |
| **HZPC Holland** | [Cultivar Profile](https://www.hzpc.com/our-potato-varieties/sifra) | Verified low-nitrogen requirements. |
| **Potatoes SA** | [Limpopo Trial 2024](https://www.potatoes.co.za/limpopo-cultivar-trial-2024/) | Local yield benchmarks for Sifra. |
| **ESA Sentinel-2** | Satellite Imagery | High-res (10m) vegetation health monitoring. |
| **NASA POWER** | Weather API | Historical daily temperature and rainfall. |

## 📂 Project Structure
* `notebooks/`: Contains the end-to-end EDA and model building.
* `src/`: Python modules for reusable data ingestion logic.

---

# Sifra Potato Yield Analysis

## Overview
The Sifra Potato Yield Analysis project aims to analyze potato yield data using NASA/Sentinel satellite imagery and other relevant datasets. This project will leverage various data processing techniques and visualizations to gain insights into potato cultivation and yield patterns.

## Project Structure
The project is organized into the following directories and files:

- **data/**: Contains instructions on how to pull NASA/Sentinel data. Raw data files are not included in this repository.
  
- **notebooks/**: This folder is designated for Google Colab or Jupyter notebooks, referred to as "The Discovery." It will contain exploratory data analysis and visualizations.

- **src/**: Holds modular Python scripts (.py files) for API calls and data processing. This is where the core functionality of the project is implemented.

- **visuals/**: Intended for exported charts, maps, and the project logo. It will store all visual outputs generated during the analysis.

- **references/**: Contains PDF research papers and cultivar profiles relevant to the project, serving as a repository for the literature review.

- **requirements.txt**: Lists the libraries required for the project, such as pandas, geemap, and any other dependencies needed for the scripts to run.

## Setup Instructions
1. Clone the repository:
   ```
   git clone <repository-url>
   cd sifra-potato-yield-analysis
   ```

2. Install the required libraries:
   ```
   pip install -r requirements.txt
   ```

3. Follow the instructions in the `data/` folder to pull the necessary NASA/Sentinel data.

4. Explore the notebooks in the `notebooks/` folder for data analysis and visualization.

## Usage
- Use the scripts in the `src/` folder to process data and perform analyses.
- Visual outputs can be found in the `visuals/` folder.
- Refer to the `references/` folder for supporting literature.

## Contributing
Contributions are welcome! Please submit a pull request or open an issue for any suggestions or improvements.