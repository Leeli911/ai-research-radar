# Weekly Research Summary - Week 06

Week: 06
Date range: 2026-06-22 to 2026-06-28
Daily notes reviewed: 2026-06-23, 2026-06-24, 2026-06-25, 2026-06-26, 2026-06-28
Missing daily notes in window: 2026-06-22, 2026-06-27
New paper cards reviewed: none
Main research identity: reliability-unit design for subgroup reliability under distribution shift

Main purpose: synthesize this week's papers into a proposal direction that moves from visible subgroup reporting toward choosing, discovering, and validating the reliability units that should guide monitoring and intervention.

## 1. What Became Clearer This Week?

English:

This week made the subgroup question sharper. The central issue is no longer only whether elderly, age, sex, race, or gender groups show worse performance. The stronger question is whether the group used for evaluation, mitigation, monitoring, or adaptation is the right reliability unit for the failure mechanism. Visible demographic groups can expose failure, but the causal or operational unit may instead be a hidden appearance cohort, an archive-age cell, a worst operating-point group, a route-specific branch, or a context-conditioned subgroup.

This reframes my thesis. Elderly-group degradation remains the key empirical starting point, but I should not assume that age alone is the mechanism. The failure may be concentrated in elderly portraits with particular archive sources, historical image styles, image-quality regimes, annotation patterns, or representation clusters. Balancing instability and cascade fragility may both come from using a visible subgroup as the intervention unit when the true failure unit lies elsewhere.

中文:

这周最清楚的推进是: subgroup reliability 的核心不只是报告哪个 demographic group 更差，而是判断我使用的 evaluation unit、mitigation unit、monitoring unit 和 adaptation unit 是否真的对应 failure mechanism。

这重新解释了我的 thesis。Elderly-group degradation 仍然是最重要的经验出发点，但 age group 不一定就是完整机制。真正的 failure 可能集中在 elderly portraits 中的 archive source、historical style、image quality、annotation pattern 或 representation cluster。Balancing 反效果和 cascaded model 脆弱性可能都来自同一个问题: 我用 visible subgroup 做干预，但真实 reliability unit 可能更细、更隐蔽、或更接近 decision operating point。

## 2. Technical Patterns

### Pattern 1: Distribution shift is becoming subgroup-mechanism diagnosis

English:

SHIFT, hidden-cohort fairness, medical shortcut analysis, and subgroup monitoring papers all move beyond average source-to-target degradation. They ask which subgroup decays, which variables explain the decay, and whether the apparent subgroup is only a surface marker for a deeper visual or contextual shift.

中文判断:

Historical portrait shift should be modeled as age x archive source x era x image quality x representation cluster, not as one generic historical-vs-modern gap. My thesis can become a diagnostic problem: which reliability unit actually explains elderly residual drift?

### Pattern 2: Subgroup robustness depends on subgroup definition

English:

Subgroups Matter for Robust Bias Mitigation, hidden-cohort fairness, pseudo-balancing, and worst-group equalized-odds regularization all show that the subgroup used for intervention can determine whether mitigation helps, fails, or harms. The evaluation subgroup and mitigation subgroup may be different.

中文判断:

Elderly group is a necessary evaluation axis, but it may not be the best mitigation axis. I should compare age-only balancing with era, image-quality, gender-age intersection, hidden-cohort, and archive-age cell interventions before claiming that balancing itself is good or bad.

### Pattern 3: Monitoring is shifting from global drift alerts to local reliability control

English:

CUSUM subgroup monitoring, SHIFT's where/how testing, representation-geometry markers, conformal interval burden, and decision-threshold fairness all treat monitoring as local and mechanism-specific. A useful alert should identify the vulnerable unit, the likely mechanism, and the action-relevant consequence.

中文判断:

For historical age estimation, the useful monitoring signal is not just representation distance or global MAE drift. It is whether elderly underestimation, worst hidden-cohort MAE, interval width, or operating-point misclassification changes before the aggregate score reveals the problem.

### Pattern 4: Interventions can relocate failure rather than remove it

English:

Disentanglement, synthetic pretraining, pseudo-balancing, dataset distillation, conformal prediction, and context-conditioned offsets all point to the same caution. An intervention can improve average performance while moving burden into uncertainty width, hidden cohorts, operating-point false negatives, small calibration cells, or route-specific fragility.

中文判断:

