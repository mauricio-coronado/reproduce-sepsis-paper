# Reproduction template

The goal of this template is to guide documentation of a reproduction of a study in an electronic health record database. Reproductions are assumed to be retrospective observational studies.

This template is based on material from the OSF, as well as from Brandt et al., 2013.

## Title of the study

The title of the reproduced study with its digital object identifier (DOI).

Title: An Interpretable Machine Learning Model for Accurate Prediction of Sepsis in the ICU

doi:10.1097/CCM.0000000000002936

## Dataset(s) used

Describe the dataset used in the reproduction. Include the same information as above, that is at least:

* Dataset name and version: MIMIC-IV v2.0
* DOI (or link if no DOI available): https://doi.org/10.13026/7vcr-e114
* Citation: Johnson, A., Bulgarelli, L., Pollard, T., Horng, S., Celi, L. A., & Mark, R. (2022). MIMIC-IV (version 2.0). PhysioNet. https://doi.org/10.13026/7vcr-e114.
* Other relevant information (link to dataset documentation, etc): https://mimic.mit.edu

If the same dataset in the original study is used for the reproduction, reference the prior section.

## Data extraction

### Inclusion/Exclusion criteria

Provide the column names for your proposed "cohort" table, which will apply all inclusion/exclusion criteria. Include the description of the criteria, the table in the dataset you will use, and how missing data will be interpreted (e.g. missing values will be assumed to include the patient).

* exclusion_short_los - Remove patients with a length of ICU stay that was less than 8 hours. Will use the *icustays* table.
* exclusion_long_los - Remove patients with a length of ICU stay that was more than 20 days. Will use the *icustays* table.
* exclusion_early_sepsis - Remove patients who met the Third International Consensus Definitions for Sepsis (sepsis-3) prior to or within 4 hours of their ICU admission. Will use *chartevents*



### Variables

List out the planned source for all covariates and exposures extracted for the study, e.g. admission source.
If describing a time-varying covariate, be specific regarding the aggregation and the time window (e.g. "lowest mean arterial pressure during the first 24 hours of the ICU stay."). The following template is a useful guide.

If unsure about the source, write all possibilities, and justify them in the notes.
Also include in the notes whether outliers were processed (and how), as well as the approach for missing data.

Variable name | Description | Timing | Aggregation | Source | Notes
--- | --- | --- | --- | --- | ---
Mean Arterial Blood Pressure (MAP) | Patient Mean Arterial Blood Pressure (MAP) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Heart Rate (HR) |  Patient Heart Rate (HR) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Oxygen Saturation (O2Sat) |  Patient Oxygen Saturation (O2Sat) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Systolic Blood Pressure (SBP) |  Patient Systolic Blood Pressure (SBP) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Diastolic Blood Pressure (DBP) |  Patient Diastolic Blood Pressure (DBP) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Respiratory Rate (RESP) |  Patient Respiratory Rate (RESP) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Temperature (Temp) | Patient Temperature (Temp) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Glasgow Coma Scale (GCS) |  Patient Glasgow Coma Scale (GCS) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Partial Pressure of Arterial Oxygen (PaO2) |  Patient Partial Pressure of Arterial Oxygen (PaO2) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
Fraction of Inspired O2 (FIO2) | Patient Fraction of Inspired O2 (FIO2) | Between 8 hours and 20 days of ICU stay | Any value | chartevents |
White Blood Count (WBC) | Patient White Blood Count (WBC) | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Hemoglobin  | Patient Hemoglobin  | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Hematocrit | Patient Hematocrit | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Creatinine   | Patient Creatinine   | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Bilirubin and Bilirubin direct | Patient Bilirubin and Bilirubin direct | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Platelets  | Patient Platelets  | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
International Normalized Ratio (INR) | Patient International Normalized Ratio (INR) | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Partial Prothrombin Time (PTT) | Patient Partial Prothrombin Time (PTT) | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Aspartate Aminotransferase (AST) | Patient Aspartate Aminotransferase (AST) | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Alkaline Phosphatase | Patient Alkaline Phosphatase | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Lactate | Patient Lactate | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Glucose, Potassium | Patient Glucose, Potassium | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Calcium | Patient Calcium | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
blood urea nitrogen (BUN) | Patient blood urea nitrogen (BUN) | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Phosphorus | Patient Phosphorus | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Magnesium | Patient Magnesium | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Chloride | Patient Chloride | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
B-type Natriuretic Peptide (BNP) | Patient B-type Natriuretic Peptide (BNP) | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Troponin | Patient Troponin | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Fibrinogen | Patient Fibrinogen | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
CRP | Patient CRP | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Sedimentation Rate | Patient Sedimentation Rate | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Ammonia | Patient Ammonia | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
pH | Patient pH | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
pCO2  | Patient pCO2  | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
HCO3 | Patient HCO3 | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Base Excess  | Patient Base Excess  | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
SaO2 | Patient SaO2 | Between 8 hours and 20 days of ICU stay | Any value | labevents/chartevents |
Care Unit | Care Unit (Surgical, Cardiac Care, or Neurointensive care) |  | Any value | icustays |
Recent Surgery | Indicator variable for surgery in the past 12 hours |  | Any value | procedureevents |
Wound Class | Wound Class (clean, contaminated, dirty, or infected) |  | Any value | procedureevents |
Surgical Specialty | Surgical Specialty (Cardiovascular, Neuro, Ortho-Spine, Oncology, Urology, etc.) |  | Any value | procedureevents |
Past Antibiotics | Number of antibiotics in the past 12, 24, and 48 hours |  | Any value | inputevents |
Age | Age of the patient |  | Any value | patients |
Charleston Comorbidity Index (CCI) | CCI of the patient |  | Any value | patients |
Mechanical Ventilation | Indicator variable for mechanical ventilation |  | Any value | procedureevents |
Max SOFA | Maximum change in SOFA score over the past 6 hours |  | Any value | chartevents (custom) |

Since the High-Resolution dynamical features were derived from the bedside monitor’s proprietary software using the ECG and blood pressure waveforms and I'm not certain that they could be obtained using MIMIC-IV, the resulting model will be the reduced model.

### Outcome(s)

List the outcome(s) used in the study, e.g. 28-day mortality, with similar detail as the above variables.

tsepsis, tSOFA and tonset as defined in the original paper with a prediction for the proceeding 4, 6, 8 and 12 hours for each.