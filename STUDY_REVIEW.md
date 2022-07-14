# Study Review

Review the chosen study as if you were an academic reviewer.

## 1. Study information

### Title

The title of the study with its digital object identifier (DOI).

Title: An Interpretable Machine Learning Model for Accurate Prediction of Sepsis in the ICU

doi:10.1097/CCM.0000000000002936

### Objective(s) of the study

Describe the primary and secondary objectives of the research study.

Primary objective: to develop and validate an Artificial Intelligence Sepsis Expert (AISE) algorithm for early prediction of sepsis and demonstrate that a high-performance prediction model can be derived from a combination of EMR and high-frequency physiologic data. 

Secondary objective: to test the relationship between the prediction lead time and predictive accuracy of the model, and to investigate questions of generalizability and interpretability of the proposed model.

### Dataset(s) used

Describe the dataset used in the original study. Include:

* Dataset name and version:
    * Over 31,000 admissions to the intensive care units (ICUs) at two Emory University hospitals (development cohort)
    * Additionally, over 52,000 ICU patients from the publicly available MIMIC-III ICU database (validation cohort)

* DOI: 10.1097/CCM.0000000000002936
* Citation: Nemati, S., Holder, A., Razmi, F., Stanley, M. D., Clifford, G. D., & Buchman, T. G. (2018). An interpretable machine learning model for accurate prediction of sepsis in the ICU. Critical care medicine, 46(4), 547.
* Other relevant information (link to dataset documentation, etc):
    * Data from the electronic medical record was extracted through a clinical data warehouse (MicroStrategy, Tysons Corner, VA). High resolution heart rate and blood pressure time series at 2 seconds resolution were collected from select ICUs, through the BedMaster system.
    * For MIMIC-III: https://mimic.mit.edu/docs/iii/.

## 2. Summarize the paper

Summarize the paper's goals and results in your own words.

Through an observational cohort study using data of patients from the ICU, the research is trying to develop an artificial intelligence method to predict sepsis occurrence. Using AUROC to measure the model's success it was proven that high-performance models can be constructed.

### Strength(s) of the work

Highlight 3 strengths of the work.

* The algorithm was tested in a development and a validation dataset. Making the results more robust.
* Their algorithm combines data collected at different resolutions: low-resolution EMR data, and high-resolution blood pressures and heart rates, being among the first to do this.
* The AISE system can accommodate more input features as the medical community learns more about sepsis.
* This is the first study to demonstrate acceptable performance of a sepsis prediction algorithm over incrementally longer time windows.

### Weakness(es) of the work

Highlight 3 weaknesses of the work.

* The data was analyzed retrospectively using electronic medical record data not originally designed for the analyses performed.The suspicion of infection had to be inferred from systematic criteria, which may not reflect the true rationale of care in all patients.
* The model used was trained on EMR data entered by bedside nurses, which may confer some recall and information bias.
* No sensitivity analysis was performed.

### Anticipated reproducibility challenges

Describe areas of the paper which appear to lack sufficient detail.

The data extraction might be difficult to reproduce since the criteria depends on developing sepsis early in the ICU stay, which in turn depends on analyzing pre-ICU antibiotic administration and culture acquisition. Additionally, there is no supplementary information regarding this step, for example, a diagram that describes how the cohort size changes with each exclusion.


## 3. Data extraction

### Variables

List out the covariates and exposures extracted for the study, e.g. admission source.

A total of 65 features were included in the machine learning prediction model:

* High-resolution dynamical features (calculated using 6 hours sliding windows, with 5 hours overlap; 6 features): 
    * standard deviation of RR intervals and MAP (RRSTD and MAPSTD),
    * average multiscale entropy 1 of RR and MAP (HRV1 and BPV1) and
    * average multiscale conditional entropy of RR and MAP (HRV2 and BPV2).


* Clinical features (10 features): 
    * Mean Arterial Blood Pressure (MAP), 
    * Heart Rate (HR), 
    * Oxygen Saturation (O2Sat), 
    * Systolic Blood Pressure (SBP), 
    * Diastolic Blood Pressure (DBP), 
    * Respiratory Rate (RESP), 
    * Temperature (Temp), 
    * Glasgow Coma Scale (GCS), 
    * Partial Pressure of Arterial Oxygen (PaO2), 
    * Fraction of Inspired O2 (FIO2).
    
    
* Laboratory (General; 25 features): 
    * White Blood Count (WBC), 
    * Hemoglobin, 
    * Hematocrit,
    * Creatinine, 
    * Bilirubin and Bilirubin direct, 
    * Platelets, 
    * International Normalized Ratio (INR), 
    * Partial Prothrombin Time (PTT), 
    * Aspartate Aminotransferase (AST), 
    * Alkaline Phosphatase, 
    * Lactate,
    * Glucose, Potassium, 
    * Calcium, 
    * blood urea nitrogen (BUN), 
    * Phosphorus, 
    * Magnesium, 
    * Chloride, 
    * B-type Natriuretic Peptide (BNP), 
    * Troponin, 
    * Fibrinogen, 
    * CRP, 
    * Sedimentation Rate, 
    * Ammonia.


