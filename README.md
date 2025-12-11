# Survival-Analysis-Dirt-Slurper-Reliability
Survival analysis of DirtSlurper3100 robot vacuum warranty data — characterizing component lifetimes using Kaplan-Meier estimation, Cox regression, and parametric reliability modeling.
## Project Overview
This project analyzes warranty data from the DirtSlurper3100, a fictional robot vacuum cleaner manufactured by IButler. The company observed higher-than-expected warranty claims and needed statistical evidence to evaluate whether component suppliers meet their reliability specifications.

## Objectives

1. Characterize component lifetimes for Battery, IR sensor, and Impact sensor
2. Identify risk factors affecting component reliability (pet ownership, usage intensity, carpet score)
3. Verify manufacturer claims:

3.1 IR sensor: L10 ≥ 2000 days
3.2 Battery: L10 ≥ 1000 days (excluding extreme usage)
3.3 Impact sensor: Provide specifications for potential external sales

## Insights

1. Pet ownership is the strongest predictor of component failure (Hazard Ratio = 9.48, p < 0.005)
2. Households with pets are ~9.5x more likely to experience vacuum failure
3. Total usage time significantly correlates with failure risk
4. Carpet score shows minimal association with component failures

## Methodology

Statistical Techniques

Method                   Purpose
Kaplan-Meier Estimation  Non-parametric survival curves
Cox Proportional Hazards Quantify covariate effects on hazard
Log-rank Tests           Compare survival between groups
Parametric AFT Models    Weibull, Log-Normal, Log-Logistic for L10 estimation
Bootstrap Resampling     Confidence intervals for L10 estimates

Censoring Mechanism
The data exhibits Type I right censoring: vacuum cleaners registered later in the study period (Jan 2015 – Dec 2019) have less opportunity to fail before study end. Non-failed units contribute censored observations.


## Notebook Sections

1. Data Loading & Preprocessing — Date conversion, binary encoding, censoring time calculation
2. Exploratory Data Analysis — Distribution comparisons, statistical association tests
3. Modeling — Kaplan-Meier, Cox PH, proportional hazards assumption check
4. Inference — Log-rank tests, L10 with bootstrap confidence intervals
5. Manufacturer Claims — Direct verification against specifications


## Notes
L10 Definition
L10 (also written as B10) is the time at which 10% of units have failed, equivalently when 90% survive. This is a standard reliability engineering metric.

## Assumptions
Proportional Hazards Assumption
The Cox model assumes hazard ratios remain constant over time. We verify this using Schoenfeld residuals test — violation may indicate need for time-varying coefficients or stratified models.

Multiple Testing Correction
With 9 association tests (3 factors × 3 components), we apply Bonferroni correction:

Original α = 0.05
Corrected α = 0.05/9 ≈ 0.0056
