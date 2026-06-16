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
- Predefined demographic groups may miss hidden failure strata in learned representations.
- Interventions that improve visible-group fairness may still worsen worst-group reliability under later shift.

## Connection to My Background

Facial age estimation is naturally connected to subgroup error because model performance can vary by age group, gender presentation, ethnicity, historical period, image quality, and cultural context. Historical domain shift can amplify these differences.

## What to Collect Daily

- Papers reporting subgroup performance under shift
- New fairness benchmarks with distribution shift
- Auditing work on demographic or intersectional errors
- Methods for robustness when subgroup labels are limited
- Evaluation guidelines for fairness reporting
- Hidden subgroup discovery methods that do not rely only on metadata labels

## Proposal Angles

- Subgroup-aware evaluation for temporal domain shift
- Fairness under historical distribution shift in visual recognition
- Monitoring subgroup error without immediate labels
- Data-centric analysis of demographic imbalance and temporal change
- Hidden-stratification diagnosis for historically shifted visual data

## Week 03 Stable Additions

- Subgroup definition should be treated as an experimental variable: age-only, age-gender, archive-period intersections, representation clusters, and hidden slices may lead to different conclusions.
- Balancing and fairness interventions should be evaluated under shift, because a visible-group improvement can still worsen worst-group or hidden-slice reliability.
- Subgroup reliability now includes uncertainty and calibration, not only prediction error: marginal coverage can hide group under-coverage in the same way global MAE can hide elderly-group degradation.
- For my thesis extension, elderly-group degradation should be tested as both a visible demographic disparity and a possible symptom of deeper hidden strata.

## Week 04 Stable Additions

- Fairness under shift is a burden-allocation problem, not only a gap-minimization problem: an intervention may move failure into coverage distortion, interval size, hidden-cluster error, or hard-example residuals.
- Visible subgroup labels are necessary but insufficient: label-free visual concept auditing and within-subgroup shift analysis can explain failures that age/gender tables only reveal after the fact.
- Balancing should be judged against corrected population baselines and hidden-subgroup outcomes, because coarse count balancing may leave target-mixture mismatch or within-elderly heterogeneity unresolved.
- Subgroup reliability should report coverage-size trade-offs alongside error gaps: marginal conformal coverage may hide elderly under-coverage, while group-specific calibration may increase interval burden for some groups.
