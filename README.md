# 🌡️ Dengue Fever Prediction – Machine Learning Project

Predicting weekly dengue cases for **San Juan (SJ)** and **Iquitos (IQ)** using climate, weather, and vegetation data.

---

## 📌 Project Overview
This project aims to forecast total weekly dengue cases for the two cities participating in the DrivenData challenge:

- **San Juan (SJ)**
- **Iquitos (IQ)**

The task is a **regression problem**, where the goal is to predict `total_cases` for each `(city, year, weekofyear)` in the test dataset.  

The project includes:
- ✅ Data cleaning and preprocessing
- ✅ Missing value imputation
- ✅ Feature renaming and transformation
- ✅ Custom train-validation split
- ✅ Model training & performance evaluation
- ✅ Ready-to-use cleaned datasets (`train_df.csv`, `test_df.csv`)

---

## 📁 Repository Structure


dengue-forcasting-ml-pipeline/

├── data/ 

│ ├── data_source/ # original dataset link

├── notebooks/ # all  Jupyter notebooks

│ ├── 01_handle_missing_values.ipynb

│ ├── 02_model_training_and_evaluation.ipynb

├── reports/ # markdown reports for each step

│ ├── version_01_missing_values.md

└── README.md


---

## 📊 Problem Description
The goal is to build a model that predicts:

`total_cases` (integer)

for each record in the test file.  

The test data is a **future hold-out**, meaning it does not overlap with training data in time. Each row represents a specific week in a specific city:

- `city` (sj or iq)
- `year`
- `weekofyear`

The dataset combines features from:

### 1️⃣ Weather Station (GHCN)
- `station_max_temp_c`
- `station_min_temp_c`
- `station_avg_temp_c`
- `station_precip_mm`
- `station_diur_temp_rng_c`

### 2️⃣ PERSIANN Satellite Precipitation
- `precipitation_amt_mm`

### 3️⃣ Reanalysis (NCEP CFSR)
- `reanalysis_air_temp_k`
- `reanalysis_dew_point_temp_k`
- `reanalysis_relative_humidity_percent`
- `reanalysis_specific_humidity_g_per_kg`
- `reanalysis_precip_amt_kg_per_m2`
- `reanalysis_max_air_temp_k`
- `reanalysis_min_air_temp_k`
- `reanalysis_avg_temp_k`
- `reanalysis_tdtr_k`
- `reanalysis_sat_precip_amt_mm`

### 4️⃣ NDVI – Vegetation Index
- `ndvi_ne`
- `ndvi_nw`
- `ndvi_se`
- `ndvi_sw`

---

## ✨ Preprocessing Steps
All preprocessing is performed inside `01_missing_values.ipynb`.

### 1. Renaming Features
Columns were renamed to more readable names such as:
- `ndvi_ne` → `vegetation_ne`
- `precipitation_amt_mm` → `satellite_precip_mm`


### 2. Handling Missing Values
Different strategies were applied based on feature type:

- **Random Imputation**  
  For NDVI vegetation features (small missing %, low correlation).

- **KNN Imputation**  
  For precipitation data (`satellite_precip_mm`).

- **Median Imputation**  
  For skewed climate features (humidity, dew point, temperature).

*KDE plots were used to compare before vs after imputation.*

### 3. City Encoding
- `sj` → 0  
- `iq` → 1

### 4. Exporting Cleaned Data
Saved as:
- `train_df.csv`
- `test_df.csv`

---

## 🤖 Model Training & Evaluation
Performed in `02_model_training.ipynb`.

### Train/Validation Split
Because the test set has no labels, a **middle 20% split** was created:
- First part → training
- Middle 20% → validation
- Remaining → training

This preserves time-series order.

### Models Tested
- Linear Regression
- Random Forest
- Gradient Boosting
- KNN Regressor
- Support Vector Regressor (SVR)

### Metrics
- MAE
- RMSE
- R² Score


### 🎯 Performance Metric
The model is evaluated using **Mean Absolute Error (MAE)**.

---

## 🚀 How to Run This Project
1. Upload raw dataset into Colab
2. Run `01_missing_values.ipynb`  
   This will generate:
   - `train_df.csv`
   - `test_df.csv`
3. Upload the generated files and run `02_model_training.ipynb`

---

## 📌 Future Improvements
- Outliers removal
- Scaling features
- Hyperparameter tuning
- Adding time-lag features
- Ensembling models

---

## 📬 Author
**Noor Fatima**  
Aspiring Data Scientist






