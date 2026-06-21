# Weekly Research Summary - Week 05

Week: 05
Date range: 2026-06-15 to 2026-06-21
Daily notes reviewed: 2026-06-15, 2026-06-16, 2026-06-17, 2026-06-18, 2026-06-19, 2026-06-20, 2026-06-21
New paper cards reviewed: none
Main research identity: hierarchical, mechanism-matched subgroup reliability under distribution shift

Main purpose: synthesize this week's papers into a proposal direction that moves from aggregate masking to within-subgroup failure, source-target support diagnosis, and early reliability monitoring.

## 1. What Became Clearer This Week?

English:

This week clarified that subgroup evaluation is not the endpoint of reliable evaluation. Global metrics can hide elderly-group degradation, but an elderly-group mean can also hide a small tail of severe failures. Even a subgroup-aware intervention can then fail if the target archive, period, or visual regime is absent from training. The resulting hierarchy is: global-to-group masking, within-group tail failure, and source-target support failure.

The second clarification is methodological. No monitoring or intervention method is reliable in the abstract. Missingness-aware calibration helps when uncertainty regimes differ by missingness; failure-score aggregation helps when confidence signals are complementary; invariant objectives help only when their stability assumptions hold; and reweighting cannot recover an unsupported target domain. My proposal should therefore diagnose the shift mechanism before selecting a monitoring or intervention tool.

中文:

这周最清楚的推进是：subgroup evaluation 不是 reliable evaluation 的终点。Global metric 会掩盖 elderly-group degradation，但 elderly-group mean 仍可能掩盖少量 severe failure；即使采用 subgroup-aware intervention，如果目标 archive、historical period 或 visual regime 在训练中没有 support，方法仍然会失败。因此我现在看到的是一个三层结构：global-to-group masking、within-group tail failure、source-target support failure。

第二个推进是 method 必须和 failure mechanism 匹配。Missingness heterogeneity、visual silent failure、spurious-correlation shift 和 unsupported domain 需要不同的诊断与干预。我的 proposal 不应预设一个 universally robust method，而应先识别 shift，再选择假设可验证的 monitoring 或 intervention。

## 2. Technical Patterns

### Pattern 1: Distribution shift is multi-axis and context-conditioned

English:

The papers repeatedly reject a single source-target split. Concurrent domain and spurious-correlation shifts, cross-country population differences, hospital or archive-source changes, temporal windows, image quality, and subgroup composition can interact. In several studies, deployment context or source support mattered more than model class.

中文判断:

Historical portrait shift 应被写成 period × archive source × age × gender × image quality 的组合问题，而不是一个笼统的 historical-vs-modern domain gap。对我的 thesis 而言，elderly degradation 很可能是多个 shift 叠加后的 interaction effect。

### Pattern 2: Hidden failure has a hierarchy

English:

Multimodal slice discovery, DuetFair, intersectional GroupDRO, and local-window evaluation converge on the same structure. Aggregate scores hide subgroup failure; named subgroup means hide hard cases or intersectional cells; and local time or source windows can hide failure even after subgroup reporting. Tail error, worst-cell error, residual distributions, and bootstrap uncertainty are therefore necessary complements to subgroup means.

中文判断:

我的 thesis 已经证明 global MAE 会掩盖 elderly error。新的推进是：elderly mean MAE 本身也是 aggregate metric。我需要继续检查 elderly 组内的 90th-percentile error、underestimation tail、archive-age cell 和 hidden slice，而不是把 elderly 当成 homogeneous group。

### Pattern 3: Reliability monitoring is moving toward mechanism-matched early warning

English:

This week's monitoring methods include subgroup-conditional shift attribution, hidden-slice discovery, subgroup conformal coverage, confidence-score aggregation, reliability trajectories, and label-free target-risk estimation. The strongest shared lesson is that a drift signal is not automatically a failure signal. Monitoring must be evaluated against actual subgroup errors, coverage gaps, lead time, false alarms, and selective-risk consequences.

中文判断:

我不能假设 representation distance、uncertainty 或 marginal coverage 自动代表 elderly reliability。每个 signal 都必须回答一个具体问题：它能否在 global MAE 改变前发现 elderly underestimation，并且不会通过 deferral 或 interval width 把 burden 再次转移给 vulnerable subgroup？

### Pattern 4: Data and robustness interventions have non-monotonic effects

English:

