<div align="center">


# A Geospatial Framework for Urban Heat Mitigation through Corridor Optimization and Targeted Interventions

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![GeoPandas](https://img.shields.io/badge/GeoPandas-139C5A?style=for-the-badge&logo=pandas&logoColor=white)](https://geopandas.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

*A data-driven decision-support system for identifying thermally comfortable urban corridors and recommending climate-responsive interventions*

</div>

---

This repository contains the implementation of a geospatial decision-support system that identifies thermally comfortable corridors in urban areas and recommends targeted interventions (like tree plantation and cool roof installations) to mitigate heat island effects. The framework integrates satellite-derived indicators such as Land Surface Temperature (LST), NDVI, NDBI, and wind data to compute a composite “coolness” score and optimize routing for walking/cycling.

## Project Overview

Urban areas face intensified thermal stress due to rapid land-use changes and increased impervious surfaces. This system proposes a scalable, data-driven method to:

- Evaluate thermal comfort at street level
- Identify "cool corridors" for non-motorized transport
- Recommend climate-responsive urban interventions
- Visualize spatial heat distribution and post-intervention impact

---

## Core Features

- **Coolness Score Estimation**: Weighted index based on normalized LST, NDVI, NDBI, and Wind Speed.
- **Corridor Optimization**: Uses NetworkX to find least-heat-exposed routes in road graphs.
- **Intervention Simulation**: Simulates the impact of greening (NDVI ↑) and reflective surfaces (LST ↓).
- **Heat Island Identification**: Detects consistently hot urban segments for priority action.
- **Interactive Dashboard**: Visualizes raw data, routes, and intervention maps via a browser interface.

---

## Methodology

1. **Data Acquisition**
   - NDVI: Sentinel-2 (COPERNICUS/S2_SR_HARMONIZED)
   - LST: Landsat 8 (LANDSAT/LC08/C02/T1_L2)
   - NDBI: Derived from Sentinel-2 SWIR and NIR bands
   - Wind Speed: ERA5 or Open-Meteo API

2. **Coolness Score Calculation**

Coolness_e = 0.35 × (1 − norm_LST)
           + 0.35 × norm_NDVI
           + 0.15 × (1 − norm_NDBI)
           + 0.15 × norm_Wind

3. **Corridor Identification**
   - Constructs OSM-based road graph clipped to AOI
   - Weights edges with coolness scores
   - Finds shortest/coolest paths using Dijkstra/A\*

4. **Intervention Modeling**
   - Modifies NDVI/LST/NDBI for top-N low-score segments
   - Recomputes scores to simulate effect of green or reflective interventions

5. **Visualization**
   - Built with Streamlit and Plotly
   - Layers include raw rasters, heat maps, optimal paths, and intervention zones

---