* Laboratory (Arterial Blood Gas or ABG; 5 features):
    * pH, 
    * pCO2, 
    * HCO3,
    * Base Excess, 
    * SaO2.
    
    
* Demographics/History/Context (19 features): 
    * Care Unit (Surgical, Cardiac Care, or Neurointensive care), 
    * Surgery in the past 12 hours, 
    * Wound Class (clean, contaminated, dirty, or infected), 
    * Surgical Specialty (Cardiovascular, Neuro, Ortho-Spine, Oncology, Urology, etc.),
    * Number of antibiotics in the past 12, 24, and 48 hours,
    * Age, 
    * Charleston Comorbidity Index (CCI), 
    * Mechanical Ventilation, 
    * Maximum change in SOFA score over the past 6 hours

The reduced model excluded the less commonly measured clinical variables, such as ABG 
laboratory features, as well as Bilirubin direct, Glucose, B-type Natriuretic Peptide (BNP), 
Fibrinogen, CRP, Sedimentation Rate, Ammonia, resulting in a total of 53 features.

### Outcome(s)

List the outcome(s) used in the study, e.g. 28-day mortality.

The primary outcome was tsepsis, but also tSOFA and tonset were reported. Additional information on the differences of these outcomes can be found in the extract below. For each of these variables a prediction for the proceeding 4, 6, 8 and 12 hours was estimated.

Patients were followed throughout their ICU stay until discharge or development of sepsis, 
according to the Third International Consensus Definitions for Sepsis (sepsis-3). 
Specifically, all episodes of suspected infection (tsuspicion) were identified as the earlier 
timestamp of antibiotics and blood cultures within a specific time span; if the antibiotic was 
given first, the culture sampling must have been obtained within 24 hours. If the culture 
sampling was first, the antibiotic must have been ordered within 72 hours. The onset time of 
sepsis (tsepsis) was then defined as an episode of suspected infection with two or more points 
change in the SOFA score (tSOFA) from up to 24 hours before to up to 12 hours after the 
tsuspicion (tSOFA+24h>tsuspicion>tSOFA-12h). These definitions were based on a recent 
assessment of the revised clinical criteria for sepsis. [11] Finally, we defined tonset as the 
minimum of tsepsis and tSOFA. Though our primary outcome was tsepsis, we report the 
predictive performance of our algorithm also on tSOFA and tonset for completeness and to 
facilitate comparison with the existing literature.

### Inclusion/Exclusion criteria

Describe the inclusion criteria for the study. Since inclusion/exclusion criteria are interchangeable, decide on the most clear presentation of the study methodology, e.g. "the study included all adults, and excluded patients admitted to CSRU."

Patients who met the Third International Consensus Definitions for Sepsis (sepsis-3) prior to or within 4 hours of their ICU admission were excluded. Also, patients were excluded if their length of ICU stay (LOS) was less than 8 hours or more than 20 days.

### Outlier handling

If outliers were specially processed, describe the approach here.

No mention of handling outliers in paper or supplementary material

### Missing data handling

For any missing data present in the study, explain the approach to handle it.

Used a general 1-hour time bin interval in all dynamic features to account for missing data points in low-frequency clinical data.

Mean imputation was used to replace all remaining missing values (mainly at the start of each record).


## 4. Results

### Population summary

Provide information about the original study's population: sample size, average mortality, etc. Typically the data is presented in the first table (i.e. Table 1). Select a parsimonious set of descriptors which you will compare your reproduction against. At the very least include the sample size and a summary measure of the outcome(s).

![Table A1](table_a1.png)

![Table E1](table_e1.png)



### Analysis method

Explain the analysis method of the study in detail.

The proposed Artificial Intelligence Sepsis Expert (AISE) algorithm is based 
on a modified Weibull-Cox proportional hazards model, designed to predict onset of sepsis in 
the proceeding T hours (where T = 12, 8, 6 or 4 hours). The Weilbull proportional hazards 
model is a robust parametric counterpart of the more familiar Cox time-to-event analysis. The 
Weibull-Cox model assumes a traditional Cox proportional hazards hazard rate but with a 
Weibull base hazard rate.


### Power calculations (if present)

If a power calculation is present, describe the approach and the assumptions made.

### Evaluation measures

e.g. p-value, effect sizes, statistical tests, performance measures like area under the receiver operator characteristic curve, etc.

AISE classification results for T hours (T = 12, 8, 6 or 
4 hours) ahead predictions are based on a random split into 80% training 20% testing, and 
the area under receiver operating characteristic (AUROC) curves statistics for both the
training and the testing sets are reported, as well as specificity (1–false alarm rate) and 
accuracy at a fixed 85% sensitivity level.

Both training set and testing set AUROCs for detecting sepsis were 0.79 or higher for every 
prediction task (tsepsis, tSOFA, tonset) and prediction window (n=4, 6, 8, and 12 hours).Catching 85% of the septic patients yielded 30% false alarms (SP=0.70) within the training 
set (left panel) and 33% false alarms (SP=0.67) within the testing set.

### Sensitivity Analyses

Describe any additional sensitivity analyses performed in the study.

No sensitivity analysis was performed