Coreset selection, data addition, balancing, GroupDRO, calibration, and conditional routing can help or harm depending on sample composition, intervention strength, within-group variation, and target support. Moderate group emphasis can improve a vulnerable intersection, while excessive regularization or uniformization can reverse the gain. More data cannot compensate for an unseen target regime.

中文判断:

这直接重读我的 balancing instability。Balancing 不是 binary choice，而是 intervention strength、source composition、within-elderly coverage 和 target support 的联合函数。评估必须包含 intervention sweep，而不是只比较 balanced 与 unbalanced 两个点。

### Pattern 5: Simple baselines remain a reliability requirement

English:

The weak-supervision and invariant-learning papers reinforce my thesis result that simpler models can generalize better. Complex predictors can exploit unstable features, robustness penalties can collapse without changing representations, and hard routing can amplify upstream errors. A simple regression baseline is therefore not a weak comparator; it is an assumption check for every proposed reliability method.

中文判断:

我的 proposal 应把 simple regression 设为强 baseline，并显式检查 feature stability、penalty dynamics、routing error 和 route-specific calibration。只有复杂方法在这些诊断上也更可靠时，architecture complexity 才有价值。

## 3. Conceptual Chain Coverage

- Diagnosis: strengthened by multimodal slice discovery, subgroup-conditional shift attribution, within-subgroup tail analysis, source-support checks, and shift-mechanism diagnostics.
- Explanation: strengthened by representation instability, spurious evidence, source-composition mismatch, route error propagation, and robustness-objective assumption failure.
- Intervention: strengthened by source-aware data selection, subgroup calibration, soft or probabilistic conditioning, regularized GroupDRO, and locally adaptive policies.
- Monitoring: strengthened most strongly by subgroup coverage gaps, failure-score aggregation, label-free target-risk estimation, reliability volatility, and early-warning evaluation.
- Evaluation: strengthened by concurrent-shift grids, local source-period windows, worst-cell and tail metrics, coverage-width trade-offs, selective risk, and bootstrap stability.

Gap this week:

The literature supplies many monitoring signals, but no paper directly validates a compact regression-ready pipeline for historical facial age estimation. The immediate gap is experimental integration: one controlled protocol must connect shift characterization, hierarchical subgroup metrics, early-warning signals, and intervention comparison without creating method sprawl.

中文判断:

这周不是缺少 idea，而是缺少压缩。下一步应把大量方法压缩为一个 historical age regression protocol：先定义 source-period shift，再报告 global/group/tail 三层 error，然后比较少量 monitoring signals，最后只测试与诊断机制匹配的 intervention。

## 4. Conceptual Shifts

### Shift 1

From: burden-aware subgroup diagnosis
To: hierarchical reliability diagnosis

English:

Week 04 asked where reliability burden moves after an intervention. Week 05 adds where it can remain hidden: below the global metric, inside the named subgroup, or outside the support of the training distribution.

中文:

Week 04 的核心是 burden movement；Week 05 的推进是 burden hiding 的层级。Failure 不只会从 global 移到 subgroup，还可能继续隐藏在 subgroup tail，或者来自训练数据完全没有覆盖的 target domain。

### Shift 2

From: subgroup-aware method selection
To: mechanism-matched reliability evaluation

English:

My question is no longer which fairness, uncertainty, or robustness method is strongest on average. It is which method's assumptions match the observed shift mechanism, and how failure is detected when those assumptions are violated.

中文:

我不再问哪个 fairness、uncertainty 或 robustness 方法平均最强，而是问它的假设是否匹配真实 shift mechanism，以及假设失效时能否被诊断出来。

### Shift 3

From: retrospective subgroup auditing
To: prospective, partly label-free early warning

English:

The EPA, ShapShift, conformal, and failure-detection papers move my direction toward deployment-time estimation before target labels arrive. This is strategically stronger than only explaining elderly residuals after evaluation labels are available.

中文:

我的方向从 retrospective audit 推向 prospective monitoring：在 target label 尚未到达时，利用 prediction、uncertainty、quality、metadata 和 representation moments 估计 elderly reliability risk，并在标签揭示后验证 early-warning quality。

## 5. Tensions and Open Problems

### Tension 1: Conditional modeling can help or amplify fragility

Soft, probabilistic, or stable-metadata conditioning improved robustness in several papers, while my hard gender-conditional cascade was fragile. The unresolved variable is not conditioning itself, but routing stability, observability of the routing attribute, source support, and whether route-specific error is monitored.

