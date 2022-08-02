# Conclusion for reproduction

The following is a logbook/ultimate conclusion for a reproduction of a published scientific study. Feel free to add/remove sections as you find them useful.

## Title

Title: An Interpretable Machine Learning Model for Accurate Prediction of Sepsis in the ICU

doi:10.1097/CCM.0000000000002936

## Known differences

Specify changes to the data processing and/or methodology which are known to you. For each difference, describe: (1) the original study approach, (2) the reproduction approach, (3) the justification for the change. If possible, classify the differences as major (could impact the result of the study) or minor (unlikely to change the result of the study).

Data Processing:
1. Original study approach: 65 covariates
2. Reproduction approach: missing covariates including high frequency data, Max SOFA, Recent Surgery and Surgical Specialty. 
3. The model performance was adequate even with the omissions.

Methodology:

1. Original study approach: Weibull-Cox proportional hazards model to predict onset of sepsis in the proceeding $T$ hours (where $T$ = 4, 6, 8 or 12) 
2. Reproduction approach: Cox's time varying proportional hazard model 
3. It is an appropriate simplification of the original study's approach.

## Unknown differences

Specify changes to the data processing and/or methodology which *may* have occurred, but you are unable to confirm due to ambiguity in the original material studied. For each difference, describe (1) the most specific reference to the approach in the original study, if possible, and (2) the approach taken in the reproduction.

* Different variables may have been used: since sometimes there are many occurrences for one search of a covariate the chances that the exact same covariate was used in every case are slim.

* Missing values were filled with the mean of the values for each stay_id, there is not too much detail on the approeach followed in the study.

## Comparison of population

A table comparing the population measures between the original and the reproduction.

Septic

Population measure | Original Study | Reproduction
--- | --- | ---
Patients (#) | 3,845 (9.1%) | 9,954 (28.5%) 
Age | 66 | 65
Male (%) | 59* | 59*
Mortality | 25* | 13*
Length of Stay (Hours) | 158* | 94*
SOFA Score| 3.3* | 3.3

Non Septic

Population measure | Original Study | Reproduction
--- | --- | ---
Patients (#) | 38,586 | 24,981 
Age | 65 | 62 
Male (%) | 56 | 55 
Mortality (%) | 7.8 | 6.9
Length of Stay (Hours) | 45 | 48
SOFA Score| 1.5 | - 

## Comparison of results

A table of the evaluation measures comparing the results in the original study and the reproduction. Also include the final size of the cohort, proportion of individuals excluded, and other important summary measures for the study.

All Patients

Population measure | Original Study | Reproduction
--- | --- | ---
Patients (#) | 42,411 | 34,935 
Age | 66 | 63 
Male (%) | 56 | 56 
Mortality (%) | 9.3 | 8.6
Length of Stay (Hours)| 47 | 61
SOFA Score| 1.6 | -


## Conclusion(s) regarding reproducibility

Highlight specific challenges faced during the reproduction attempt which could be improved upon in the future.

Getting a single query without the notebook crashing was a challenge that required more efficiency in the coding, and in the end was solved getting different queries from different sources. The integration of these sources is something that would improve the reporoduction. Additionally, exploration of the variables that share the name in different tables could be explored in order to decrease the number of missing values. 

Further improvements could be achieved by the addition of the high frequency data once it is available.