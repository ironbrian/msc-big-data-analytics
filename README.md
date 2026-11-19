# Predicting Childhood Obesity in the UK with Data Analytics

**MSc Big Data Analytics dissertation | University of Liverpool | October 2019**  
**Author:** Brian White

> **Research question:** *How can big data analytics help to solve the childhood obesity epidemic in the UK? A predictive model based on open data to empower health and education institutions.*

## Overview

This dissertation investigated whether publicly accessible research datasets and machine-learning techniques could help identify children at elevated risk of becoming overweight or obese. The work brought together longitudinal cohort data, demographic information and external indicators, then evaluated how different features and classification algorithms affected predictive performance.

The emphasis was on **practical data science**: sourcing and understanding complex datasets, preparing them for modelling, building repeatable analytical workflows, experimenting with feature selection and class balance, and interpreting the trade-offs between model accuracy and recall.

It was an academic research project, not a clinically validated prediction system or a deployed healthcare product.

## Technical stack

| Area | Technology or approach |
| --- | --- |
| Main modelling environment | **RapidMiner** |
| Early exploration | Python, Anaconda and Jupyter Notebook |
| Data preparation | CSV processing, joins, data typing, missing-value handling, deduplication and aggregation |
| Classification | Logistic Regression, Decision Trees, Random Forest, Naive Bayes, Support Vector Machines and Deep Learning |
| Feature analysis | Correlation-based weighting, Chi-squared weighting, PCA and feature selection |
| Evaluation | Accuracy, class precision, class recall and confusion matrices |
| Validation tooling | RapidMiner modelling and validation operators |
| Data | UK Millennium Cohort Study and historical Public Health England datasets |

**Implementation note:** The final experimental models were built primarily in **RapidMiner**. Python/Anaconda/Jupyter were explored early in the project, but the dissertation deliberately changed direction to RapidMiner to prioritise modelling and research within the available time. A cloud-based Python/Databricks/AWS implementation was considered but **not** built as part of the submitted work.

## Research methodology

1. **Literature review:** Compared existing academic approaches to predicting childhood obesity and identified commonly used candidate predictors.
2. **Data discovery:** Examined longitudinal cohort information and supplementary public-sector data, paying particular attention to completeness, accessibility and usable variables.
3. **Data preparation:** Joined Millennium Cohort Study survey datasets using cohort identifiers, selected relevant records, cleaned and transformed attributes, and prepared an overweight/obesity classification target.
4. **Feature engineering:** Extended established predictors with social, environmental and household attributes, including regional fast-food outlet density and reported social-media activity.
5. **Model development:** Established a Logistic Regression baseline, iteratively introduced additional attributes and compared alternative classification algorithms.
6. **Evaluation:** Analysed accuracy, precision and recall, explicitly considering the cost of false negatives and false positives when identifying potential risk.

The first Millennium Cohort Study survey contained **18,552 records** in the data examined. Joining to the later survey with the relevant obesity flag yielded an initial modelling dataset of **15,808 records**, before subsequent selection and preprocessing steps.

### Features investigated

- Child birth weight and subsequent weight gain
- Maternal and paternal body mass index (BMI)
- Breastfeeding and maternal smoking
- Household income, deprivation and education
- Family structure and parental working hours
- Ethnicity and language-related variables
- Regional density of fast-food outlets
- Body-fat percentage and reported social-media use

These are **observational candidate predictors**, not demonstrated causes of childhood obesity.

## Selected results

The models were assessed with an intentional emphasis on **positive-class recall**: identifying a high proportion of potentially at-risk children. This sometimes required accepting low overall accuracy and more false positives.

The dissertation reports the following selected RapidMiner results:

| Model / feature set | Accuracy | Positive-class recall |
| --- | ---: | ---: |
| Logistic Regression with primary attributes | 23.87% | 99.14% |
| Primary attributes + fast-food outlet density | 24.09% | 99.04% |
| Body-fat and social-media feature variant | **55.73%** | 88.02% |
| Extended key attributes | 26.15% | 96.65% |

Additional exploratory algorithm comparisons included Decision Trees, Random Forest, Naive Bayes, Support Vector Machines and a Deep Learning model. The dissertation used Logistic Regression as the principal basis for controlled feature comparison.

### What the results demonstrated

- **Recall versus accuracy:** The high-recall configurations could identify most positive cases within the evaluated samples, but their low accuracy would create substantial false-positive risk.
- **Feature selection matters:** Adding variables did not consistently improve performance; different configurations traded positive recall against other measures.
- **External data adds useful perspectives:** Environmental, household and online-activity attributes were worth investigating alongside conventional anthropometric predictors.
- **Data constraints drive engineering decisions:** Available variables, survey timing, regional aggregation and incomplete records constrained what could reasonably be inferred.

The figures above are the **historical experimental results reported in the 2019 dissertation**, not independently replicated results or a current benchmark. Configurations involved different feature sets and sampling choices and should not be interpreted as a validated clinical comparison.

## Engineering lessons

### Data preparation can outweigh modelling complexity

The most time-consuming work involved identifying usable fields across surveys, interpreting documentation and transforming inconsistent datasets. Cleaning, matching and feature preparation were central to the project.

### Choose tools appropriate to the problem

The original ambition included Python, distributed processing and cloud infrastructure. For a static, moderately sized research dataset and a fixed academic deadline, RapidMiner provided a more practical route to experimentation. This was a deliberate engineering trade-off rather than a requirement for maximum architectural complexity.

### Optimise for the actual outcome

Accuracy alone was not sufficient to evaluate the models. For a screening-oriented research question, positive-class recall was important, but a genuinely usable application would also need acceptable precision, calibration, validation and appropriate safeguards against unnecessary interventions.

### More data is not automatically better data

Long gaps between cohort surveys, limited geographic detail, missing variables and access restrictions all affected the scope and usefulness of the findings. In particular, a retrospective association does not automatically support accurate early prediction.

## Limitations and future work

The dissertation identified several constraints: limited time and computing resources, reliance on secondary datasets, inconsistent survey intervals, incomplete access to certain research datasets, and the absence of a live data-collection or intervention system.

Potential follow-on research includes:

- Repeating the study with more recent and representative data, subject to appropriate research permissions.
- Testing **XGBoost** and other models with rigorous validation and calibrated probability outputs.
- Investigating how models generalise across cohorts, geographies and demographic groups.
- Assessing bias, fairness, explainability and the practical consequences of false positives.
- Exploring longitudinal data capture and carefully governed, human-led decision support.

No claims are made here that those future systems were implemented as part of the dissertation.

## Data access, ethics and reproducibility

The work used Millennium Cohort Study material made available through the **UK Data Service** and historical **Public Health England** data. Access and reuse of source datasets are subject to the relevant provider terms. Raw individual-level cohort records should **not** be uploaded to a public GitHub repository.

The original analytical artefacts were RapidMiner processes (`.rmp`). This README is a research and technology overview; it does not imply that executable workflows, raw datasets or a reproducible software package have been published alongside it.

Before publishing the full dissertation PDF publicly, review it for personal identifiers and any material that should be redacted.

## About the author

**Brian White** — Data & AI engineering, enterprise data products and technology leadership.

- [GitHub](https://github.com/ironbrian)
- [LinkedIn](https://www.linkedin.com/in/brianawhiteuk/)

## Copyright

Copyright © 2019 Brian White. All rights reserved unless a separate licence is explicitly provided. The source datasets and cited academic works remain subject to their respective ownership and access terms.