### Tension 2: Subgroup protection can create subgroup burden

Mondrian calibration and GroupDRO can improve the vulnerable group, but small calibration sets can widen intervals and concentrated DRO weights can destabilize other groups. Coverage, interval width, effective sample size, tail error, and non-elderly performance must be reported together.

### Tension 3: Hidden-slice discovery improves diagnosis but may weaken interpretability

Automatically discovered slices can reveal failure beyond age and gender, but unstable or opaque clusters are weak proposal evidence. Slice stability, semantic coherence, repeated-run agreement, and injected-failure recovery are required before a hidden slice is treated as a meaningful subgroup.

### Tension 4: Label-free monitoring may reproduce routing error

Estimating elderly risk without target age labels may require predicted group membership. That prediction can itself drift, recreating the cascade problem. Global and probabilistic age-conditioned estimates should be compared, with routing uncertainty and effective sample size reported explicitly.

## 6. Strongest Papers This Week

### Paper 1

Title: DuetFair: Coupling Inter- and Intra-Subgroup Robustness for Fair Medical Image Segmentation
Link: https://arxiv.org/abs/2605.10521
Research function: Intervention
Usefulness: proposal anchor
Why it matters: It provides the clearest concept for the new layer of aggregate masking: a subgroup mean can hide severe within-subgroup failures.
Connection to my thesis: Elderly mean MAE may conceal a smaller hard tail defined by archive source, quality, pose, gender, or period.
Limitation: It requires subgroup attributes and uses a routing/DRO architecture that may repeat my cascade fragility if routing is unstable.
中文判断: 这是本周最强的 conceptual anchor，但我应先借用 dual-axis evaluation，而不是直接采用复杂 routing architecture。

### Paper 2

Title: Missingness-Aware Conformal Prediction Under Cross-Hospital Distribution Shift
Link: https://openreview.net/forum?id=h2I7GN4hTh
Research function: Diagnosis
Usefulness: proposal anchor
Why it matters: It formalizes aggregate masking as marginal coverage hiding subgroup undercoverage and offers a feasible grouping-and-calibration design.
Connection to my thesis: It converts global MAE masking into a subgroup-valid residual-coverage question for elderly portraits.
Limitation: Small elderly calibration sets may produce unstable or excessively wide intervals, and the current evidence is workshop-level.
中文判断: 这篇最适合把我的 residual diagnostics 推进为 uncertainty-aware evaluation。

### Paper 3

Title: A multimodal slice discovery framework for systematic failure detection and explanation in medical image classification
Link: https://arxiv.org/abs/2602.24183
Research function: Diagnosis / Monitoring
Usefulness: proposal anchor
Why it matters: It gives a concrete pipeline for discovering failure slices that predefined age and gender groups miss.
Connection to my thesis: Image embeddings plus archive metadata and quality descriptors could identify elderly-adjacent slices with concentrated underestimation.
Limitation: Historical portrait metadata may be much sparser than medical reports and metadata, and discovered slices require stability checks.
中文判断: 它支持 hidden-slice auditing，但在 deep read 前不应把自动聚类当成稳定 subgroup 定义。

### Paper 4

Title: Investigating Data Interventions for Subgroup Fairness: An ICU Case Study
Link: https://arxiv.org/abs/2604.03478
Research function: Diagnosis / Intervention / Evaluation
Usefulness: proposal anchor
Why it matters: It directly shows that adding or balancing data can create volatile subgroup outcomes when source composition shifts.
Connection to my thesis: It gives the strongest external analogy for why age balancing could worsen elderly-group reliability.
Limitation: The clinical tabular setting must be translated into archive source, period, quality, and age-bin structure.
中文判断: 这篇最适合支撑“更多或更平衡的数据不自动等于更可靠的数据”。

### Paper 5

Title: Entropic Projection Alignment: Estimating, Explaining, and Improving Model Performance Under Distribution Shift
Link: https://arxiv.org/abs/2605.31250
Research function: Monitoring / Explanation
Usefulness: monitoring method reference
Why it matters: It turns unlabeled target data into a risk-estimation and shift-explanation signal using controlled moment matching.
Connection to my thesis: An age-conditioned extension could estimate elderly MAE or underestimation before later-period labels arrive.
Limitation: The paper is tabular and mainly estimates global risk; subgroup-conditioned image monitoring is a new research problem, not a direct application.
中文判断: 这篇给 proposal 增加 prospective monitoring，但技术风险高于前四篇，应从简单 quality/prediction moments 开始。

