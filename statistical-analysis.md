# Statistical Inference, Resampling, and Hypothesis Testing on COVID-19 Data

This repository contains the second phase of a COVID-19 data analysis project. After completing data cleaning, preprocessing, and exploratory analysis, this stage focuses on applying statistical inference techniques to understand population characteristics and investigate clinically relevant hypotheses.

## Project Overview

The objective of this analysis is to demonstrate practical applications of statistical theory using a large-scale COVID-19 patient dataset containing 566,602 observations.

The project covers:

* Central Limit Theorem (CLT) simulation
* Sampling distributions of the mean
* Standard Error estimation
* Bootstrap resampling
* Confidence interval estimation
* Hypothesis testing
* Statistical interpretation of clinical risk factors

The analysis uses patient age, ICU admission status, diabetes history, and other medical variables to explore relationships between demographic and clinical outcomes.

---

## Dataset

The dataset contains:

* 566,602 patient records
* Demographic information
* COVID-19 test results
* Hospitalization status
* ICU admission records
* Comorbidities and underlying diseases
* Mortality outcomes

The dataset used in this stage is the fully cleaned and encoded version generated during the preprocessing phase.

For details about data preparation and feature engineering, see:

**[COVID-19 Data Preprocessing, Encoding, and Exploratory Analysis](../preprocessing/README.md)**

---

# Statistical Analyses

## 1. Central Limit Theorem (CLT) Simulation

The age variable was used to empirically demonstrate the Central Limit Theorem.

Random samples of varying sizes were repeatedly drawn from the population, and sampling distributions of the sample mean were generated.

Sample sizes examined:

* n = 15
* n = 30
* n = 100
* n = 200

Key objectives:

* Observe convergence toward normality
* Compare sample means with the population mean
* Investigate the effect of sample size on variability

### Findings

* Sampling distributions become increasingly normal as sample size increases.
* Larger samples produce more stable estimates of the population mean.
* Variability decreases as sample size grows.

---

## 2. Standard Error Estimation

Standard Error (SE) was estimated using two independent approaches:

### Theoretical Formula

SE = σ / √n

### Simulation-Based Estimation

The standard deviation of the simulated sampling distributions was calculated and compared with theoretical values.

### Findings

* Simulated and theoretical standard errors were nearly identical.
* Standard error decreases as sample size increases.
* Larger samples yield more precise estimates.

---

## 3. Bootstrap Resampling

Bootstrap resampling was performed to estimate sampling variability without relying on distributional assumptions.

### Procedure

* 5,000 bootstrap samples
* Sample size = 100
* Sampling with replacement

### Outputs

* Bootstrap estimate of mean age
* Bootstrap standard error
* 95% confidence interval

### Results

* Bootstrap Mean ≈ 42.62 years
* Bootstrap SE ≈ 1.66
* 95% Confidence Interval ≈ (39.37, 45.95)

### Findings

Bootstrap estimates closely matched theoretical and simulation-based results, confirming the robustness of the estimation procedure.

---

## 4. Hypothesis Testing

### Test 1: Age and ICU Admission

#### Research Question

Are ICU patients significantly older than non-ICU patients?

#### Method

Welch's Two-Sample t-Test

#### Hypotheses

H₀: Mean age of ICU patients equals mean age of non-ICU patients.

H₁: Mean age of ICU patients differs from mean age of non-ICU patients.

#### Results

* Mean Difference ≈ 8.33 years
* t-statistic ≈ 38.38
* p-value < 0.001

#### Conclusion

ICU patients were significantly older than non-ICU patients, indicating age as an important risk factor for severe COVID-19 outcomes.

---

### Test 2: Clinical Risk Factors and ICU Admission

Chi-square tests were applied to evaluate associations between categorical medical variables and ICU admission.

Variables examined include:

* Diabetes
* Hypertension
* Pneumonia
* COPD
* Obesity
* Cardiovascular disease
* Tobacco use
* COVID test result
* Patient hospitalization status

#### Findings

Strong associations were observed for:

* Pneumonia
* Hospitalization status
* Intubation
* Diabetes
* Hypertension
* Renal chronic disease

These variables exhibited extremely large Chi-square statistics and highly significant p-values.

---

## Key Findings

### Age as a Risk Factor

Patients admitted to the ICU were substantially older than those who were not admitted.

### Diabetes as a Risk Factor

Diabetes showed one of the strongest associations with severe outcomes and mortality.

### Validation of Statistical Theory

The project provides empirical evidence supporting:

* Central Limit Theorem
* Sampling theory
* Standard Error estimation
* Bootstrap inference

### Importance of Large Sample Sizes

The large dataset allowed precise estimation of population parameters and increased the reliability of hypothesis testing results.

---

## Technologies Used

* Python
* NumPy
* Pandas
* SciPy
* Matplotlib
* Seaborn

---

## Authors

* Porya Ardestani Samani
* Tohid Nouri

---

## Related Work

This project builds directly upon the preprocessing phase:

**COVID-19 Data Preprocessing, Encoding, and Exploratory Analysis**

which includes:

* Missing value handling
* Data cleaning
* Feature engineering
* Categorical encoding
* Exploratory data analysis
* Target construction

The processed dataset generated in that stage serves as the foundation for all statistical analyses performed in this repository.