My thesis balancing result should be evaluated as burden transfer. Did balancing reduce global MAE while increasing elderly residual skew, interval width, worst-cell error, or hidden-cohort failure? This is more informative than asking whether balancing worked in a binary way.

### Pattern 5: Soft context use is different from hard routing

English:

Patient-conditioned offsets and synthetic pretraining suggest that age, sex, archive source, and context variables can be useful if used as soft modulation, representation shaping, or evaluation structure. This differs from hard conditional routing, which can amplify upstream errors.

中文判断:

The lesson from my cascaded model is not to avoid context variables. It is to avoid brittle context use. A shared regressor with lightweight context-conditioned residual adapters may be a better comparison than a hard gender-conditional cascade.

## 3. Conceptual Shifts

### Shift 1

From: hierarchical subgroup reliability
To: reliability-unit design

English:

Week 05 established that failure can hide below global metrics, inside named subgroups, or outside source support. Week 06 adds that the reliability unit itself must be chosen or discovered. Named groups, hidden cohorts, operating-point groups, calibration cells, and adaptation units can point to different failure mechanisms.

中文:

Week 05 的重点是 hidden failure 的层级。Week 06 的推进是 reliability unit 本身需要被设计和验证。Age group、hidden cohort、operating-point group、calibration cell 和 adaptation unit 可能对应不同机制。

### Shift 2

From: subgroup-aware mitigation
To: mechanism-aligned intervention unit

English:

The current question is not whether balancing, reweighting, disentanglement, synthetic data, or conditional adaptation is best. It is whether the intervention acts on the same unit and mechanism that produced the subgroup degradation.

中文:

我不应先比较哪种 mitigation 平均最好，而应先判断 intervention unit 是否对准 failure mechanism。如果 elderly degradation 实际来自 image-quality cohort，age balancing 就可能错位。

### Shift 3

From: calibration as statistical validity
To: calibration as decision burden

English:

Conformal and operating-point fairness papers show that valid coverage or strong AUC can still impose unequal burden through wider intervals, false-negative margins, or less actionable predictions. Reliability must include what the uncertainty or error does to the downstream decision.

中文:

Coverage 或 AUC 合法不代表 decision burden 公平。Elderly portraits 可能得到更宽 interval、更高 underestimation cost，或在特定 threshold 附近产生更高风险。

## 4. Conceptual Chain Coverage

- Diagnosis: strengthened by hidden-cohort discovery, SHIFT-style subgroup decay tests, sensitive-attribute probing, shortcut detection, and subgroup-estimate stability analysis.
- Explanation: strengthened by subgroup-definition mismatch, representation separation, age or archive-source leakage, feature-specific shift risk, and hidden visual cohorts.
- Intervention: strengthened by pseudo-balancing, barycentric coreset selection, synthetic pretraining, worst-group operating-point regularization, and soft context-conditioned residual adaptation.
- Monitoring: strengthened by CUSUM subgroup alerts, representation-geometry markers, where/how drift decomposition, conformal interval burden, and operating-point error tracking.
- Evaluation: strengthened by worst hidden-cohort error, worst archive-age cell MAE, subgroup coverage plus width, decision-threshold underestimation, and model-rank stability under source-target splits.

Gap this week:

The literature offers many candidate reliability units, but there is not yet one compact historical-age protocol for validating whether a discovered unit is stable, interpretable, and actionable. The immediate gap is to design minimum-support, stability, and intervention-response checks for candidate reliability units.

中文判断:

这周概念变强了，但也带来一个风险: hidden cohort、operating point、context adapter、pseudo-balancing 都可能让 proposal 变散。下一步应压缩成一个实验核心: 先比较 candidate reliability units，再看这些 units 是否解释 elderly residual drift，并只测试与该 unit 匹配的少数 intervention。

## 5. Strongest Papers This Week

### Paper 1

Title: Fairness Beyond Demographics: Optimizing Performance Across Appearance-Based Hidden Cohorts in Medical Imaging
Link: https://arxiv.org/abs/2605.29827
Research function: Diagnosis / Intervention / Evaluation
Usefulness: proposal anchor
Why it matters: It directly reframes subgroup reliability from visible demographic categories to appearance-based hidden cohorts.
Connection to my thesis: Elderly-group degradation may be a surface label for hidden historical cohorts combining age, archive source, image quality, pose, and representation instability.
Limitation: The clustering representation may create opaque or unstable cohorts, so hidden cohorts need interpretability and repeated-run stability checks.
中文判断: 这是本周最强 proposal anchor，因为它把"elderly group failed"推进到"哪个 hidden cohort 解释 elderly failure"。

