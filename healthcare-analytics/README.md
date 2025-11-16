**Hospital Readmission Analysis — End-to-End Data Project**

**Overview**
This project explores hospital readmission patterns using a fully synthetic dataset that I generated, corrupted, cleaned, analyzed, modeled, and visualized end-to-end.
The goal of the project is to:
understand the factors that most strongly predict readmission
identify high-risk patient groups
build an interpretable baseline model
create a Tableau-ready dataset for interactive dashboards
This project simulates a realistic healthcare analytics workflow, from raw data creation to actionable insights.

**Dataset**
**Data Creation**
I generated the raw dataset programmatically using Python (Faker, NumPy, pandas).
It includes:
Patient demographics (age, gender, language)
Admission and discharge information
Diagnosis and comorbidities
Length of stay
Cost of stay
30-day readmission status

**Injected Imperfections**
To simulate real hospital EHR data, I intentionally added imperfections such as:
typos in categorical fields
missing values
out-of-range ages and LOS values
inconsistent date formats
skewed distribution in costs

**Cleaning Pipeline**
I built a structured cleaning notebook that:
normalized strings (title-case, strip, deduplicate categories)
corrected common typos
validated allowed vocabularies
converted and repaired date fields
clipped outliers
imputed missing values
enforced correct data types
exported a clean, analysis-ready dataset

The cleaned dataset is saved as:
data/hospital_readmissions_clean.csv

**Tools & Methods Used**

**Language & Libraries**
Python
pandas, NumPy
Matplotlib, Seaborn
scikit-learn
Faker (for data generation)

**Analysis & Modeling**
Exploratory Data Analysis (EDA)
Feature engineering
Correlation ranking
Logistic regression (baseline predictive model)
ROC curve and model evaluation

**Visualization**
Professional-styled EDA charts in Python
Tableau dashboard for storytelling and reporting

**Analysis Summary**

**Feature Engineering**
Created:
Age buckets
Length-of-Stay buckets
Cost-per-day metric
Admission month & year
Predicted readmission risk (model output)

**Key EDA Findings**
Patterns observed:
Readmission rate increases sharply with age.
Patients with multiple comorbidities show significantly higher risk.
Longer hospital stays correlate with higher readmission probability.
Differences appear across insurance types and primary languages.
Cost-per-day and length-of-stay show meaningful relationships with readmission.

**Predictive Modeling**
A logistic regression model was trained using:
Age
Comorbidities count
Length of stay
Cost of stay

**Model Performance**
ROC AUC: ~0.78
Good separation between high- and low-risk patients
Interpretable coefficients highlighting the strongest predictors

**Output**
Each patient receives a Predicted_Readmit_Risk score (0–1).
This becomes the foundation for Tableau visuals.

Final dashboard dataset exported as:
data/hospital_readmissions_for_tableau.csv

**Results & Insights**
Age is the strongest predictor of readmission in this dataset.
Patients with 3+ comorbidities face substantially higher risk.
Risk increases consistently across length of stay buckets.
Certain patient groups (by language or insurance type) display higher readmission rates.
Predicted risk offers a way to proactively identify high-risk patients.
These insights can support hospital quality teams, discharge planning, and readmission-prevention programs.

**Project Structure**
data-analytics-portfolio/
│
├── data/
│   ├── hospital_readmissions.csv
│   ├── hospital_readmissions_dirty.csv
│   ├── hospital_readmissions_clean.csv
│   └── hospital_readmissions_for_tableau.csv
│
├── healthcare-analytics/
│   ├── generate_hospital_data.ipynb
│   ├── inject_imperfections.ipynb
│   ├── clean_hospital_data.ipynb
│   └── analyze_hospital_readmissions.ipynb
│
└── README.md