## 7. Strongest Connections to My Thesis

### Aggregate masking

English:

This week expands aggregate masking into a hierarchy. Global MAE can hide elderly degradation; elderly mean MAE can hide high-error tails and intersectional cells; marginal coverage can hide subgroup undercoverage; and a global target-risk estimate can hide elderly-specific decline.

中文:

Aggregate masking 现在不只是 global-vs-group，而是 global -> subgroup -> within-subgroup tail -> target-support 的多层问题。我的 evaluation panel 必须同时报告 global MAE、elderly MAE、worst archive-age cell、elderly tail error 和 subgroup coverage。

### Balancing instability

English:

Balancing instability now has four candidate mechanisms: selected-sample composition, source incompatibility, loss of within-elderly variation, and non-monotonic intervention strength. The correct experiment is an intervention sweep under matched source-period shifts, not a single balanced-versus-unbalanced comparison.

中文:

Balancing 可能因为 sample selection、source mismatch、within-elderly diversity loss 或 intervention strength 过强而失败。这比“balancing 有效或无效”的二元判断更接近我的实证结果。

### Subgroup degradation

English:

Elderly-group degradation should be treated as both a visible disparity and a possible container for narrower hard cases. The strongest explanatory variables this week are archive/period support, image quality, hidden visual slices, representation stability, and route-specific error propagation.

中文:

Elderly group 是可靠性问题的入口，不是最终粒度。真正的 failure 可能集中在 elderly × archive source × quality × gender 的少数 cell，或者集中在 hard-routing error 与 high-residual tail 中。

### Simpler-model stability

English:

The simple regression result in my thesis gains a stronger interpretation: simplicity may reduce dependence on unstable features, avoid penalty or routing failure, and produce smoother reliability across source-period windows. This remains an empirical hypothesis that should be tested through feature stability and reliability volatility.

中文:

Simple regression 可能更稳，不只是因为参数少，而是因为它更少依赖 unstable feature、hard route 和脆弱 objective。这个解释需要用 feature stability、route error 和 window-level reliability volatility 验证。

## 8. Top 3 Research Directions

### Rank 1

Working title: Hierarchical subgroup reliability auditing for historical facial age estimation

Research question: Under archive-source and historical-period shift, can a three-level audit using subgroup residuals, elderly tail error, and worst archive-age cells detect reliability degradation and model-ranking reversals that global MAE and elderly mean MAE miss?

Why it matters: This is the most direct extension of my thesis and the clearest conceptual contribution from this week. It makes the hierarchy of hidden failure testable without requiring a new architecture.

Possible data: My historical portrait dataset with age, gender, archive source or period, image-quality descriptors, model predictions, residuals, and embeddings; controlled blur, contrast, compression, and noise shifts can supplement naturally occurring shift.

Possible method: Compare simple regression, multi-task, and cascaded models across repeated source-period splits. Report global, elderly, intersectional, and within-elderly-tail outcomes; add image-plus-metadata slice discovery only as a secondary diagnostic.

Evaluation metric: Global and elderly MAE, elderly 90th-percentile absolute error, underestimation rate, worst archive-age cell MAE, residual variance, model-ranking reversal frequency, bootstrap confidence intervals, and hidden-slice stability.

Thesis connection: Directly extends aggregate masking, elderly degradation, cascade fragility, and simpler regression stability.

Risk or limitation: Sparse elderly cells can make tail estimates unstable. Minimum-support rules, hierarchical shrinkage, repeated splits, and bootstrap intervals are required.

Strategic fit: Very high
Feasibility: High
Proposal potential: Very high

中文判断: 这是第一方向，因为它最贴近我的 thesis、实验上可执行，而且不依赖先发明复杂方法。它可以成为 proposal 的 evaluation core。

### Rank 2

Working title: Mechanism-matched early warning for hidden elderly degradation

Research question: Which deployment signal—subgroup conformal coverage, residual-history statistics, ensemble variance, shift attribution, or moment-matched target-risk estimation—detects elderly underestimation earliest under historical visual shift without disproportionately widening intervals or deferring elderly portraits?

Why it matters: This turns my retrospective residual finding into a prospective monitoring problem and directly tests whether a signal matches the actual failure mechanism.

Possible data: Earlier-period labeled portraits and later-period target portraits whose labels are hidden during monitoring and revealed for retrospective evaluation; source/period/quality shifts define monitoring windows.