### Paper 2

Title: "Who experiences large model decay and why?" A Hierarchical Framework for Diagnosing Heterogeneous Performance Drift
Link: https://arxiv.org/abs/2506.00756
Research function: Diagnosis / Explanation
Usefulness: proposal anchor
Why it matters: SHIFT gives a concrete where/how structure for detecting subgroup-specific decay and explaining whether covariate or outcome shift drives it.
Connection to my thesis: It can turn elderly underestimation under historical shift into a formal performance-decay diagnosis rather than a descriptive subgroup table.
Limitation: The explanatory layer requires interpretable variables or concept summaries; raw historical portraits need image-quality, era, archive, or embedding-cluster proxies.
中文判断: 这篇最适合支撑 thesis-to-proposal 的诊断框架，但需要改写成 continuous age regression 和 visual shift setting。

### Paper 3

Title: Subgroups Matter for Robust Bias Mitigation
Link: https://arxiv.org/abs/2505.21363
Research function: Explanation / Intervention
Usefulness: method reference with high strategic value
Why it matters: It shows that mitigation can succeed or fail depending on subgroup definition, and the mitigation subgroup may differ from the evaluation subgroup.
Connection to my thesis: It gives the clearest mechanism for why age balancing or gender-conditional routing may worsen elderly reliability when the chosen subgroup does not match the true failure source.
Limitation: Controlled spurious-correlation settings are cleaner than historical portrait shift, where the relevant subgroup may be latent or noisy.
中文判断: 这篇把 balancing instability 从"方法失败"变成"subgroup definition 失败"。

### Paper 4

Title: Fairness and Robustness of CLIP-Based Models for Chest X-rays
Link: https://arxiv.org/abs/2507.21291
Research function: Evaluation / Explanation
Usefulness: proposal anchor and evaluation reference
Why it matters: It combines age-specific gaps, shortcut reliance, sensitive-attribute probing, and calibration failure in one audit structure.
Connection to my thesis: Its three-part audit maps well to historical portraits: subgroup error, representation leakage, and shortcut or artefact dependence.
Limitation: It is classification-oriented and medical-domain specific; representation encoding does not by itself prove causal shortcut use.
中文判断: 这篇提供了一个可迁移的 audit template，可直接改写为 portrait age-estimation evaluation panel。

### Paper 5

Title: Beyond Procedure: Substantive Fairness in Conformal Prediction
Link: https://arxiv.org/abs/2602.16794
Research function: Evaluation / Decision
Usefulness: decision-relevant uncertainty reference
Why it matters: It shows that equal coverage can still create unequal decision burden through prediction-set size disparity.
Connection to my thesis: Elderly reliability should include interval width, undercoverage, and decision-weighted underestimation cost, not only elderly MAE.
Limitation: The paper does not solve distribution-shift validity and partly depends on an LLM-in-the-loop fairness evaluator.
中文判断: 这篇帮助我把 hidden failure 从 point error 扩展到 uncertainty burden。

## 6. Strongest Connections to My Thesis

### Aggregate masking

English:

Aggregate masking now includes at least four layers: global score masks visible subgroup failure; visible subgroup score masks hidden cohort failure; subgroup AUC or MAE masks operating-point harm; and marginal uncertainty coverage masks interval-width or decision-burden disparity.

中文:

Aggregate masking 现在不只是 global MAE 掩盖 elderly MAE，而是 global -> visible subgroup -> hidden cohort -> operating point / uncertainty burden 的多层结构。

### Balancing instability

English:

Balancing instability is best reinterpreted as intervention-unit mismatch. Age balancing may fail if the real mechanism is archive-source support, image-quality strata, representation separation, biased pseudo-labels, or decision-threshold error. Balancing should be evaluated against alternative units rather than accepted or rejected wholesale.

中文:

Balancing 反效果可能不是说明 balancing 永远无效，而是说明 intervention unit 没有对准 mechanism。Age-only balancing 需要和 archive-aware、quality-aware、hidden-cohort-aware、intersectional balancing 做同预算比较。

### Subgroup degradation

