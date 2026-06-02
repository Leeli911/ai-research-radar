# Deep Paper Card - FairTree Subgroup Bias-Variance Auditing

Title: FairTree: Subgroup Fairness Auditing of Machine Learning Models with Bias-Variance Decomposition
Authors: Rudolf Debelak
Year / Venue: 2026, arXiv preprint; ACM FAccT 2026 acceptance status needs conference-page verification
Link: https://arxiv.org/abs/2604.19357
Research function: Explanation
Usefulness: proposal anchor
Evidence status: arXiv abstract and daily-note metadata checked; full PDF, figures, tables, formulas, and appendix still need verification.

## Part 1: Literature Overview

### 1. Full Citation

Verified from paper:

Debelak, R. (2026). *FairTree: Subgroup Fairness Auditing of Machine Learning Models with Bias-Variance Decomposition*. arXiv:2604.19357. https://arxiv.org/abs/2604.19357

Needs full-paper verification:

- Final ACM FAccT 2026 proceedings citation.
- DOI, page numbers, and final camera-ready metadata if available.

### 2. Research Background

English:

Verified from paper:
FairTree addresses subgroup fairness auditing for machine learning models. The paper argues that existing auditing methods often require discretizing continuous variables, which can limit their ability to detect unfairness across subgroups defined by continuous, categorical, or ordinal covariates.

My interpretation:
This is directly relevant to subgroup-aware reliability diagnosis under distribution shift because many important failure axes in historical portrait data are not naturally discrete. Year, image quality, restoration artifacts, pose, and archival source can behave as continuous or mixed-type covariates. A method that avoids crude binning may help expose hidden subgroup degradation that ordinary age/gender tables miss.

中文:

这篇论文关注 subgroup fairness auditing。它的重要性在于，不是简单把人群切成几个固定 group 后比较误差，而是尝试更灵活地处理连续、类别和有序变量。对我的研究来说，这很有价值，因为 historical facial age estimation 里的失败轴可能不是简单的 age group 或 gender group，而是历史时期、图像质量、档案来源、修复痕迹等混合因素。

## Part 2: Core Logic

### 3. Core Hypothesis / Central Idea

Verified from paper:

FairTree adapts psychometric invariance testing to subgroup fairness auditing and decomposes prediction disparities into bias and variance components.

My interpretation:
The paper's central idea can help move my analysis from "which subgroup has higher error" to "what type of error structure makes this subgroup unreliable." This matters because elderly-group degradation in my thesis may reflect systematic underestimation, higher prediction variance, or both.

Needs full-paper verification:

- Exact mathematical definition of the bias and variance components.
- How the method handles model predictions across regression and classification tasks.
- Whether the method directly supports MAE-style age-estimation errors or needs adaptation.

### 4. Research Pathway

Research paradigm: diagnostic framework / algorithmic auditing method / empirical evaluation.

Verified from paper:

The paper proposes two FairTree variants: a permutation-based version and a fluctuation-test version. It evaluates them using simulations and a real-data case study.

My interpretation:
This pathway fits the problem because subgroup auditing is not only a prediction task. It is a diagnostic problem: the goal is to discover where disparity exists and whether the disparity comes from systematic bias or instability.

中文:

FairTree 更像 diagnostic framework，而不是一个普通预测模型。它的作用是帮助我解释 failure structure。对我的 thesis 来说，这比只报告 elderly-group MAE 更进一步，因为它可能区分 elderly group 的问题到底是系统性低估，还是模型在该组上的预测更不稳定。

### 5. Methodological Details

#### Object / Data

Verified from paper:

- Data setting: simulations and a UCI Adult real-data case study.
- Covariate types: continuous, categorical, and ordinal covariates are supported according to the abstract.

Needs full-paper verification:

- Simulation design details.
- UCI Adult preprocessing choices.
- Sample sizes.
- Protected attributes and covariates used.
- Whether temporal or distribution-shifted settings are directly evaluated.

#### Tools / Models

Verified from paper:

- Core method: FairTree.
- Variants: permutation-based FairTree and fluctuation-test FairTree.
- Comparator mentioned in the abstract: SliceLine.

Needs full-paper verification:

- Baseline list beyond SliceLine.
- Models audited in the experiments.
- Software implementation or code availability.

#### Technical Workflow

Verified from paper:

1. Use FairTree to audit subgroup fairness without requiring crude discretization of continuous predictors.
2. Decompose subgroup disparity into bias and variance components.
3. Compare the permutation-based and fluctuation-test variants through simulation.
4. Apply the method in a real-data UCI Adult case study.

My interpretation:

For my historical age-estimation setting, an adapted workflow could be:

1. Train or reuse age-estimation models from my thesis.
2. Use residuals, absolute error, or calibrated prediction error as the auditing target.
3. Feed age group, historical year, archive source, image quality proxies, and model type into a FairTree-like audit.
4. Ask whether elderly-group degradation is mostly bias, mostly variance, or a combined pattern.
5. Compare simple regression, balanced training, and cascaded models through the same audit.

## Part 3: Evidence and Findings

### 6. Core Findings

Verified from paper:

- The fluctuation-test version is reported to have higher power while maintaining satisfactory false-positive control.
- The paper reports that FairTree can handle multiple covariate types without discretization.
- The paper includes simulations and a UCI Adult real-data case study.