Possible method: Start with pooled and age/quality-aware conformal intervals, residual-history baselines, ensemble variance, and simple quality/prediction moment matching. Add subgroup-conditioned risk estimation only after the global estimator is stable.

Evaluation metric: Detection lead time, elderly failure AUROC, subgroup AUGRC, harmful-shift detection power, false-positive rate, elderly coverage gap, interval width, deferral disparity, and effective sample size.

Thesis connection: Extends aggregate masking, calibration analysis, residual diagnostics, and decision-relevant monitoring.

Risk or limitation: Target age labels and true elderly membership are unavailable online. Probabilistic subgroup membership can recreate routing fragility and must be audited explicitly.

Strategic fit: Very high
Feasibility: Medium
Proposal potential: Very high

中文判断: 这是第二方向，因为它比静态 audit 更有 PhD novelty，但 label-free subgroup estimation 的技术风险更高，需要从简单 baseline 开始。

### Rank 3

Working title: Mechanism-aware stress testing of data and routing interventions

Research question: When do source-aware selection, age balancing, regularized group reweighting, and soft uncertainty-aware routing reduce elderly tail error under historical shift, and when do they worsen reliability because within-group variation or target-domain support is missing?

Why it matters: This directly explains my most distinctive thesis puzzle—balancing and conditional complexity can harm the vulnerable subgroup—while avoiding architecture novelty as the main contribution.

Possible data: Original and intervention-specific training subsets from my historical portrait data, organized by age, gender, archive source, period, quality, and discovered stable slices.

Possible method: Use a fixed simple backbone and compare no intervention, naive age balancing, source-aware selection, a small regularization-strength sweep for group reweighting, hard gender routing, and soft routing. Match training budget and source coverage across conditions.

Evaluation metric: Elderly mean and 90th-percentile error, worst-cell MAE, residual skew, calibration/coverage, intervention ranking stability, routing error, effective sample size, and non-elderly performance.

Thesis connection: Directly tests balancing instability, cascade fragility, subgroup degradation, and simpler-model reliability.

Risk or limitation: The intervention grid can become too large. The first study should include only one data intervention, one reweighting baseline, and hard-versus-soft routing after Rank 1 identifies the dominant failure mechanism.

Strategic fit: Very high
Feasibility: Medium-high
Proposal potential: High

中文判断: 这是第三方向，因为它非常贴合 thesis，但必须服从 diagnosis。若没有先识别 shift mechanism，方法比较会重新变成 method zoo。

## 9. Topic Map Updates

English:

I did not update any topic map this week. The notes produced a promising new structure—global-to-group masking, within-subgroup tail failure, and source-target support diagnosis—but no new deep paper card was reviewed. Under the repository rule, topic maps should change only after deep reading verifies that a concept is stable enough to affect the long-term map.

Candidate additions after deep reading:

- `topic_maps/distribution_shift.md`: source-target support diagnosis and mechanism-matched monitoring.
- `topic_maps/fairness_subgroup_error.md`: within-subgroup hidden failure and tail-aware subgroup evaluation.
- `topic_maps/trustworthy_ai.md`: label-free subgroup early warning evaluated by lead time, false alarms, coverage, and deferral burden.

I did not identify a stable new structure for `topic_maps/ai_governance.md` or `topic_maps/multimodal_authenticity.md`.

中文:

本周不更新 topic maps。虽然已经出现 global-to-group、within-group tail、source-target support 的新结构，但还没有对应 deep paper card 完成验证。等 DuetFair 或 Missingness-Aware Conformal Prediction 完成 deep read 后，再决定是否把该结构写入长期 topic map。

## 10. Weekly Reflection

English:

This week's reading reshaped my PhD direction from burden-aware subgroup diagnosis into hierarchical, mechanism-matched reliability evaluation. My thesis now appears as the first layer of a broader problem: global MAE hid elderly degradation, but subgroup means may still hide severe elderly cases, and interventions may fail when the relevant archive or visual regime is unsupported. The strongest research contribution is therefore not another fairness correction or complex visual architecture. It is an evaluation framework that identifies the level and mechanism of hidden failure before choosing an intervention.

I am becoming a researcher who studies how reliability evidence breaks down across levels of aggregation and under changing support conditions. My work should connect retrospective residual analysis to prospective monitoring, while keeping simple models and assumption checks as first-class baselines. Historical facial age estimation remains a strong grounding case because it contains the exact tensions I want to study: aggregate masking, sparse vulnerable groups, unstable balancing, hard-routing fragility, uncertain labels, and multi-axis visual shift.

