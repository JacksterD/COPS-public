# COPS-public

The COVID-19 in Pregnancy in Scotland (COPS) study aims to find out how COVID-19 infection during pregnancy affects mothers and babies. This is a repository for public facing information about the study, including:

* Study protocols
* COPS code - the R code used to generate the COPS cohort
* Data Dictionary & Technical document. 

## Corrections

### November 2026: maternal diabetes and QCOVID risk factor flags

A recode added to `COPS code/1k. read in qcovid.r` in August 2022 set the QCOVID diabetes flags (`q_diag_diabetes_1`, `q_diag_diabetes_2`) to 1 for every mother linked to the March 2020 QCOVID extract, which covers most pregnancies that started before 2021. The March 2020 extract records "no" as 0 rather than missing, and the recode treated any non-missing value as "yes".

This affected the following variables in the fetus-level and pregnancy-level cohort files released in October 2022:

* `q_diag_diabetes_1` and `q_diag_diabetes_2`
* `x_diabetes` (fetus level) and `diabetes` (pregnancy level): about 62% of pregnancies were classed as `pre-existing_diabetes`; after the correction it is about 1%
* `q_covid_diag_any` (any QCOVID risk factor)

`q_preexisting_diabetes`, `q_covid_diag_any_excluding_diabetes` and `cv_clinical_vulnerability_category` were not affected. No other variables or records changed.

The code in this repository has been corrected. Researchers who used any of the affected variables should contact eDRIS about the corrected data.
