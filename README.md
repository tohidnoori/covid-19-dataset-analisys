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

## Data Understanding and Preprocessing

A major part of the homework is dedicated to understanding how the dataset is structured and how missing values should be interpreted.

### Missing Data Analysis

The assignment examines missing values across the dataset and shows that some columns have very high missingness:

- `died_date`: about **93.62%** missing
- `intubed`: about **78.51%** missing
- `icu`: about **78.51%** missing
- `pregnancy`: about **50.95%** missing
- `contact_other_covid`: about **30.89%** missing

The report explains that these missing values are not always random. For example:

- `died_date` being missing often means the patient survived.
- `intubed` and `icu` are often only meaningful for hospitalized cases.

## Data Cleaning Strategy

The cleaning process is based on domain logic rather than simple deletion.

### Pregnancy
Since men cannot be pregnant, missing values for male patients are treated as a data quality issue and filled as **No**.

### Contact with Other COVID Cases
Missing values in `contact_other_covid` are filled with **Unknown** so that missing information is preserved as a separate category instead of being confused with a confirmed negative response.

### Binary Clinical Features
For clinical binary variables such as:

[`diabetes`,`copd`,`asthma`,`inmsupr`,`hypertension`,`other_disease`,`cardiovascular`,`obesity`,`pneumonia`,`renal_chronic`,`tobacco`]

missing values are treated as **No**.

### Outcome Construction
A new binary target variable named `died` is created:

- `1` = patient died
- `0` = patient survived

After that, `died_date` is no longer used as a raw feature and is replaced with a clean binary outcome representation.

### Intubation and ICU
For outpatient cases, `intubed` and `icu` are considered not applicable, so missing values are filled as **No** or **Not Admitted**, depending on the field.

After cleaning:

- the dataset still has **566,602 records**
- **no missing values remain**
- all categorical variables are in usable form for analysis and modeling

## Feature Encoding

To prepare the data for machine learning, categorical variables are converted into numeric form.

### Manual Encoding
Some variables are encoded manually:

- `sex`: `male -> 2`, `female -> 1`
- `pregnancy`: `Yes -> 1`, `No -> 0`

### Label Encoding
Other categorical features are label-encoded, including:

- `diabetes`
- `copd`
- `asthma`
- `hypertension`
- `cardiovascular`
- `obesity`
- `renal_chronic`
- `inmsupr`
- `other_disease`
- `tobacco`
- `contact_other_covid`
- `covid_res`
- `pneumonia`
- `intubed`
- `icu`
- `patient_type`

## Time Feature Engineering

Date columns are converted to `datetime` format and then transformed into numeric timestamp values. This makes the dataset fully numeric and easier to use in downstream modeling.

The assignment notes that `date_of_death` is not used directly because the new `died` variable already summarizes the key outcome.

## Exploratory Data Analysis

The report includes descriptive analysis of the cleaned dataset.

### Target Distribution

The `died` target is highly imbalanced:

- `died = 0`: **530,426**
- `died = 1`: **36,176**

This corresponds to:

- **93.61% survival**
- **6.39% mortality**

The class imbalance ratio is approximately **1:14.7**, which is important for any later modeling stage.

### Histograms

Histograms are generated for all numeric features to inspect:

- distribution shape,
- skewness,
- spread,
- and outliers.

Key observations include:

- `age` is roughly symmetric and close to normal,
- binary medical features are strongly imbalanced,
- date/timestamp features are skewed.

## Main Takeaways

This homework demonstrates a complete preprocessing pipeline for a real-world medical dataset. The key ideas are:

- using clinical logic to interpret missing data,
- cleaning and imputing values carefully,
- encoding categorical variables for modeling,
- engineering useful time-based features,
- and understanding class imbalance before building predictive models.

## Authors

- **Porya Ardestani Samani**  
- **Tohid Nouri**