中文:

这周的阅读把我的 PhD 方向从 burden-aware subgroup diagnosis 推进到 hierarchical、mechanism-matched reliability evaluation。我的 thesis 现在更像这个问题的第一层：global MAE 掩盖 elderly degradation，但 subgroup mean 仍可能掩盖 severe elderly cases；当 archive source 或 visual regime 缺乏 support 时，subgroup-aware intervention 也会失败。因此我最强的贡献不应该是再提出一个 fairness correction 或复杂视觉架构，而是建立一个 evaluation framework，先识别 failure 隐藏在哪一层、由什么 mechanism 产生，再选择 intervention。

我正在成为一个研究“reliability evidence 如何在不同 aggregation level 和 changing support condition 下失效”的研究者。我的工作需要把 retrospective residual analysis 推进到 prospective monitoring，同时把 simple model 和 assumption check 作为第一层 baseline。Historical facial age estimation 仍然是很强的 grounding case，因为它同时包含 aggregate masking、sparse vulnerable group、balancing instability、hard-routing fragility、label uncertainty 和 multi-axis visual shift。

## 11. Proposal Seed

English:

My proposed research studies hierarchical subgroup reliability under distribution shift. Motivated by my thesis on historical facial age estimation, where aggregate MAE masked elderly-group degradation and balancing or conditional routing could worsen vulnerable cases, I will examine three levels of hidden failure: global-to-group masking, severe errors within named subgroups, and failure caused by missing source-target support. Using historical portraits as a grounding case, I will combine residual and tail diagnostics, source-period evaluation windows, subgroup-valid uncertainty assessment, and deployment signals that can be tested before target labels arrive. Rather than assuming one universally robust method, the framework will characterize the shift mechanism and then evaluate whether data selection, calibration, reweighting, or soft routing matches that mechanism. The expected contribution is a decision-relevant protocol for detecting when model reliability evidence is misleading, identifying which subgroup or within-subgroup cases are at risk, and determining whether an intervention removes failure or merely relocates it.

中文理解:

我的 proposal 可以围绕 distribution shift 下的 hierarchical subgroup reliability。出发点是我的 thesis：aggregate MAE 掩盖 elderly-group degradation，而且 balancing 或 conditional routing 可能让 vulnerable cases 更差。我会研究三层 hidden failure：global-to-group masking、named subgroup 内部的 severe error，以及 source-target support 缺失导致的 failure。以 historical portraits 为 grounding case，我可以结合 residual/tail diagnostics、source-period evaluation windows、subgroup-valid uncertainty evaluation，以及 target label 到达前可测试的 deployment signals。核心不是假设一个 universally robust method，而是先识别 shift mechanism，再检验 data selection、calibration、reweighting 或 soft routing 是否真正匹配该机制。预期贡献是一个 decision-relevant protocol，用于识别 reliability evidence 何时具有误导性、哪些 subgroup 或 within-subgroup cases 面临风险，以及 intervention 是真正减少 failure 还是只移动 failure。

## 12. Deep Reading Queue

Create at most two deep paper cards this week.

- Priority 1: DuetFair: Coupling Inter- and Intra-Subgroup Robustness for Fair Medical Image Segmentation
- Priority 2: Missingness-Aware Conformal Prediction Under Cross-Hospital Distribution Shift
- Deferred: A multimodal slice discovery framework for systematic failure detection and explanation in medical image classification; Investigating Data Interventions for Subgroup Fairness: An ICU Case Study; ShapShift; Entropic Projection Alignment; The Impact of Coreset Selection on Spurious Correlations and Group Robustness

## 13. Next Week Plan

- [ ] Deep-read DuetFair and verify whether the within-subgroup gains survive simple baselines, repeated external-domain splits, and routing-error analysis.
- [ ] Deep-read Missingness-Aware Conformal Prediction and verify subgroup construction, finite-sample coverage, interval-size burden, and current OpenReview revision.
- [ ] Draft a compact historical portrait evaluation matrix with global, elderly, worst-cell, and elderly-tail metrics across archive-source or period windows.
- [ ] Select no more than three monitoring baselines: residual-history statistics, subgroup conformal coverage, and one uncertainty or moment-matching signal.
- [ ] Update topic maps only if a deep paper card verifies within-subgroup hidden failure or mechanism-matched early warning as a stable concept.
