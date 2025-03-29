# Predictive Causes of Death in Europe (1994-2010)

## 🔎 Project Overview
This project investigates factors influencing standardized death rates across European countries from 1994 to 2010. We analyze demographic variables, geographic regions, time trends, and causes of death to identify significant predictors of mortality patterns.

---

## ❓ Research Question
> "What factors influence standardized death rates across European countries from 1994 to 2010?"

---

## 📑 Table of Contents
[📚 Dependencies](#dependencies) <br>
[🧹 Data Preparation (EDA)](#---data-preparation--eda-) <br>
[🧮 Modeling](#---modeling) <br>
[💡 Key Findings](#---key-findings) <br>
[📉 Visualizations](#---visualizations) <br>
[🔍 Conclusions](#---conclusions) <br>
[🔮 Future Work](#---future-work) <br>
[📜 License](#---license) <br>
[👥 Contributors](#---contributors) <br>

---

## 🛠 Tools and Technologies
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=matplotlib&logoColor=white)
![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

---

## 📚 Dependencies
The project relies on the following libraries:
```python
# Get rid of warnings
import warnings
warnings.filterwarnings('ignore')

# Import libraries for general use
import numpy as np
import pandas as pd # data processing
import seaborn as sns
import matplotlib.pyplot as plt
import plotly.express as px

# Import libraries for machine learning models
""" For regression models """
import statsmodels.formula.api as smf

""" For random forest regression """
from sklearn.ensemble import RandomForestRegressor as RFR
from sklearn.metrics import mean_squared_error, r2_score # metrics for RFR

""" For random forests """
from sklearn.ensemble import RandomForestClassifier as RF
from sklearn import ensemble

""" For performance testing of tree models """
from sklearn.model_selection import train_test_split # data sampling
from sklearn.metrics import accuracy_score # model accuracy check

""" For label encoding """
from sklearn.preprocessing import LabelEncoder
```

---

## 🧹 Data Preparation (EDA)
The data preparation process involved several key steps to ensure quality analysis:

### 1️⃣ Feature Selection
- Removed 5 redundant columns
- Retained key factors: age, sex, year, country, and death causes
- Renamed columns for clearer interpretation

### 2️⃣ Data Filtering
- Removed aggregated data entries (e.g., "TOTAL" in sex column, "T" in age column)
- Excluded EU-level aggregations ("EU27_2020" and "EU28" in country_code)
- Selected 17 representative disease groups rather than specific diseases

### 3️⃣ Missing Value Treatment
- Missing values constituted only 0.6% of the dataset, all in the "death_rate" column
- Imputed missing values with column means to preserve data patterns
- Verified no duplicate records existed

### 4️⃣ Feature Engineering
- Grouped countries into 4 European regions: North, South, East, West
- Applied categorical encoding techniques:
  - One-hot encoding for country regions
  - Label encoding for age and sex variables
- Transformed the year range (1994-2010) to ordinal values (1-17)

---
## 🧮 Modeling
We implemented two regression models to answer our research question:

### 📈 Multiple Linear Regression
Selected as our primary model for its interpretability and straightforward insights.

### 🌲 Random Forest Regression
Implemented to capture potential non-linear relationships between variables.

---
## 💡 Key Findings

### 📊 Multiple Regression Results
- **Model Significance**: The overall model is statistically significant (p < 0.05)
- **Significant Predictors**: Sex, age, year, European regions, and most causes of death
- **Model Fit**: Adjusted R² = 0.475 (explains approximately 48% of death rate variation)
- **Key Coefficients**:
  - Diseases of circulatory system ("I") strongly associated with high death rates (coef = 1528.33)
  - Age is a significant predictor, with higher death rates in older populations
  - Males show higher death rates compared to females (coef = 76.96)

### 🌳 Random Forest Regression Results
- **Superior Model Fit**: R² = 0.945 (explains approximately 95% of death rate variation)
- **Model Comparison**: The substantial improvement in fit suggests significant non-linear relationships in the data
- Feature Importance: Age, circulatory system diseases (I), malignant neoplasms (C), etc. <br>
![Screenshot 2025-03-29 at 16 50 58](https://github.com/user-attachments/assets/5265eaa6-456e-4ccd-8767-4045216433ef)

---
## 📉 Visualizations

### 🗺️ Regional Death Rate Trends (1994-2010) <br>
![Screenshot 2025-03-29 at 16 55 32](https://github.com/user-attachments/assets/170b65ec-d40b-4256-bc6b-0fe5b3a76052)

- **Eastern Europe**: Showed increasing trends, maintaining the highest rates throughout
- **Northern Europe**: Consistently maintained the lowest death rates
- **Western & Southern Europe**: Demonstrated immediate trends

### 🩺 Death Causes Analysis <br>
![Screenshot 2025-03-29 at 16 57 29](https://github.com/user-attachments/assets/2f638072-adfd-43e2-9a48-005a3a2c0b0d)

- **Circulatory System Diseases (I)**: Highest mortality factor, significantly exceeding all others
- **Malignant Neoplasms (C)**: Second highest contributor with approximately 1.3M deaths
- **Other Causes**: Substantially lower mortality rates

---
## 🔍 Conclusions
Our analysis reveals that demographic factors (age, sex), geographic location (European region), and time period all significantly influence standardized death rates. The causes with the highest mortality impact are diseases of the circulatory system and malignant neoplasms (i.e., cancers), suggesting areas for targeted public health interventions.

The superior performance of the Random Forest model indicates complex, non-linear relationships between predictors and death rates that merit further investigation.

---
## 🔮 Future Work
- Deeper analysis of specific diseases within high-mortality categories
- Investigation of interactions between demographic factors and disease susceptibility
- Time series forecasting of death rate trends
- Policy impact analysis on mortality patterns

---
## 📜 License

This work is licensed under a 
[Creative Commons Attribution-NonCommercial 4.0 International License](http://creativecommons.org/licenses/by-nc/4.0/).

[![CC BY-NC 4.0][cc-by-nc-shield]][cc-by-nc]

[![CC BY-NC 4.0][cc-by-nc-image]][cc-by-nc]

[cc-by-nc]: http://creativecommons.org/licenses/by-nc/4.0/
[cc-by-nc-image]: https://licensebuttons.net/l/by-nc/4.0/88x31.png
[cc-by-nc-shield]: https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg

---
## 👥 Contributors
- Aatos Pham (Team Lead)
- [Uyen Pham](https://www.linkedin.com/in/elliepham05/) 
- [Linh Ha](https://www.linkedin.com/in/nhatlinhha/)
- [Phuong Nguyen](https://www.linkedin.com/in/phuong-paige-nguyen-6b3147289/)