My interpretation:

The most useful finding for my research is not only that FairTree detects subgroup disparity, but that it decomposes disparity into bias and variance. This creates an explanation layer between diagnosis and intervention.

Needs full-paper verification:

- Exact power and false-positive rates.
- Quantitative differences between FairTree and SliceLine.
- Which figures or tables support the claims.

### 7. Key Evidence and Figure / Table Index

Needs full-paper verification:

Full figure/table verification needed.

Figure / Table list:

- Figure / Table number: Needs full-paper verification.
- What it shows: Needs full-paper verification.
- Why it matters: It should be used to verify the bias-variance decomposition and the power / false-positive behavior before citing the method in proposal text.

## Part 4: Critical Evaluation and Research Connection

### 8. Contributions and Limitations

#### Contributions

Verified from paper:

- Methodological contribution: subgroup fairness auditing with bias-variance decomposition.
- Practical contribution: support for continuous, categorical, and ordinal covariates without forced discretization.
- Empirical contribution: simulations and a UCI Adult case study.

My interpretation:

This method is strategically valuable because it strengthens the Explanation part of my conceptual chain. SHIFT helps ask who decays and why at a shift level. FairTree may help ask whether the subgroup failure itself is driven by systematic bias or instability.

#### Limitations

Needs full-paper verification:

- Whether FairTree has been tested under temporal or historical distribution shift.
- Whether the method is robust with small vulnerable subgroups.
- Whether it can be adapted cleanly to regression errors such as MAE.
- Whether subgroup discovery remains interpretable when covariates are noisy or proxy-based.

My interpretation:

Historical portrait data may stress the method. Age labels may be uncertain, subgroup labels may be incomplete, and image quality proxies may be noisy. FairTree could still be useful, but the adaptation should be framed as exploratory unless the statistical assumptions hold.

### 9. Connection to My Research

English:

My research direction is subgroup-aware reliability diagnosis under distribution shift. FairTree is useful because it adds an explanation layer to subgroup auditing. My thesis showed that aggregate MAE can hide elderly-group failure, but the thesis did not fully separate systematic underestimation from increased residual variance. FairTree gives me a vocabulary for asking whether elderly-group degradation is a bias problem, a variance problem, or a mixed reliability problem.

This also helps reinterpret balancing instability. If balancing worsened elderly-group performance, the failure may not simply be "more imbalance" or "less imbalance." It may have changed the bias-variance structure of errors in a vulnerable subgroup. That framing could make my proposal stronger because it turns a thesis anomaly into a testable research question.

中文:

FairTree 对我的价值在于补上 Explanation 这一环。我的 thesis 已经看到 elderly-group degradation，但还没有把这个 degradation 拆成 bias 和 variance。也就是说，我还没有完全回答：elderly group 是被系统性低估，还是预测方差变大，还是两者同时发生。

这对 balancing trade-off 也很重要。如果 balancing 之后 elderly error 变差，可能不是简单的“平衡没做好”，而是 balancing 改变了某个 subgroup 的误差结构。这个解释比单纯报告 MAE 更有 PhD proposal 价值。

### 10. How I Can Use This in My Proposal

Proposal argument supported by the paper:

Aggregate subgroup metrics are not sufficient for reliable model evaluation under shift. A stronger diagnostic framework should not only identify affected subgroups, but also explain whether subgroup failure reflects systematic bias, unstable variance, or both.

Possible proposal sentence:

> Building on recent subgroup auditing work that decomposes fairness disparities into bias and variance, my project will study whether historical domain shift in facial age estimation produces subgroup-specific reliability degradation through systematic underestimation, increased residual variance, or both.

Method or evaluation design I could adapt:

- Use FairTree-style subgroup auditing on residuals from age-estimation models.
- Compare simple regression, balanced training, and cascaded conditional models.
- Evaluate explicit age/gender subgroups and continuous historical covariates such as year or image-quality proxies.
- Report subgroup bias, residual variance, worst-group MAE, and calibration error.

Warning about limitations or overclaiming:

Do not claim FairTree solves historical domain shift. The safer claim is that FairTree provides a useful auditing lens that may be adapted to explain subgroup reliability degradation in historical visual data.

### 11. Inspiration and Backward Tracing

#### Inspiration

New research question:

Can bias-variance subgroup auditing detect elderly-group reliability degradation under historical domain shift earlier or more informatively than aggregate MAE and subgroup MAE tables alone?

Possible evaluation design:

Compare three reporting layers:

1. global MAE;
2. age/gender subgroup MAE;
3. FairTree-style bias-variance subgroup auditing.

Then test which layer best explains the thesis observations: elderly underestimation, balancing instability, and cascade fragility.

#### Must-read References

Needs full-paper verification:

1. SliceFinder / SliceLine literature.
   - Why it matters: FairTree is positioned against slice-finding approaches that may depend on discretization or search strategy.
   - Role in paper logic: baseline and methodological contrast.

2. Psychometric invariance testing literature.
   - Why it matters: FairTree adapts this logic to fairness auditing.
   - Role in paper logic: conceptual and statistical foundation.

Full reference details should be extracted from the FairTree bibliography before using these references in proposal writing.
