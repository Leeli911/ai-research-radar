# Representation Instability and Subgroup Degradation under Distribution Shift

Li Li

## 1. Background and Motivation

Machine learning systems are often evaluated under the assumption that test data are sufficiently representative of deployment data. My master's thesis, **From Faces to Ages: Enhancing Historical Recognition with Transfer Learning**, challenged this assumption in a concrete computer vision setting: facial age estimation on historically structured portrait data.

The thesis showed that aggregate evaluation can hide subgroup failure. A model may obtain a reasonable overall MAE while still producing high error for elderly subjects. It also showed that interventions intended to improve demographic balance can have unstable effects: dataset balancing sometimes worsened elderly-group performance. In addition, a cascaded gender-conditional model was fragile under shift, while simpler regression models generalized more reliably.

These findings motivate a broader research problem in trustworthy machine learning: distribution shift may not only reduce average performance, but also alter latent representations in ways that produce hidden subgroup-specific degradation. Standard aggregate metrics are insufficient for understanding this process.

中文说明: 我的 thesis 最重要的启发是，模型失败不是平均发生的。整体 MAE 可能看起来可以接受，但 elderly group 已经明显退化。更复杂的模型结构或数据平衡策略不一定更稳，反而可能在分布变化下暴露新的脆弱性。

## 2. Research Problem

**Main question:** How does distribution shift alter representation stability and induce hidden subgroup reliability degradation?

This project studies the link between three levels of model behaviour:

1. **Representation level:** how learned feature spaces change across domains or time periods;
2. **Subgroup level:** how these changes affect age groups, gender-conditioned groups, or hidden intersectional groups differently;
3. **Monitoring level:** how early signals of representation instability can be used to anticipate subgroup reliability degradation.

The central hypothesis is that subgroup failure under shift is partly driven by instability in latent representations. If a model's feature space changes unevenly across groups, then aggregate performance may remain acceptable while vulnerable subgroups experience larger error, poorer calibration, or higher uncertainty.

中文说明: 这个 proposal 的核心不是简单问“模型在新分布上准不准”，而是问：分布变化如何改变模型内部 representation？这种 representation instability 是否会让某些 subgroup 的误差上升？能不能提前监控这种风险？

## 3. Research Questions

**RQ1. Representation diagnostics**  
How do latent representations of facial age estimation models change across historical or domain-shifted data, and are these changes stronger for vulnerable subgroups?

**RQ2. Subgroup reliability profiling**  
Which subgroups experience the largest reliability degradation under distribution shift, and how much of this degradation is hidden by aggregate metrics such as MAE?

**RQ3. Intervention analysis**  
When do balancing, reweighting, or conditional routing improve subgroup reliability, and when do they amplify fragility?

**RQ4. Monitoring and anticipation**  
Can uncertainty, calibration, residual structure, or representation drift provide early warning signals for future subgroup degradation?

中文说明: 这些问题直接延伸我的 thesis。它们把原来的观察重新组织成 PhD-level questions：representation 是否不稳定？哪个 subgroup 退化最大？balancing 为什么有时失败？能否提前监控？

## 4. Methodology

### 4.1 Representation Diagnostics

The first stage will analyze representation stability across source and target domains. Candidate methods include feature-space distance, class-conditional embedding shift, neighborhood consistency, representation similarity analysis, and visualization of subgroup trajectories in latent space.

For historical facial age estimation, source and target domains may be defined by historical periods, dataset sources, or natural versus balanced data distributions. The analysis will compare whether elderly samples, gender-conditioned groups, or low-quality historical portraits move differently in representation space.

### 4.2 Subgroup Reliability Profiling

The second stage will profile subgroup-specific performance under shift. Metrics may include group-wise MAE, worst-group MAE, residual median, residual IQR, calibration error, error tail probability, and uncertainty by subgroup.

This stage directly extends my thesis evaluation pipeline, which already used subgroup-wise MAE, residual plots, calibration analysis, and model comparison. The goal is to formalize these diagnostics into a repeatable reliability profiling framework.

### 4.3 Temporal and Domain Shift Analysis

The third stage will study how subgroup reliability changes across time or domain boundaries. Possible settings include historical period splits, archival source splits, modern-to-historical transfer, and balanced-to-natural distribution transfer.

This stage will test whether subgroup degradation emerges gradually, whether it is linked to representation drift, and whether simple models remain more stable than cascaded or conditional models.

### 4.4 Uncertainty-Aware Monitoring

The final stage will explore monitoring signals that may anticipate subgroup degradation. Candidate signals include uncertainty growth, calibration mismatch, residual skew, feature-space drift, and divergence between global and subgroup-specific metrics.

The monitoring goal is decision-relevant: not merely to detect that a model changed, but to identify when subgroup degradation becomes large enough to require intervention, retraining, recalibration, or model redesign.

中文说明: 方法上，我会从四个层面做：看 representation 怎么变，看 subgroup error 怎么变，看 temporal/domain shift 下错误轨迹怎么变，再看 uncertainty 和 calibration 是否能提前预警。这个方法 realistic，因为它延续了我 thesis 里已经做过的 residual diagnostics、calibration analysis 和 subgroup evaluation。

## 5. Expected Contributions

This project is expected to contribute:

1. A diagnostic framework linking representation instability to subgroup reliability degradation under distribution shift.
2. Empirical evidence on how historical domain shift affects facial age estimation across age and gender-conditioned groups.
3. A systematic comparison of balancing, conditional routing, and simpler regression models under subgroup shift.
4. Monitoring indicators that connect representation drift, uncertainty, calibration, and subgroup error.
5. A decision-relevant evaluation perspective for trustworthy machine learning systems under changing data conditions.

中文说明: 预期贡献不是提出一个更大的模型，而是提出一套更清楚的诊断和评估方式。重点是解释模型为什么在某些 subgroup 上失败，以及如何在部署前或部署中提前发现这种失败。

## 6. Why This Direction Naturally Extends My Thesis

This direction naturally extends my thesis because it starts from the same empirical puzzle: aggregate performance can look acceptable while subgroup reliability deteriorates. My thesis provided the initial evidence through historical facial age estimation. This proposal generalizes that evidence into a broader trustworthy ML problem.

The thesis also showed that common solutions are not automatically reliable. Balancing may worsen elderly-group performance, and cascaded conditional models may amplify fragility. These observations motivate a deeper study of representation instability and subgroup monitoring under shift.

In this sense, my PhD direction is not a departure from my thesis. It is a methodological expansion: from evaluating age estimation models under historical shift to understanding and monitoring subgroup reliability degradation under distribution shift.

中文说明: 这个方向是我的 thesis 的自然延伸。我的 thesis 已经发现了问题：平均指标会隐藏 subgroup failure，balancing 不一定有效，复杂 conditional model 可能脆弱。PhD 阶段可以把这些观察上升为一个更系统的问题：distribution shift 如何改变 representation，并导致 subgroup-specific reliability degradation。

