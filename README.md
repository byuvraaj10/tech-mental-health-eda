# Workplace Resources and Willingness to Speak Out: A Study of Mental Health in Tech

## Project Overview
This project, authored by **The Real Ricardo**, is an exploratory data analysis (EDA) of **Mental Health in Tech**. The core investigation focuses on the relationship between an employee's perception of workplace mental health resources and their willingness to seek treatment or speak out.

## Data Source
The data was sourced from a 2014 survey conducted by **OSMI** (Open Sourcing Mental Illness), a non-profit organization dedicated to raising awareness, educating, and providing resources to support mental wellness in the tech and open-source communities.
* **Original Data Link:** [Kaggle - Mental Health in Tech Survey](https://www.kaggle.com/osmi/mental-health-in-tech-survey)

---

## Data Cleaning and Preprocessing Summary

### 1. Column Exclusion
I dropped the **timestamp, country, state, and comments columns**. I decided not to use them because the dataset lacked sufficient location data to perform a meaningful geographical analysis.

### 2. Age Cleaning
I found weird ages (like `99999999` and `-1729`), so I'm only keeping **valid numbers** in the age column. (Ages outside the 0-100 range were replaced with nulls and subsequently removed).

### 3. Gender Standardization
The **Gender** column was chaotic, but I tackled it by **making everything lowercase and stripping spaces** to clean up the options. A custom function standardized over 40 unique entries into three primary categories: **'male', 'female', or 'other'**.

### 4. Data Refinement
* **Self-Employed Exclusion:** All respondents who identified as self-employed were dropped from the final analysis, as the central question relies on data related to *employer-provided* resources.
* **Missing Values:** Missing data in the `work_interfere` and `self_employed` columns were replaced with **"Don't know"**.
* **Uncertainty Unification:** All uncertain answers (like 'Maybe', 'Some of them', and 'Not sure') were uniformly mapped to **"Don't know"** across all categorical columns.
* **Care Options:** The **'Don't know'** responses in the `care_options` column were conservatively interpreted as **'No'** for the purpose of assessing resource availability.

---

## Key Findings

Two new composite scores were created for the analysis: `workplace_resources` (a composite score of perceived resources) and `willingness` (a composite score of the likelihood of seeking help/treatment).

### 1. Workplace Resources Directly Impact Care Awareness
A clear **positive correlation** exists between an employee's perceived level of mental health resources and their awareness of care options.
* For the group with the **lowest** perceived resources (score -6), only **40%** were aware of care options.
* For the group with the **highest** perceived resources (score 6), nearly **87%** were aware of care options.

### 2. Increased Resources Drive Higher Willingness to Seek Help
The analysis suggests a strong **positive relationship** between the `workplace_resources` score and the `willingness` score.
* **As the perceived level of mental health resources increases, employees show a higher average willingness to seek treatment or speak out.**
* The mean willingness score increased from **-2.6** at the lowest resource level to **0.35** at the highest resource level.

### 3. Family History is a Strong Predictor of Seeking Treatment
An individual's willingness to seek treatment is significantly influenced by whether they have a family history of mental illness.
* Respondents with a family history who are **already seeking treatment** have the **highest average willingness score** (close to 1.0).
* Respondents **without** a family history who are **not** seeking treatment have the **lowest average willingness score** (close to 0.0).
