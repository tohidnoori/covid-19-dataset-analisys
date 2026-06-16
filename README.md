## COVID-19 Data Preprocessing, Encoding, and Exploratory Analysis

This repository contains a report-style homework assignment for a **Data Science** course. The project focuses on preparing and analyzing a **COVID-19 patient dataset** for machine learning and descriptive statistics.

## Project Overview

The main goal of the assignment is to transform a raw clinical dataset into a clean, numeric, model-ready dataset. The work includes:

- understanding the raw data structure,
- inspecting categorical features,
- analyzing missing values,
- cleaning and imputing incomplete records,
- encoding categorical variables,
- engineering time-based features,
- and exploring the target distribution and feature histograms.

## Dataset

The original dataset contains:

- **566,602 records**
- **23 columns**

It includes demographic, clinical, admission, and outcome-related information such as:

[`sex`,`age`,`patient_type`,`entry_date`,`hypertension`,`asthma`,`copd`,`diabetes`,`pregnancy`,`pneumonia`,`tobacco`,`renal_chronic`,`obesity`,`cardiovascular`,`other_disease`,`contact_other_covid`,`res_covid`,`died_date`,`intubed`,`icu`]

The `id` column is removed during preprocessing.

## **[Data Understanding and Preprocessing Report](./data_preprocessing_report.md)**

A detailed analysis of data quality, missing values, cleaning strategies, feature encoding, time-based feature engineering, and exploratory data analysis is provided in the accompanying preprocessing report.

The report covers:

* Missing value analysis and interpretation
* Domain-driven data cleaning and imputation
* Construction of the binary `died` target variable
* Handling of ICU and intubation information
* Categorical feature encoding
* Date and timestamp feature engineering
* Target distribution analysis
* Histogram-based exploratory data analysis

## **[Statistical Inference, Resampling, and Hypothesis Testing](./statistical_analysis/README.md)**

The second phase of the project focuses on applying statistical inference techniques to the cleaned COVID-19 dataset. The objective is to understand population characteristics, quantify uncertainty, and investigate clinically relevant relationships between patient attributes and COVID-19 outcomes.

The analysis includes:

* Central Limit Theorem (CLT) simulation using patient age data
* Sampling distribution analysis for different sample sizes
* Standard Error estimation using theoretical and simulation-based approaches
* Bootstrap resampling for estimating sampling variability
* Construction of 95% confidence intervals
* Hypothesis testing using Welch's t-test
* Chi-square tests for associations between clinical variables and ICU admission

Key findings include:

* Sampling distributions become increasingly normal as sample size increases, providing empirical support for the Central Limit Theorem.
* Larger sample sizes produce more precise estimates, resulting in smaller standard errors.
* Bootstrap estimates closely match theoretical results, demonstrating the reliability of resampling methods.
* Age shows a strong association with ICU admission, with ICU patients being significantly older on average.
* Several clinical conditions, including diabetes, hypertension, pneumonia, and renal disease, exhibit significant relationships with severe COVID-19 outcomes.


## Authors

- **Porya Ardestani Samani**  
- **Tohid Nouri**
