# 📄 Version 01 – Missing Value Handling & Baseline Model Evaluation

## 1. Overview
This version focuses on:

- Merging training features and labels  
- Renaming climate-related variables for clarity  
- Handling missing values using multiple imputation strategies  
- Generating KDE plots to compare data distributions before & after imputation  
- Preparing cleaned datasets (`train_df.csv` and `test_df.csv`)  
- Training baseline models for initial performance evaluation  

This serves as the **baseline version** for future improvements  

---

## 2. Data Preparation Steps

### 2.1 Dataset Loading & Merging
- Training features and labels were merged using:
  - `city`, `year`, `weekofyear`
- Test dataset was kept separate.

### 2.2 Column Renaming
Technical variable names were replaced with meaningful names.

**Examples:**
| Old Name | New Name |
|----------|----------|
| `ndvi_ne` | `vegetation_ne` |
| `precipitation_amt_mm` | `satellite_precip_mm` |

Renaming improves clarity for analysis and modeling.

---

## 3. Missing Value Handling

Different imputation strategies were applied based on:

- Data type  
- Distribution (normal / skewed)  
- Missing value percentage  
- Correlation patterns  

---

### 3.1 Random Imputation (Low-missing NDVI features)
Applied to:

- `vegetation_ne`, `vegetation_nw`, `vegetation_se`, `vegetation_sw`

**Why this method?**

- Missing values < 5%
- Weak correlation with target
- Random sampling preserves natural distribution  
- KDE plots show similar distributions before/after imputation

---

### 3.2 KNN Imputation (MAR-Type Feature)
Applied to:

- `satellite_precip_mm`

**Reasoning:**

- Feature influenced by multiple climate variables → MAR  
- KNN preserves local relationships  
- Both train and test imputed using:

```python
KNNImputer(n_neighbors=5)
```

### 3.3 Median Imputation (Skewed Climate Variables)

**Applied to:**

- air_temp_k, avg_temp_k, dew_point_k, max_air_temp_k, min_air_temp_k,
- precip_kg_per_m2, humidity_percent, temp_range_k, specific_humidity

**Why median imputation?**

- Distributions are skewed  
- Median is resistant to outliers  
- Ensures stable performance for regression models  

---

### 3.4 Median Imputation for Reanalysis Precipitation

- `re_satellite_precip_mm` filled using median.

---

### 3.5 Weather Station Columns (Median Fill)

**Applied to:**

- station_avg_temp, station_temp_range,
- station_max_temp, station_min_temp, station_precip_mm


**Reason:**

- Skewed distributions  
- Consistency with other climate variables  

---

## 4. Encoding

### City Encoding

- sj → 0
- iq → 1

Numeric encoding improves model compatibility.

---

## 5. Dataset Export

After preprocessing, the following cleaned files were exported:

- `train_df.csv`
- `test_df.csv`

These datasets will be used in upcoming versions (outlier removal, scaling, feature engineering, etc.).

---

## 6. Baseline Model Training & Evaluation

A **middle 20% validation split** was used instead of a random split to avoid time leakage, as dengue cases often follow temporal patterns.

### Models tested:

- Linear Regression  
- Random Forest  
- Gradient Boosting  
- KNN Regressor  
- Support Vector Regressor (SVR)  

### Metrics calculated:

- **MAE** (Mean Absolute Error)  
- **RMSE** (Root Mean Squared Error)  
- **R² Score**  

These metrics serve as the baseline for evaluating future improvements.

---

## 7. Baseline Performance Summary

| Model | MAE | RMSE | R² Score |
|-------|-----|------|----------|
| Linear Regression | 23.978 | 28.189 | -0.641 |
| Random Forest | 19.901 | 30.349 | -0.902 |
| Gradient Boosting | 21.694 | 35.279 | -1.571 |
| KNN Regressor | 23.218 | 34.395 | -1.443 |
| SVR | 13.017 | 23.207 | -0.112 |

---

## 8. Key Insights of Version 01

✔️ Missing values fully handled for both train and test  
✔️ Imputation strategies tailored to feature type & distribution  
✔️ Cleaned datasets prepared for next preprocessing steps  
✔️ Baseline model metrics established  
✔️ Future versions will be compared against this baseline  

---

## 9. Next Steps – Version 02 Preview

In **Version 02**, the following tasks will be performed:

- Detecting and removing outliers  
- Re-plotting feature distributions  
- Retraining models  
- Comparing new performance metrics with Version 01  

This will help measure improvements gained through outlier removal.

---