English:

Elderly degradation should be treated as a reliable symptom, not a complete explanation. The weekly papers repeatedly suggest that visible age gaps may be produced by hidden visual cohorts, shortcut artefacts, source support, outcome shift, or threshold-specific error patterns.

中文:

Elderly group 是可靠性诊断入口，不是最后答案。真正要解释的是 elderly failure 集中在哪些 archive-age cell、hidden cohort、quality regime 或 operating point。

### Cascade fragility

English:

The cascade result now has a stronger interpretation: hard routing can lock the model into the wrong reliability unit. If gender is not the mechanism of age-estimation degradation, route-specific heads may amplify noise, leakage, and support mismatch. Soft context-conditioned adapters are a better comparator than another hard branch.

中文:

Cascaded model 脆弱性不只是结构复杂，而是 hard routing 可能把错误 subgroup unit 固化进模型。Context 可以使用，但应先测试 soft modulation、route uncertainty 和 route-specific calibration。

## 7. Tensions and Open Problems

### Tension 1: Hidden cohorts improve diagnosis but weaken interpretability

Appearance-based cohorts can reveal failures missed by age/gender tables, but opaque clusters are weak proposal evidence unless they are stable, semantically coherent, and predictive of intervention response.

### Tension 2: Using sensitive context can help or harm

Disentanglement papers warn that removing age or sex can damage useful signal, while patient-conditioned offsets suggest that context can improve reliability. The unresolved question is how to use context softly without creating cascade-style fragility.

### Tension 3: Synthetic data can support training or evaluation, but can also reassure falsely

Synthetic pretraining and synthetic subgroup expansion can reduce sparsity, but generator artefacts may hide the same rare historical patterns that cause elderly failure.

### Tension 4: Monitoring needs labels, proxies, and action rules

CUSUM and SHIFT-style monitoring are appealing, but historical portrait settings may not have streaming labels. Proxy signals must be validated against later revealed residuals and linked to an action such as recalibration, data review, or manual inspection.

## 8. Top 3 Research Directions

### Rank 1

Working title: Reliability-unit discovery for historical facial age estimation

Research question: In historical facial age estimation, do hidden appearance cohorts, archive-age cells, or visible age/gender groups best explain elderly-group MAE degradation under archive-source and historical-period shift?

Why it ranks first: It is the cleanest extension of this week's conceptual shift and directly builds on my thesis. It turns elderly degradation into a testable mechanism-diagnosis problem without requiring a new model architecture.

Possible method: Extract embeddings from existing thesis models; define candidate units using visible groups, archive-age cells, image-quality strata, and clustering; compare their ability to explain residual bias, residual variance, elderly underestimation, and source-target degradation.

Possible data: My historical portrait dataset with age, gender, archive source, period, image-quality proxies, model predictions, residuals, and backbone embeddings.

Evaluation plan: Global MAE, elderly MAE, worst-unit MAE, elderly-cohort overlap, residual skew, residual variance, calibration error, hidden-unit stability, and model-ranking reversal under source-period splits.

Fit with my background: Very high. It uses my thesis data, subgroup evaluation, representation analysis, and residual diagnostics.

Risk level: Medium. Hidden cohorts may be unstable or hard to interpret, so minimum-support rules, repeated clustering, and semantic validation are required.

Strategic fit: Very high
Feasibility: High
Proposal potential: Very high

中文判断: 这是第一方向，因为它把我的 thesis 核心发现推进为"如何选择可靠性单位"。它技术上可执行，也能形成清晰 proposal identity。

### Rank 2

Working title: Mechanism-aligned balancing and adaptation under historical shift

Research question: When does age-only balancing worsen elderly reliability because the intervention unit is wrong, and can archive-aware, quality-aware, hidden-cohort-aware, or soft context-conditioned adaptation reduce elderly tail error more reliably?

Why it ranks second: It directly explains the most distinctive thesis puzzle: balancing and hard conditional routing sometimes harmed the vulnerable group. It should follow Rank 1 because intervention should be matched to the diagnosed reliability unit.

Possible method: Compare no balancing, age balancing, archive-age balancing, hidden-cohort-aware sample selection, hard gender routing, and lightweight context-conditioned residual adapters under matched training budgets.

Possible data: Historical portrait training and evaluation splits organized by age, gender, archive source, era, image quality, and stable hidden cohorts from Rank 1.

