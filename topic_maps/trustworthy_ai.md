# Topic Map - Trustworthy AI and Model Monitoring

## Purpose

Track methods and evaluation practices that make AI systems more reliable, auditable, and useful in high-stakes or changing environments.

中文定位: 这条主线可以把技术问题提升为 PhD 申请中更有广度的研究叙事, 但要避免写得太泛。

## Core Questions

- What makes a model trustworthy in deployment?
- How should reliability, uncertainty, calibration, and monitoring be evaluated?
- How can model failures be detected before they affect users?
- How can audits reveal hidden risks in model behavior?
- What evidence is needed before a model can support decisions?

## Keywords

- trustworthy machine learning
- model monitoring
- uncertainty estimation
- calibration
- model auditing
- data quality
- reliability evaluation
- robustness
- risk assessment

## Datasets and Benchmarks to Watch

- Reliability and calibration benchmarks
- Dataset shift benchmarks
- Monitoring datasets with delayed labels
- Auditing datasets with demographic or subgroup metadata
- Data quality benchmarks

## Evaluation Metrics

- Calibration error
- Selective risk
- Coverage
- Detection delay
- False positive and false negative monitoring alerts
- Worst-case or subgroup performance
- Reliability under shift

## Open Research Gaps

- Trustworthy AI is often too broad unless tied to a concrete evaluation setting.
- Monitoring papers may not address what happens after an alert.
- Calibration can fail under distribution shift.
- Auditing methods often lack decision-relevant criteria.
- Many studies do not connect technical metrics to stakeholder needs.

## Connection to My Background

Facial age estimation under historical domain shift is a concrete example of why model monitoring matters: a model can appear strong on historical test data but fail when the population, image style, or collection process changes.

## What to Collect Daily

- Papers on uncertainty under shift
- Monitoring methods for deployed models
- Auditing frameworks with technical evaluation
- Data-centric methods for diagnosing reliability problems
- Case studies where model performance changes over time

## Proposal Angles

- Model monitoring for temporal and subgroup shift
- Auditing visual models for hidden demographic performance gaps
- Decision-relevant reliability metrics for trustworthy ML
- Data-centric diagnosis of model failures after deployment

## Week 03 Stable Additions

- Trustworthy monitoring should include subgroup alert timing: the useful signal is whether subgroup degradation appears before global performance changes.
- Uncertainty-aware monitoring is now central to this map: group coverage gaps, adaptive conformal thresholds, and subgroup interval efficiency can reveal hidden reliability failure.
- Model maintenance should be evaluated separately for population-level performance and subgroup reliability, because updates can improve global metrics while leaving subgroup gaps unresolved or worse.
- For my thesis extension, a trustworthy age-estimation system should report residual drift, subgroup calibration, coverage gaps, and temporal validity, not only MAE.

## Week 04 Stable Additions

- Trustworthy monitoring should track where reliability burden moves after an intervention: residual error, subgroup miscoverage, interval width, deferral rate, hidden-cluster failure, or route-specific fragility.
- Conformal and selective-prediction guarantees need subgroup trust boundaries: a marginal guarantee is not enough if elderly or historically shifted portraits are under-covered or systematically deferred.
- Decision-relevant reliability should connect uncertainty signals to action rules, such as manual review, abstention, interval widening, or localized recalibration, rather than only reporting a calibration number.
- For my thesis extension, a trustworthy historical age-estimation audit should combine target-mixture baseline checks, residual diagnostics, hidden concept or cluster analysis, and subgroup coverage monitoring.
