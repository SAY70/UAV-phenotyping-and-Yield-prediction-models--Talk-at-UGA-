# 🌱 UAV Phenotyping & Yield Prediction using Vegetation Indices and GeoAI

This repository presents an end-to-end pipeline for **UAV-based crop phenotyping**, integrating remote sensing, feature engineering, and machine learning for yield prediction.

---

## 🚀 Overview

The workflow includes:

- Multispectral image stacking (B, G, R, RedEdge, NIR)
- AOI extraction using shapefiles
- RGB visualization with percentile stretching
- NDVI computation and soil masking
- Vegetation indices generation
- Subplot-level feature extraction
- Feature ranking using PLSR (VIP scores)
- Yield prediction using ML and DL models

---

## 📂 Project Structure
├── Code/
│ ├── Loading mosaics and visualizing.ipynb
│ ├── Remove soil pixel.ipynb
│ ├── Feature extraction.ipynb
│ ├── Feature Engineering.ipynb
│ ├── Yield Prediction Model.ipynb
│
├── Data/
│ ├── raw/
│ ├── stack/
│ ├── shapefiles/
│ ├── Vegetation_Indices_Output/
│
├── Results/
│ ├── NDVI_output/
│ ├── Model_Results/
│
├── README.md


---

## 🛰️ 1. Multispectral Band Stacking

Input bands:
- Blue (B)
- Green (G)
- Red (R)
- Red Edge (RE)
- Near Infrared (NIR)

Output:
- 5-band stacked GeoTIFF

---

## 🎨 2. Visualization

RGB composite:
- R = band 3  
- G = band 2  
- B = band 1  

Includes percentile stretching (2–98%) for better visualization.

---

## 🧭 3. AOI Selection (GUI)

Interactive GUI enables:
- Raster loading
- Rectangle/polygon selection
- Shapefile export
- Raster cropping

---

## 🌿 4. NDVI & Soil Removal

NDVI formula: NDVI = (NIR - Red) / (NIR + Red)


- Invalid pixels are masked
- Soil removal using threshold:


---

## 📊 5. Vegetation Indices

Computed indices include:

- NDVI, GNDVI, DVI  
- EVI, EVI2  
- SAVI, MSAVI, OSAVI  
- CHLRE, CHLGR  
- MCARI, MCARI/OSAVI  
- SR, WDRI, PVI  
- MARI, TSAVI  

---

## 📐 6. Subplot-Level Feature Extraction

- Input: shapefile polygons  
- Output: statistics per subplot:

  - Mean  
  - Median  
  - Min / Max  
  - Standard deviation  

Saved as multi-sheet Excel (one sheet per index).

---

## 🧠 7. Feature Engineering

- Selection of specific locations
- Merging indices into a single dataset
- Cleaning variable names (removing `masked_` prefix)

---

## 🔬 8. Feature Ranking (PLSR)

- Model: Partial Least Squares Regression  
- Metric: VIP (Variable Importance in Projection)

Interpretation:
- VIP > 1 → important feature  
- VIP < 1 → less important  

---

## 🤖 9. Yield Prediction Models

Using top-ranked VIP features:

Models used:
- SVR (Support Vector Regression)
- Random Forest
- Extra Trees
- Gradient Boosting
- AdaBoost
- KNN
- PLSR
- MLP (Neural Network)
- XGBoost (optional)

---

## 📈 10. Model Evaluation

Metrics:
- R (Pearson correlation)
- RMSE
- MAE
- Bias

Cross-validation:
- 5-fold KFold

---

## 📊 Outputs

- Vegetation index rasters  
- NDVI maps (with CRS)  
- Subplot-level Excel tables  
- VIP ranking results  
- Model performance comparison  
- Feature importance plots  
- Observed vs predicted yield plots  

---

## ⚙️ Requirements

Install dependencies:

```bash
pip install numpy pandas matplotlib rasterio geopandas scikit-learn xgboost openpyxl

## ⚙️ Large Data Handling

Large files are managed using Git LFS:
git lfs track "*.tif" "*.las" "*.xlsx"

## 📌 Notes

- Ensure CRS consistency between raster and shapefile  
- NDVI threshold may vary by crop and growth stage  
- Deep learning models require sufficient data  

---

## 🔬 Applications

- Precision agriculture  
- Nitrogen management  
- Yield prediction  
- Crop health monitoring  
- UAV phenotyping  

---

## 👨‍🔬 Author

**Dr. Sura Yadav**  
Postdoctoral Researcher  
Mississippi State University  

---

## 📬 Contact

For collaboration or questions, feel free to reach out.

---

## 🚀 Future Work

- Physics-informed AI models  
- Multi-temporal analysis  
- Integration with LiDAR and hyperspectral data  
- Edge AI deployment on UAV platforms  

---

## ⭐ Acknowledgment

This work integrates UAV remote sensing, radiative transfer modeling, and AI for advanced agricultural analytics.