Evaluation plan: Global and elderly MAE, elderly 90th-percentile error, worst-unit MAE, underestimation rate, route-specific error, calibration error, interval width, and burden transfer to non-elderly groups.

Fit with my background: Very high. It directly revisits balancing experiments and cascade fragility from my thesis.

Risk level: Medium-high. The intervention grid can expand too quickly; the first study should use only two or three diagnosed units and one soft-adaptation baseline.

Strategic fit: Very high
Feasibility: Medium-high
Proposal potential: High

中文判断: 这是第二方向，因为它解释 thesis 中最有辨识度的反常结果，但必须以 diagnosis 为前提，避免变成 method zoo。

### Rank 3

Working title: Decision-relevant subgroup monitoring for historical age reliability

Research question: Can local monitoring signals detect elderly or hidden-cohort degradation before global MAE changes, while avoiding unequal interval-width, false-alarm, or deferral burden?

Why it ranks third: It gives the proposal stronger trustworthy-ML scope by moving from retrospective audit to prospective monitoring. Its feasibility is lower because online labels and true subgroup membership may be delayed or uncertain.

Possible method: Use rolling source-period windows; compare residual-history baselines, representation-geometry markers, subgroup or hidden-cohort conformal intervals, CUSUM-style residual alerts, and simple target-moment risk estimates.

Possible data: Time-ordered or archive-ordered historical portrait splits, existing predictions and residuals, source-period calibration data, and later-period labels for retrospective validation.

Evaluation plan: Detection lead time, subgroup failure AUROC, false-alarm rate, detection delay, elderly coverage gap, interval-width disparity, underestimation cost, effective sample size, and actionability of the alert.

Fit with my background: High. It connects my calibration/residual diagnostics with professional monitoring-dashboard experience.

Risk level: Medium-high. Label-free monitoring and probabilistic subgroup membership can recreate routing fragility.

Strategic fit: High
Feasibility: Medium
Proposal potential: Very high

中文判断: 这是第三方向，因为它有更强 PhD novelty，但需要先完成 reliability-unit diagnosis，才能避免 monitoring signal 没有明确对象。

## 9. Topic Map Updates

English:

I did not update any topic map this week. A genuinely new conceptual structure emerged - reliability-unit design - but no new deep paper card was reviewed during the weekly window. Under the repository rule, topic maps should be updated only when a deep paper card produces a stable concept, not whenever daily notes identify a promising direction.

Candidate additions after deep reading:

- `topic_maps/distribution_shift.md`: reliability-unit design under source-target shift, including visible groups, hidden cohorts, operating-point groups, and source-support cells.
- `topic_maps/fairness_subgroup_error.md`: subgroup definition as an experimental variable for both evaluation and mitigation.
- `topic_maps/trustworthy_ai.md`: local monitoring of hidden-cohort and operating-point reliability, with interval burden and false-alarm cost.

I did not identify a stable new structure for `topic_maps/ai_governance.md` or `topic_maps/multimodal_authenticity.md`.

中文:

本周不更新 topic maps。`reliability-unit design` 已经是强候选概念，但还没有本周新 deep paper card 验证。等 hidden-cohort fairness 或 SHIFT 完成 deep read 后，再决定是否把它写入长期 topic map。

## 10. Weekly Reflection

English:

This week's reading reshaped my evolving PhD direction from hierarchical subgroup reliability into reliability-unit design under distribution shift. My thesis already showed that global MAE can hide elderly degradation, balancing can worsen a vulnerable group, and hard conditional routing can be fragile. I now interpret these findings as evidence that the visible subgroup may not be the right unit for every reliability task. Age is essential for evaluation, but the mechanism may live in hidden appearance cohorts, archive-age cells, operating-point errors, or context-specific representation instability.

I am becoming a researcher who studies how to identify the unit at which reliability should be measured, monitored, and improved. This keeps my work grounded in historical facial age estimation while making the contribution broader than one dataset or one fairness metric. The strongest proposal shape is: diagnose which reliability unit explains hidden elderly degradation, test whether interventions aligned to that unit reduce failure without moving burden elsewhere, and design monitoring signals that warn about local degradation before aggregate metrics change.

中文:

