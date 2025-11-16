# Hospital Readmission Analysis — End-to-End Data Project
## Overview
This project explores hospital readmission patterns using a fully synthetic dataset that I generated, corrupted, cleaned, analyzed, modeled, and visualized end-to-end.

The goals of this project are to:

- Understand the factors that most strongly predict readmission
- Identify high-risk patient groups
- Build an interpretable baseline model
- Create a Tableau-ready dataset for interactive dashboards
- This project simulates a realistic healthcare analytics workflow, from raw data creation to actionable 		insights.

## Dataset
### Data Creation

The dataset was generated programmatically using Python (Faker, NumPy, pandas).
It includes:

- Patient demographics (age, gender, primary language)
- Admission and discharge information
- Diagnosis codes and comorbidities
- Length of stay
- Cost of stay
- 30-day readmission status

### Injected Imperfections
To simulate real hospital EHR data, I intentionally added imperfections such as:

- Typos in categorical fields
- Missing values
- Out-of-range ages and LOS values
- Inconsistent date formats
- Skewed cost distributions

### Cleaning Pipeline
 A dedicated cleaning notebook was built to:

- Normalize strings (title-case, strip, standardize categories)
- Correct common typos
- Validate allowed vocabularies
- Convert and repair date fields
- Clip outliers
- Impute missing data
- Enforce consistent data types
- Export a clean, analysis-ready dataset

#### The cleaned dataset is saved as:
 data/hospital_readmissions_clean.csv

## Tools & Methods Used
### Languages & Libraries
- Python
- pandas, NumPy
- Matplotlib, Seaborn
- scikit-learn
- Faker (for synthetic data generation)

### Analysis & Modeling
- Exploratory Data Analysis (EDA)
- Feature engineering
- Correlation ranking
- Logistic regression (baseline predictive model)
- ROC curve and model evaluation

### Visualization
- Professional-styled EDA charts in Python
- Tableau dashboard for storytelling and reporting

## Analysis Summary
### Feature Engineering
- Created:
- Age buckets
- Length-of-stay buckets
- Cost-per-day metric
- Admission month and year
- Predicted readmission risk (model output)

### Key EDA Findings
- Readmission rate increases sharply with age
- Patients with multiple comorbidities show significantly higher risk
- Longer hospital stays correlate with higher readmission probability
- Variation observed across insurance types and primary languages
- Cost-per-day and length-of-stay show meaningful relationships with readmission

## Predictive Modeling
A logistic regression model was trained using:
- Age
- Comorbidities count
- Length of stay
- Cost of stay

### Model Performance
- ROC AUC: ~0.78
- Good separation between high- and low-risk patients
- Interpretable coefficients highlighting the strongest predictors

### Output
Each patient receives a Predicted_Readmit_Risk score (0–1), which serves as the foundation for Tableau dashboards.

Final dataset exported as:
data/hospital_readmissions_for_tableau.csv

## Results & Insights
- Age is the strongest predictor of readmission
- Patients with 3+ comorbidities face substantially higher risk
- Readmission risk increases consistently across LOS buckets
- Certain patient groups (e.g., by language or insurance) show elevated rates
- Predicted risk enables proactive identification of high-risk cohorts
- These insights support hospital quality teams, discharge planning, and readmission-prevention strategies.
