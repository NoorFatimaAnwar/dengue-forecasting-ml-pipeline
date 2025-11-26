# 🧠 Student Academic Score Prediction -> Statistical Edition

## 📘 Project Overview
This project explores how different lifestyle factors — including **sleep**, **exercise**, **social media use**, and **study habits** — influence students’ **academic performance**.  
The updated version enhances the analysis by integrating **statistical testing methods** and **distribution checks** to validate findings scientifically.

---

## 🎯 Objective
Analyze how lifestyle choices impact academic outcomes and identify which factors are statistically significant contributors to academic success.

---

## 📊 Dataset Description
The dataset (`students_lifestyle_5000.csv`) contains 5000 student records, including:

**Numerical Columns:**  
Study_Hours_Per_Day, Sleep_Hours, Screen_Time_Hours, Physical_Activity_Hours, Social_Activity_Score, Mental_Wellbeing_Score, Attendance_Rate, Academic_Score, Age  

**Categorical Columns:**  
Gender, Stress_Level

---

## 🔍 Project Workflow

### 1. Initial Exploration
- Loaded and visualized raw data distributions.  
- Identified missing values, outliers, and inconsistent category names.  
- Explored gender and stress level distributions.  

### 2. Data Cleaning
- Used **KNN Imputer** for numerical columns with >5% missing values.  
- Replaced missing categorical values (e.g., Stress_Level) using **mode imputation**.  
- Standardized categorical entries (e.g., gender variants: “fmmale” → “female”).  
- Removed and capped outliers using **IQR method** and **z-score analysis**.  

### 3. Statistical Enhancements (New Section 🧮)
This version adds **inferential statistics** to strengthen EDA insights.

#### 📏 Normality & Distribution Analysis
- **Shapiro-Wilk Test:** Checked if numerical columns follow normal distribution.  
- **Skewness & Kurtosis:** Measured shape of data distribution.  
- Found most variables approximately normal (|skew| < 0.5), suitable for parametric tests.  

#### 📊 Outlier Detection
- Applied **z-score method** to quantify outliers across multiple columns.  
- Outliers > 3σ were replaced or capped at upper whiskers.  

#### 🧠 Hypothesis Testing
- **ANOVA (f_oneway):**  
  Tested if mean Academic_Score differs across **genders** and **stress levels**.  
  Found p < 0.05 → Significant differences exist between groups.  

- **Pearson Correlation:**  
  Used for normally distributed variables (Study_Hours, Sleep_Hours, etc.).  
  Revealed **Study_Hours_Per_Day** has the strongest positive correlation with Academic_Score.  

- **Spearman Correlation:**  
  Used for non-normal variables (Physical_Activity_Hours).  
  Showed no significant relationship with Academic_Score.  

- **F-test (f_regression):**  
  Validated relationship strength between categorical encodings (Stress_Level) and target variable.  

#### 📈 Insights
- Study hours and attendance rate show significant positive influence on academic score.  
- Sleep and mental wellbeing have mild positive effects.  
- Physical activity and screen time show negligible impact.  
- Stress level and gender influence academic outcomes significantly.  

---

## 📊 EDA Highlights
- No major skew after cleaning.  
- Heatmaps, scatterplots, and violin plots illustrate weak to moderate relationships.  
- Correlation matrix confirms **Study_Hours_Per_Day ↔ Academic_Score (r ≈ 0.78)** as the strongest association.  

---

## ⚙️ Feature Engineering
- **Encoding:** Converted Gender and Stress_Level into dummy variables.  
- **Scaling:** Applied **StandardScaler** to normalize numerical columns.  
- **Train-Test Split:** 80-20 ratio for modeling readiness.  

---

## 📈 Key Learnings
- Statistical validation adds reliability to EDA.  
- ANOVA and correlation tests reveal hidden relationships beyond visual inspection.  
- Outlier and normality checks ensure accurate, unbiased analysis.  

---

## 🧩 Technologies Used
- **Python Libraries:** pandas, numpy, matplotlib, seaborn, scipy, sklearn  
- **Statistical Methods:** ANOVA, Shapiro-Wilk, Pearson, Spearman, z-score, skewness, kurtosis  
- **Tools:** Google Colab  

---

## 🧠 Conclusion
The statistical version of this project provides a more rigorous understanding of how students’ habits affect academic outcomes.  
While study hours and attendance have the strongest positive impact, lifestyle balance (adequate sleep and moderate stress) remains essential for optimal performance.  

---

## 📁 Folder Structure

Student_Lifestyle_Analysis/

├── Academic_Score_Prediction_Statistical_Version/

    ├── students_lifestyle_5000.csv

    ├── Academic_Score_statists.ipynb

    ├── README.md   

└── Student_Academic_Score_Analysis/

    ├── students_lifestyle_5000.csv
    
    ├── Academic_Score_EDA.ipynb
    
    ├── README.md

# Run the Jupyter/Colab notebook
Academic_Score_Statists.ipynb

---
## 👩‍💻 Author

**Noor Fatima**  
🎓 *Computer Science Student* | 💡 *Data Science Enthusiast*  
📍 *Pakistan* 
