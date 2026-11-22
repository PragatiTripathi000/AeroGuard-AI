# AeroGuard-AI 
### Intelligent Go-Around Prediction and Aviation Approach Risk Analysis

AeroGuard-AI is an end-to-end machine learning project focused on identifying patterns associated with aircraft go-arounds during landing approaches. It uses historical aviation landing data, aircraft and runway characteristics, and weather observations to develop a data-driven approach to go-around prediction and aviation risk analysis.

The project emphasizes careful data preprocessing, feature engineering, leakage prevention, chronological validation, and evaluation under severe class imbalance.

---

##  Project Objectives

- Analyze historical aircraft landing and go-around events.
- Identify operational, runway, aircraft, and weather-related patterns.
- Develop reliable machine learning models for go-around prediction.
- Address the highly imbalanced nature of aviation go-around data.
- Interpret model predictions using explainability techniques.
- Build an interactive interface for exploring predictions and risk factors.

## 📊 Dataset Overview

The project uses historical aircraft landing data containing normal landing and go-around observations.

**Current dataset characteristics:**

| Attribute | Details |
|---|---|
| Total observations | 8,969,145 |
| Total original columns | 31 |
| Normal landings | 8,935,481 |
| Go-arounds | 33,664 |
| Go-around proportion | Approximately 0.375% |
| Observation period | January–December 2019 |

The dataset contains information related to:

- Airport and runway characteristics
- Aircraft types and wake turbulence categories
- Glide-slope angle and runway length
- Wind speed and direction
- Visibility and temperature
- Weather observations and conditions
- Go-around target label

**Dataset source:** [Zenodo – Large aircraft landing dataset at 20 large European airports](https://zenodo.org/records/7148117)

Raw and processed datasets are excluded from this GitHub repository to avoid committing large data files.

## ⚙️ Work Completed

### 1. Dataset Inspection and Quality Assessment

- Examined dataset dimensions, data types, and feature distributions.
- Investigated missing values and duplicate records.
- Checked target distribution and class imbalance.
- Examined categorical features and rare categories.
- Investigated inconsistencies in numerical and categorical values.

### 2. Data Cleaning and Preprocessing

- Standardized categorical values and handled missing categories.
- Investigated invalid temperature observations.
- Examined runway and aircraft-related feature inconsistencies.
- Reviewed highly missing and strongly correlated numerical features.
- Excluded potentially leakage-prone variables from the initial feature set.

### 3. Chronological Data Splitting

The data was divided chronologically to preserve the time order of observations.

| Dataset | Period | Records |
|---|---|---:|
| Training | January–September 2019 | 6,437,111 |
| Validation | October 2019 | 876,435 |
| Testing | November–December 2019 | 1,655,599 |

The test dataset is reserved for final model evaluation.

### 4. Feature Engineering

**Categorical features**
- One-hot encoding for selected categorical variables.
- Frequency encoding for high-cardinality features.
- Encoder fitted using training data only.
- Unseen categories handled during validation and testing.

**Numerical features**
- Circular encoding of wind direction using sine and cosine transformations.
- Training-set median calculation for numerical imputation.
- Missingness indicators retained where appropriate.

**Weather features**
- Investigated serialized weather-code lists.
- Extracted observed weather conditions into binary indicators.
- Engineered 21 weather-condition and intensity indicators.
- Created a recognized-weather-condition presence indicator.
- Removed the original raw weather-list columns after feature extraction.

### 5. Model-Ready Dataset Preparation

Prepared separate model-ready datasets for training, validation, and testing.

| Validation check | Result |
|---|---|
| Expected row counts preserved | Passed |
| Missing values in final datasets | 0 |
| Duplicate columns | 0 |
| Raw weather columns remaining | 0 |
| Invalid weather indicator values | 0 |
| Target column preserved | Yes |

The final model-ready datasets contain **139 columns each**, including the target.

---

##  Planned Machine Learning Workflow

The following stages are planned and have not yet been completed:

1. Feature selection and final modelling dataset preparation.
2. Baseline model development.
3. Model training and comparison.
4. Class imbalance handling.
5. Hyperparameter tuning.
6. Evaluation using precision, recall, F1-score, ROC-AUC, PR-AUC, and confusion matrices.
7. Model explainability using feature importance and SHAP.
8. Interactive dashboard development using Streamlit.
9. Final documentation and deployment.

## 🛠️ Technology Stack

| Area | Technologies |
|---|---|
| Programming | Python |
| Data manipulation | Pandas, NumPy |
| Data visualization | Matplotlib, Seaborn |
| Machine learning | Scikit-learn |
| Data storage | CSV, Parquet |
| Model artifacts | Joblib, JSON |
| Development | Jupyter Notebook, VS Code |
| Version control | Git, GitHub |
| Planned dashboard | Streamlit |

## 📁 Project Structure

```text
AeroGuard-AI/
│
├── data/
│   ├── raw/
│   └── processed/
│       ├── splits/
│       ├── encoded/
│       ├── numerical/
│       ├── weather/
│       └── model_ready/
│
├── notebooks/
│
├── src/
│
├── models/
│   ├── categorical_encoder.joblib
│   └── numerical_medians.json
│
├── reports/
│
├── dashboard/
│
├── 01_dataset_inspection.ipynb
├── README.md
└── .gitignore
```

*Note: The project structure represents the working directory; some folders and planned components are still under development.*

##  Current Project Status

**Completed:** Dataset inspection, data cleaning, chronological splitting, categorical encoding, numerical preprocessing, weather feature engineering, and model-ready dataset validation.

**In progress:** Final feature review and machine learning experimentation.

**Upcoming:** Model comparison, explainability, interactive dashboard, and deployment.

---

##  Important Note

AeroGuard-AI is an academic machine learning research project. Its predictions are intended for experimentation and decision-support research, not as a replacement for certified aviation safety systems, air traffic control procedures, or operational pilot judgment.

##  Author

**Pragati Tripathi**

B.Tech Computer Science and Engineering | Data Science Minor

[GitHub Profile](https://github.com/PragatiTripathi000)

