# Prostate Cancer Survival & Screening Impact Dashboard
SQL + Power BI Project | Prostate Cancer Analytics | From Raw Data to Healthcare Insights

### Table of Contents
* Project Overview
* Tools & Technologies
* Dataset Overview
* Data Cleaning
* Exploratory Data Analysis
* Power BI Dashboard
* Key Metrics
* Key Insights
*Recommendations

### Project Overview
This project analyses prostate cancer patient data to uncover insights on survival outcomes, mortality rates, early detection impact, and treatment effectiveness.
The goal is to:
> - Evaluate the impact of early screening on survival rates
> - Understand diagnosis distribution across stages
> - Analyse patient outcomes (Alive vs Deceased)
> - Identify trends across age groups and PSA levels
> - Support data-driven healthcare and screening strategies

### Tools & Technologies
SQL – Data extraction, cleaning, and analysis
Power BI – Dashboard creation and data storytelling

### Dataset Overview
The dataset includes:
> - Patient demographics (Age groups)
> - Diagnosis stages (Stage I – Stage IV)
> - Screening frequency (Regular, Occasional, None)
> - Treatment types (Surgery, Radiation, Hormone Therapy, etc.)
> - Survival outcomes (Alive, Deceased)
> - PSA (Prostate-Specific Antigen) levels
- Total Patients: 50,000

Sample Preview
| Patient_ID |Age |Gender | Cancer_Type | Cancer_Stage | Tumor_Size_cm | Affected_testicle | Receptor_Status |Histology_Comfirmation | Treatment_Type | Diagnosis_Date | Survuval_Status | Survival_Months | Recurrence_Status |Recurrence_Months |
|-----------|-----|-------|--------------|--------------|---------------|-----------------|-----------------|-----------------------|----------------|----------------|-----------------|-----------------|-------------------|------------------|
| PC000001 | 83 | Male | Prostate | Stage IV |3.32 | Both (N/A) | Negative | Confirmed | Radiation Therapy | 2024-05-05 | Alive | 62 | No | 0 |
| PC000002 | 73 | Male | Prostate | Stage I | 4.29 | Right (N/A) |Negative | Confirmed | Radiation Therapy | 2012-07-01 | Alive | 11| No | o |

### Data Cleaning
Key steps performed:
> - Removed duplicate patient records
> - Handled missing/null values
> - Standardized stage and treatment categories
> - Created calculated measures (Survival Rate %, Death Rate %, Early Detection %)
> - Grouped ages into meaningful segments (40–49, 50–59, etc.)
> - Ensured consistent formatting for numerical and date fields

### Exploratory Data Analysis
1. Patients by Diagnosis Stage
```SQL
SELECT 
    Diagnosis_Stage,
    COUNT(*) AS total_patients
FROM prostate_data
GROUP BY Diagnosis_Stage
ORDER BY total_patients DESC;
```
2. Survival vs Death Rate
```SQL
SELECT 
    Survival_Status,
    COUNT(*) AS total,
    ROUND(COUNT(*) * 100.0 / (SELECT COUNT(*) FROM prostate_data), 2) AS percentage
FROM prostate_data
GROUP BY Survival_Status;
```
3. Screening Impact on Diagnosis Stage
```SQL
SELECT 
    Screening_Type,
    Diagnosis_Stage,
    COUNT(*) AS total_patients
FROM prostate_data
GROUP BY Screening_Type, Diagnosis_Stage;
```
4. Age Group Distribution
```SQL
SELECT 
    Age_Group,
    COUNT(*) AS total_patients
FROM prostate_data
GROUP BY Age_Group
ORDER BY total_patients DESC;
```
5. Treatment Distribution
```SQL
SELECT 
    Treatment_Type,
    COUNT(*) AS total_patients
FROM prostate_data
GROUP BY Treatment_Type
ORDER BY total_patients DESC;
```
6. PSA Levels by Age
```SQL
SELECT 
    Age,
    AVG(PSA_Level) AS avg_psa
FROM prostate_data
GROUP BY Age
ORDER BY Age;
```

### Power BI Dashboard
The dashboard provides an interactive and clinical view of prostate cancer insights:
- KPIs (Top Section):
> - Total Patients: 50,000
> - Survival Rate: 85%
> - Death Rate: 15%
> - Early Detection Rate: 66%
> - Regular Check-up Rate: 45%
- Filters:
> - Treatment Type
> - Age Group
> - Diagnosis Stage
> - Screening Frequency
_ Visuals:
1. Diagnosis Stage by Screening Frequency
2. Patient Outcome (Alive vs Deceased)
3. Age Group Distribution
4. Diagnosis Stage Distribution
5. Treatment Distribution
6. PSA Level by Age (Scatter Plot)
<img width="1158" height="654" alt="Prostate_cancer_dashboard_image" src="https://github.com/user-attachments/assets/208526ba-346f-401d-8ddc-8663d481be50" />


### Key Metrics
- Total Patients: 50,000
- Survival Rate: 85%
- Death Rate: 15%
- Early Detection Rate: 66%
- Regular Check-up Rate: 45%

### Key Insights
1. Early detection significantly improves survival
- Majority of patients diagnosed at Stage I show high survival outcomes
- Regular check-ups strongly correlate with early-stage diagnosis
2. Late-stage diagnosis increases mortality risk
- Stage IV has the lowest patient count but highest risk impact
- Patients without check-ups are more likely diagnosed at later stages
3. Screening behavior is inconsistent
- Only 45% of patients undergo regular check-ups
- A large portion still relies on occasional or no screening
4. Age distribution is relatively balanced
- Most cases fall between 40–80+, with slight peaks in older groups
5. Treatment distribution is evenly spread
- No single dominant treatment, indicating personalized treatment approaches
6. PSA levels vary with age
- PSA levels generally increase with age, supporting its role in early detection

### Recommendations
1. Promote regular screening programs
> Increase awareness campaigns to boost regular check-up rates beyond 45%
2. Focus on early-stage detection
> Invest in screening infrastructure to catch more cases at Stage I
3. Target high-risk age groups
> Prioritize screening for patients aged 50+ where risk increases
4. Improve late-stage treatment strategies
> Enhance care plans for Stage III and IV patients
5. Leverage PSA monitoring
> Encourage routine PSA testing as a preventive measure
6. Adopt data-driven healthcare decisions
> Use dashboards like this to guide hospital policies and resource allocation

### Dataset Source
<img width="1622" height="842" alt="Prostate_cancer_sample" src="https://github.com/user-attachments/assets/936a9a77-aa15-4a04-b75d-6aaed24f2bbc" />
[Download Here](https://docs.google.com/spreadsheets/d/1h0F7e1O_il-M3iVJxBfpVC_v7FwTVqQGFiMDlr17tYg/edit?usp=sharing)

