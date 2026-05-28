# Topic Map - Fairness, Subgroup Error, and Evaluation

## Purpose

Study how model errors differ across groups, especially when data distributions change over time, across contexts, or across deployment populations.

中文定位: 这条线能把我的 thesis 从 "domain shift" 扩展到 "谁受到错误影响", 很适合 proposal 和面试表达。

## Core Questions

- Which subgroups experience the largest performance degradation under shift?
- How can subgroup error be measured when labels or group attributes are incomplete?
- How does distribution shift interact with fairness metrics?
- Can evaluation protocols reveal hidden harms before deployment?
- How should subgroup robustness be reported in research papers?

## Keywords

- subgroup robustness
- fairness under distribution shift
- worst-group accuracy
- demographic shift
- model bias
- group calibration
- error disparity
- intersectional evaluation

## Datasets and Benchmarks to Watch

- Vision datasets with demographic metadata
- Medical AI datasets with site or demographic shifts
- Fairness benchmarks with subgroup labels
- Temporal datasets where subgroup composition changes
- Auditing datasets for deployed models

## Evaluation Metrics

- Worst-group accuracy
- Group-wise error rate
- Equalized odds gap
- Calibration by group
- Subgroup performance under shift
- Error concentration
- Robustness gap between average and worst subgroup

## Open Research Gaps

- Many papers report average performance but hide subgroup failures.
- Group labels are often incomplete, noisy, or ethically sensitive.
- Fairness metrics may change when the deployment distribution shifts.
- Subgroup analysis can become descriptive unless connected to intervention.
- Benchmarks often underrepresent temporal and historical change.

## Connection to My Background

Facial age estimation is naturally connected to subgroup error because model performance can vary by age group, gender presentation, ethnicity, historical period, image quality, and cultural context. Historical domain shift can amplify these differences.

## What to Collect Daily

- Papers reporting subgroup performance under shift
- New fairness benchmarks with distribution shift
- Auditing work on demographic or intersectional errors
- Methods for robustness when subgroup labels are limited
- Evaluation guidelines for fairness reporting

## Proposal Angles

- Subgroup-aware evaluation for temporal domain shift
- Fairness under historical distribution shift in visual recognition
- Monitoring subgroup error without immediate labels
- Data-centric analysis of demographic imbalance and temporal change