这周的阅读把我的 PhD 方向从 hierarchical subgroup reliability 推进到 distribution shift 下的 reliability-unit design。我的 thesis 已经说明 global MAE 会掩盖 elderly degradation，balancing 可能伤害 vulnerable group，hard conditional routing 可能脆弱。现在我更倾向于把这些结果解释为: visible subgroup 不一定是所有 reliability task 的正确单位。Age 对 evaluation 很重要，但真正机制可能存在于 hidden appearance cohort、archive-age cell、operating-point error 或 context-specific representation instability 中。

我正在成为一种研究者: 关注如何识别应该在哪个单位上测量、监控和改善 reliability。这个方向仍然以 historical facial age estimation 为 grounding case，但贡献不局限于一个数据集或一个 fairness metric。最强的 proposal 形状是: 先诊断哪个 reliability unit 解释 hidden elderly degradation，再检验与该 unit 对齐的 intervention 是否减少 failure 而不是转移 burden，最后设计能在 aggregate metric 变化前发现 local degradation 的 monitoring signal。

## 11. Proposal Seed

English:

My proposed research studies reliability-unit design for machine learning systems under distribution shift. Motivated by my thesis on historical facial age estimation, where aggregate MAE hid elderly-group degradation and balancing or hard conditional routing sometimes worsened vulnerable cases, I will examine whether visible demographic groups are sufficient reliability units or whether failure is better explained by archive-age cells, hidden appearance cohorts, operating-point groups, or context-conditioned representation shifts. Using historical portraits as a grounding case, I will compare candidate reliability units by their ability to explain residual drift, underestimation, calibration failure, and model-ranking reversals across historical source-target splits. I will then test whether interventions aligned to the diagnosed unit, such as archive-aware selection, hidden-cohort-aware balancing, subgroup-valid calibration, or soft context-conditioned adaptation, reduce failure without transferring burden into uncertainty width, tail error, or other groups. The contribution is a decision-relevant protocol for discovering where reliability actually breaks and how that unit should guide evaluation, monitoring, and intervention.

中文理解:

我的 proposal 可以围绕 distribution shift 下的 reliability-unit design。出发点是我的 thesis: aggregate MAE 掩盖 elderly-group degradation，而 balancing 或 hard conditional routing 有时会让 vulnerable cases 更差。我会研究 visible demographic group 是否足够作为 reliability unit，还是 archive-age cell、hidden appearance cohort、operating-point group 或 context-conditioned representation shift 更能解释 failure。以 historical portraits 为 grounding case，我可以比较不同 candidate reliability unit 对 residual drift、underestimation、calibration failure 和 model-ranking reversal 的解释能力。然后检验与诊断结果对齐的 intervention - 例如 archive-aware selection、hidden-cohort-aware balancing、subgroup-valid calibration 或 soft context-conditioned adaptation - 是否真正减少 failure，而不是把 burden 转移到 uncertainty width、tail error 或其他 groups。预期贡献是一个 decision-relevant protocol，用于发现 reliability 在哪个单位上失效，并用该单位指导 evaluation、monitoring 和 intervention。

## 12. Deep Reading Queue

Create at most two deep paper cards this week.

- Priority 1: Fairness Beyond Demographics: Optimizing Performance Across Appearance-Based Hidden Cohorts in Medical Imaging
- Priority 2: "Who experiences large model decay and why?" A Hierarchical Framework for Diagnosing Heterogeneous Performance Drift
- Deferred: Subgroups Matter for Robust Bias Mitigation; Fairness and Robustness of CLIP-Based Models for Chest X-rays; Beyond Procedure: Substantive Fairness in Conformal Prediction; Fairness Without Labels: Pseudo-Balancing for Bias Mitigation in Face Gender Classification; Diagnosing Generalization Failures from Representational Geometry Markers

## 13. Next Week Plan

- [ ] Deep-read the hidden-cohort fairness paper and verify how cohorts are constructed, stabilized, interpreted, and evaluated across demographic attributes.
- [ ] Deep-read SHIFT and translate its where/how decomposition into continuous age-regression residual diagnostics.
- [ ] Draft a compact reliability-unit comparison matrix: visible age/gender groups, archive-age cells, quality strata, embedding clusters, and operating-point groups.
- [ ] Test one low-cost pilot on existing thesis outputs: which candidate unit best explains elderly underestimation and worst-cell MAE?
- [ ] Update topic maps only if a deep paper card verifies reliability-unit design as a stable concept.
