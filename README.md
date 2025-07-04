# Land Use / Land Cover (LULC) Classification for Murang’a, Kenya (2024–2025)

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]()
[![Earth Observation](https://img.shields.io/badge/Data-Sentinel--1%20%2F%20Sentinel--2-blue)](https://www.copernicus.eu/en)

This repository contains code and documentation for a supervised machine learning-based **Land Use / Land Cover (LULC) classification** project conducted for **Murang’a County, Kenya** using **Sentinel-1 SAR** and **Sentinel-2 optical** imagery between **December 2024 and January 2025**.

> Final Accuracy: **94.89% (XGBoost)**, **94.81% (Random Forest)**  
> Classes: Water, Trees, Cropland, Built-up, Bareland, Grasslands  
> Tools: Python, Rasterio, Scikit-learn, XGBoost, ArcGIS Pro, GEE

---

## Project Structure

```bash
├── Land_Use_Land_Cover_Analysis_For_Murang'a_2024_12_to_2025_1.ipynb  # Core Jupyter Notebook
├── report on LULC.pdf                                                 # Full technical report
├── /data                                                              # Folder for imagery and training data
├── /models                                                            # Trained models (RF & XGBoost)
├── /outputs                                                           # Classified rasters and filtered outputs
└── README.md
```

 
---

## Data Sources

| Source        | Description                                        |
|---------------|----------------------------------------------------|
| **Sentinel-2** | Surface reflectance bands (B2–B11), <5% cloud      |
| **Sentinel-1** | VV/VH dual-polarized backscatter (dB + VV/VH)     |
| **DEM**        | SRTM terrain data for topographic correction       |
| **Field Samples** | 8,601 labeled points for six land cover classes |

Derived indices include: `NDVI`, `MSAVI`, `GCI`, `NPCI`, `GNDVI`.

---

## Model Training

**Models Trained:**

- **Random Forest (RF)**  
- **XGBoost**

**Training Configuration:**

- Stratified sampling: **70% training / 30% testing**  
- Feature scaling: **StandardScaler**

### Key Accuracy Metrics

| Class       | Precision | Recall | F1-score |
|-------------|-----------|--------|----------|
| **Water**     | 0.98      | 1.00   | 0.99     |
| **Trees**     | 0.95      | 0.96   | 0.96     |
| **Cropland**  | 0.96      | 0.94   | 0.95     |
| **Built-up**  | 0.94–0.95 | 0.92–0.94 | 0.93–0.94 |
| **Bareland**  | 0.92–0.94 | 0.97   | 0.94–0.95 |
| **Grasslands**| 0.94–0.96 | 0.85–0.89 | 0.90–0.91 |

---

## Methodology Overview

### 1. Data Acquisition  
- Source: **Google Earth Engine (GEE)**  

### 2. Preprocessing  
- Cloud masking using QA60  
- Bilinear interpolation  
- Terrain correction (gamma⁰ normalization)  

### 3. Feature Engineering  
- 13 total features: spectral bands, SAR bands, vegetation indices  

### 4. Model Training  
- Stratified sampling  
- Models: **Random Forest** and **XGBoost**

### 5. Prediction  
- Tiled inference (256x256 px tiles)  
- Memory optimization with smart tile handling  

### 6. Post-Processing  
- **Majority filter** (3×3 kernel) to reduce noise  

---

## LULC Statistics (Murang’a 2024)

| Land Cover  | Area (ha)   | Percentage (%) |
|-------------|-------------|----------------|
| **Trees**       | 136,632.57  | 56.41%         |
| **Cropland**    | 71,384.12   | 29.47%         |
| **Bare Ground** | 26,378.49   | 10.89%         |
| **Built-up**    | 5,709.85    | 2.36%          |
| **Grasslands**  | 1,500.99    | 0.62%          |
| **Water**       | 601.30      | 0.25%          |

---
---

## License

This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for full details.

---

## Acknowledgments

Special thanks to the following organizations and tools that made this project possible:

- [Copernicus Sentinel Program (ESA)](https://www.copernicus.eu/en)
- [Google Earth Engine](https://earthengine.google.com/)
- [Kenya Space Agency](https://ksa.go.ke/)
- [Scikit-learn](https://scikit-learn.org/)
- [XGBoost](https://xgboost.readthedocs.io/)
- [Rasterio](https://rasterio.readthedocs.io/)
-  [GDAL](https://gdal.org/)

---

