# Weekly Research Summary - Week 13

Week: 13
Date range: 2026-09-07 to 2026-09-13
Daily notes reviewed: 2026-09-07, 2026-09-08, 2026-09-09, 2026-09-10, 2026-09-11, 2026-09-12, 2026-09-13
Missing daily notes in window: none
New paper cards reviewed: none
Topic maps updated: none. The week produced a strong repeated candidate frame, but no new deep paper card confirmed it as stable enough for topic-map promotion.
Main research identity: evidence-validity-first subgroup reliability under historical distribution shift

Main purpose: synthesize this week's reading into a proposal direction where I validate the data source, label source, metric meaning, subgroup support, and decision threshold before trusting balancing, routing, calibration, or model adaptation.

## 1. What Became Clearer This Week?

English:

This week clarified that my thesis findings should not be interpreted too quickly as a simple model-choice or fairness-intervention problem. The stronger frame is evidence validity before intervention. Across seven daily notes, the selected papers repeatedly asked whether the evidence used to diagnose subgroup reliability is itself trustworthy: whether source aggregation hides shortcuts, whether automated or archival labels distort subgroup conclusions, whether marginal coverage hides local under-coverage, whether metrics are collapsible or decision-relevant, whether threshold meaning changes across contexts, and whether subgroup discovery has enough statistical support.

This makes my thesis story sharper. Aggregate MAE masked elderly failure, but the masking may have several layers: pooled error can hide source-specific residuals; pooled conformal coverage can hide elderly under-coverage; pooled calibration can hide group-specific score meaning; pooled datasets can hide shortcut directions; and pooled subgroup labels can hide label-process differences. Age/gender balancing may have backfired not only because balancing was weak, but because the intervention may have targeted the wrong evidence surface: visible counts rather than source identity, label reliability, subgroup separability, calibration validity, or context-conditioned thresholds. The cascaded gender-conditional model may have been fragile because hard routing assumed a stable boundary, while the real reliability boundary may have been archive/source, period, image quality, label provenance, or representation shortcut structure.

The most useful conceptual shift is therefore from "which intervention improves elderly reliability?" to "what evidence must be valid before an intervention claim is credible?" This is a more disciplined and proposal-ready direction. Historical portrait age estimation can become a compact testbed for trustworthy ML evaluation under shift: source-aware representation diagnosis, label-provenance sensitivity, subgroup conditional coverage, context-aware threshold auditing, and calibration-aware monitoring.

中文:

这周最清楚的一点是: 我的 thesis findings 不应该太快被解释成简单的 model choice 或 fairness intervention 问题。更强的 framing 是 evidence validity before intervention。七篇 daily notes 反复追问同一件事: 用来诊断 subgroup reliability 的证据本身是否可信? Dataset aggregation 是否隐藏 source shortcut? automated 或 archival labels 是否改变 subgroup conclusion? marginal coverage 是否隐藏 local under-coverage? metric 是否可分解、是否 decision-relevant? threshold 在不同 context 中是否还有同样含义? subgroup discovery 是否有足够统计支持?

这让我的 thesis 叙事更锋利。Global MAE 掩盖 elderly failure, 但这种 masking 可能有多层: pooled error 掩盖 source-specific residuals; pooled conformal coverage 掩盖 elderly under-coverage; pooled calibration 掩盖 group-specific score meaning; pooled datasets 掩盖 shortcut directions; pooled subgroup labels 掩盖 label-process differences。Age/gender balancing 可能 backfire, 不只是因为 balancing 不够强, 而是因为 intervention 对准的是 visible counts, 不是 source identity、label reliability、subgroup separability、calibration validity 或 context-conditioned thresholds。

所以这周最重要的变化是: 从 "哪个 intervention 能改善 elderly reliability?" 转向 "在 intervention claim 成立前, 哪些 evidence 必须先有效?" 这个方向更有 PhD proposal 纪律性。Historical portrait age estimation 可以作为一个紧凑 testbed: source-aware representation diagnosis、label-provenance sensitivity、subgroup conditional coverage、context-aware threshold auditing 和 calibration-aware monitoring。

## 2. Technical Patterns

### Pattern 1: Distribution shift is increasingly source-aware, not only time-aware

English:

The strongest distribution-shift signal this week is that source identity can dominate the reliability surface. The cross-hospital debiasing paper, healthcare dataset-effects paper, and multi-institutional foundation-model shortcut paper all warn that models can encode source/domain structure in ways that survive or undermine fairness interventions. For my thesis, archive/source identity should be treated as a first-class diagnostic axis, not only background metadata.

中文判断:

Historical portrait shift 不能只写成 train-test style mismatch。更具体的问题是 archive/source identity 是否支配 embedding space、residual structure、calibration 和 cascade route behavior。

### Pattern 2: Subgroup robustness depends on evidence support, not only subgroup naming

English:

Several notes converged on a small-sample and local-evidence problem. A subgroup reliability claim needs enough calibration support, enough residual evidence, and stable subgroup partitions. Conformal subgroup under-coverage papers ask whether local coverage claims are supported; subgroup-tree work asks whether discovered splits overfit; latent-slice and perturbation papers ask whether hidden fragile samples are stable enough to justify intervention.

中文判断:

这直接约束我的 future subgroup analysis。我可以切 elderly-source-quality-route intersections, 但不能因为发现一个高 MAE cell 就立刻当作 stable subgroup。需要 minimum support、bootstrap stability、held-out source/period validation 和 uncertainty intervals。

### Pattern 3: Label provenance became a central reliability variable

English:

The false-confidence and label-bias papers make label source part of the reliability mechanism. Subgroup fairness conclusions can change when automated labels, biased labels, or noisy reference labels are used. For historical portraits, age labels may be estimated, archival, incomplete, or source-dependent. Elderly degradation may therefore mix visual difficulty with label-process instability.

中文判断:

我的 thesis 可以加入 label-reliability sensitivity: known age versus estimated age, high-confidence versus uncertain metadata, source-specific age recording practices, and simulated label perturbation. 这比只做 age/gender balancing 更接近 failure mechanism。

### Pattern 4: Uncertainty validity is now part of subgroup reliability

English:

Conformal and calibration papers repeatedly showed that marginal uncertainty validity can hide subgroup failure. Elderly portraits may have higher MAE, wider residual tails, lower interval coverage, or overconfident underestimation. A trustworthy evaluation should compare point error, coverage, interval width, calibration, false-safe rate, and route-specific uncertainty.

中文判断:

我的 residual diagnostics 可以升级成 monitoring protocol: global coverage、elderly coverage、source-period coverage、route-specific coverage、undercoverage lead time 和 interval burden 都应该和 MAE 一起看。

### Pattern 5: Decision thresholds and context variables should not be treated mechanically

English:

The cross-context threshold and hidden-confounding papers add a middle position between aggregate evaluation and blanket invariance. A threshold, metric, route, or context variable may change meaning across environments. Some source or period variables can be harmful shortcuts; others can be useful proxies for label reliability or image-formation context. The task is not automatic removal, but context-aware auditing.

中文判断:

在 historical portraits 中, source、period、quality、restoration metadata 不能被简单当成 nuisance。它们可能造成 shortcut, 也可能是唯一能解释 label reliability 和 visual formation shift 的线索。

## 3. Conceptual Shifts

### Shift 1

From: conditional-shift-aware intervention evidence
To: evidence-validity-first subgroup reliability

English:

Week 12 asked whether an intervention changes the failure mechanism or moves failure across axes. Week 13 adds a prior gate: before asking whether an intervention worked, I need to test whether the source data, labels, metric decomposition, subgroup partition, uncertainty guarantee, and threshold are valid enough to support that claim.

中文:

Week 12 关注 intervention 是否真的改变 failure mechanism。Week 13 加了一道更前置的 gate: 在判断 intervention 有没有用之前, 要先检验证据本身是否可靠。

### Shift 2

From: subgroup degradation as model error
To: subgroup degradation as data-context and audit-target instability

English:

Elderly degradation is still the visible symptom, but the mechanism may come from archive/source structure, source shortcuts, label provenance, subgroup separability, calibration drift, or temporal split design. This keeps the elderly group central while avoiding the mistake of treating the group label as the full explanation.

中文:

Elderly degradation 仍然是核心现象, 但它可能来自 source shortcut、label process、calibration drift 或 temporal split design。Elderly group 是入口, 不是完整机制。

### Shift 3

From: monitoring as drift detection
To: monitoring as audit-validity checking

English:

The monitoring layer should not only ask whether the distribution changed. It should ask whether the diagnostic still means what it claims to mean: whether local explanations miss global drift, whether route utilization shifts, whether subgroup residual trees are stable, whether coverage holds locally, and whether threshold claims remain decision-relevant.

中文:

Monitoring 不只是 drift detector。更重要的是 audit validity: local explanation 是否给 false reassurance? route utilization 是否变化? subgroup tree 是否稳定? local coverage 是否失效? threshold 是否还对应同一个 decision risk?

### Shift 4

From: simple versus complex model comparison
To: evidence-gated model selection

English:

The week strengthened my earlier thesis finding that simpler regression sometimes generalized better than more complex conditional routing. The new interpretation is not "simple is always better." It is that complex local treatment needs evidence: enough local support, route-specific calibration, source-held-out validation, and target-probe local-gain evidence.

中文:

这不是说 simple model 永远更好, 而是 complex intervention 必须过 evidence gate: local support、route calibration、source-held-out validation 和 target-probe gain。

## 4. Conceptual Chain Coverage

- Diagnosis: strengthened by source-identity probing, metric collapsibility checks, subgroup conditional coverage diagnostics, label-provenance sensitivity, dataset-effect decomposition, and statistically disciplined subgroup trees.
- Explanation: strengthened by source shortcuts, hidden confounding, subgroup separability, label bias, calibration drift, context-dependent thresholds, and dataset-algorithm interaction.
- Intervention: strengthened by evidence gates for hidden-slice augmentation, leakage-aware intervention selection, conditional coverage repair, clean-label validation, subgroup/source-aware recalibration, and shortcut-direction sensitivity analysis.
- Monitoring: strengthened by coverage deficits, threshold instability, route-utilization drift, local explanation/global drift mismatch, subgroup residual trees, source recoverability, and elderly false-safe rate.
- Evaluation: strengthened by separating global MAE, elderly MAE, worst-source elderly MAE, coverage gaps, interval width, calibration error, label-source sensitivity, source-held-out generalization, and decision-threshold validity.

Gap this week:

The evidence is broad and internally consistent, but still mostly daily-note level. No new deep paper card verified the exact formulas, datasets, ablations, or limitations for the strongest candidate concepts. Therefore, topic maps should stay unchanged until at least one of the source-shortcut, label-provenance, dataset-effects, or subgroup-conformal papers receives a deep paper card.

中文判断:

这周概念非常强, 但还没有 deep paper card 支撑。最稳妥的做法是把 `evidence validity before intervention` 放进 weekly report 和 deep-reading queue, 暂时不提升到 topic map。

## 5. Strongest Papers This Week

### Paper 1

Title: When multi-institutional dataset aggregation masks shortcut-like behavior in Foundation Models for medical imaging
Link: https://www.sciencedirect.com/science/article/pii/S1361841526003270
Research function: Diagnosis / Explanation / Monitoring / Evaluation / Intervention
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It is the closest bridge from my computer-vision thesis to trustworthy medical-imaging reliability. It gives a concrete vocabulary for source-identity probing, shortcut-like representation directions, aggregate masking, subgroup disparity, and performance-fairness trade-offs.
Connection to my thesis: It supports testing whether archive/source identity directions in facial embeddings are stronger than age-relevant directions and whether they explain elderly MAE degradation.
Limitation: Source, period, image quality, and age composition may be confounded, so early use should be diagnostic and sensitivity-oriented rather than causal.
中文判断: 这是本周最强 anchor, 因为它把 source shortcut 和 aggregate masking 直接连接到 visual embeddings。

### Paper 2

Title: Dataset effects outweigh algorithmic effects in determining fairness of healthcare machine learning
Link: https://www.nature.com/articles/s41746-026-02723-1
Research function: Diagnosis / Explanation / Evaluation / Intervention
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It argues that dataset identity and dataset-algorithm interaction can dominate algorithm choice and that balancing alone may not remove subgroup gaps.
Connection to my thesis: It gives a data-centric explanation for balancing backfire: elderly degradation may reflect source-specific feature structure and label processes rather than architecture alone.
Limitation: It is healthcare ML rather than historical facial age regression, so the transferable part is the decomposition logic, not the exact task.
中文判断: 它能帮助我把 balancing instability 写成 dataset-context problem, 而不是 isolated anomaly。

### Paper 3

Title: False Confidence: Automated Labels Confound Fairness Audits in Cervical Spine Segmentation
Link: https://arxiv.org/abs/2607.07852
Research function: Diagnosis / Explanation / Monitoring / Evaluation
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It adds a missing audit layer: subgroup reliability conclusions depend on the validity of the reference labels.
Connection to my thesis: Historical age labels and archive metadata may be noisy or source-dependent, especially for elderly portraits. This paper supports label-provenance sensitivity before judging balancing or cascaded routing.
Limitation: The task is segmentation and automated labels, so the historical portrait adaptation requires age-label confidence proxies or perturbation-based sensitivity analysis.
中文判断: 这篇直接补上 thesis 里还没系统处理的 label-source validity 问题。

### Paper 4

Title: When Is a Conformal Guarantee Fair? Auditing Silent Subgroup Under-Coverage in Alzheimer's Disease Longitudinal Prediction
Link: https://arxiv.org/abs/2608.04254
Research function: Diagnosis / Monitoring / Evaluation / Intervention
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It turns aggregate masking into an uncertainty-validity problem by asking whether marginal coverage silently fails for subgroups.
Connection to my thesis: Elderly residual variance and underestimation can be reframed as subgroup under-coverage, residual-tail, and calibration-cell support problems under historical shift.
Limitation: Small elderly-source-period cells may make fine-grained conformal claims unstable, so the first experiment should use prespecified coarse strata and report coverage-width trade-offs.
中文判断: 这是 uncertainty-aware monitoring 的最强候选之一。

### Paper 5

Title: The Cross-Context Threshold Test: Detecting Discrimination Under Environmental Shifts
Link: https://proceedings.mlr.press/v300/yuan26b.html
Research function: Diagnosis / Explanation / Evaluation / Intervention
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It provides a decision-threshold vocabulary for asking whether the same metric or cutoff means the same thing across contexts.
Connection to my thesis: It supports translating elderly degradation from "higher MAE" into "high-error threshold, age-bin threshold, or cascade confidence threshold changes meaning across archive/source contexts."
Limitation: The threshold framing may require converting continuous age regression into decision-relevant bins or high-error events, which must be justified by the downstream historical-demography use case.
中文判断: 它能把 subgroup reliability 从 static score 推向 decision-relevant threshold validity。

## 6. Strongest Connections to My Thesis

### Aggregate masking

English:

Aggregate masking now has at least five forms: pooled MAE masking elderly residuals, pooled coverage masking elderly under-coverage, pooled calibration masking subgroup score semantics, pooled dataset aggregation masking source shortcuts, and pooled labels masking subgroup-specific label-process error. This broadens my thesis finding without losing its concrete empirical center.

中文:

Aggregate masking 不再只是 global MAE 掩盖 elderly MAE。它还包括 pooled coverage、pooled calibration、pooled dataset source 和 pooled label process 的 masking。

### Balancing instability

English:

Balancing instability is now best interpreted as intervention before evidence validation. Age/gender balancing can fail if the true reliability mechanism is source identity, label provenance, subgroup separability, image quality, calibration drift, or hidden contextual confounding. The next experiment should compare visible balancing with source-aware, label-aware, and calibration-aware diagnostics before claiming mitigation.

中文:

Balancing backfire 可以写成 intervention before evidence validation。Visible count 平衡不一定处理 source shortcut、label process、calibration drift 或 hidden confounding。

### Subgroup degradation

English:

Elderly degradation remains central, but I should treat it as a diagnostic entry point. The reportable claim should not stop at "elderly MAE is higher." It should ask whether elderly degradation is stable across archive, period, label confidence, calibration cell, route, source shortcut strength, and decision threshold.

中文:

Elderly group 是 failure 出现的位置, 但 proposal 应该进一步问它是否在 source、period、label confidence、route、calibration 和 threshold 下稳定。

### Cascade fragility

English:

The cascade finding becomes an evidence-gated routing problem. A hard route is credible only if route confidence, route-specific calibration, source-held-out performance, local gain over a simple regression floor, and subgroup coverage support all hold. Otherwise, the cascade may amplify source or label artifacts.

中文:

Cascaded model 的脆弱性可以写成 routing evidence 不足。Route-specific calibration、source-held-out validation 和 local gain 都需要先验证。

## 7. Tensions and Open Problems

### Tension 1: Source variables can be shortcuts or useful context

Source, period, restoration, and image-quality variables can encode harmful shortcut behavior, but they may also carry useful information about label reliability or image formation. The first study should separate predictive utility, fairness risk, and causal interpretation instead of automatically removing context variables.

### Tension 2: Fine-grained subgroup discovery improves sensitivity but increases overfitting risk

Elderly-source-quality-route cells may reveal hidden degradation, but small cells can create unstable alarms. The solution is not to avoid subgroup discovery, but to require minimum support, regularized partitions, bootstrap stability, and held-out source/period validation.

### Tension 3: Uncertainty repair may move burden rather than reduce failure

Subgroup-aware conformal intervals may improve coverage while widening intervals or increasing deferral for elderly portraits. Evaluation should report both coverage and burden: interval width, abstention rate, false-safe rate, and worst-source coverage.

### Tension 4: Label filtering improves audit validity but may reduce subgroup support

High-confidence age labels may make validation cleaner, but elderly high-confidence labels may be scarce. The proposal should model sample-size uncertainty and avoid treating filtered validation as the only truth.

## 8. Top 3 Research Directions

### Rank 1

Working title: Source-aware evidence validity for elderly facial age reliability

Research question: Are archive/source identity directions in facial embeddings stronger than age-relevant directions, and do they explain elderly-group MAE degradation under historical portrait shift?

Why it ranks first: It has the strongest thesis fit, the clearest data path, and the best proposal potential. It connects aggregate masking, historical domain shift, source shortcuts, balancing instability, and representation diagnosis in one experiment.

Possible method: Train probes for archive/source and age group on embeddings; estimate task-to-source signal ratio; fit mixed-effects or variance-decomposition models for elderly MAE, residual skew, and calibration; test source-held-out and period-held-out splits; optionally suppress source directions as a sensitivity analysis.

Possible data: thesis embeddings, predicted ages, true or estimated ages, age groups, gender labels, archive/source labels, period metadata, image-quality proxies, model family, balancing condition, and cascade-route outputs.

Evaluation plan: source-probe accuracy, age-probe accuracy, task-to-source signal ratio, elderly MAE, worst-source elderly MAE, residual skew, calibration error, source-model interaction size, and aggregate-performance trade-off.

Fit with my background: very high. It extends my thesis directly and uses computer vision, representation learning, subgroup evaluation, and data-centric diagnosis.

Risk level: medium. Source labels may be confounded with period, quality, and age composition, so the first version should avoid causal language and report sensitivity analyses.

中文判断: 这是最适合 proposal 的主线, 因为它把 historical visual domain shift 具体化成 source-aware reliability diagnosis。

### Rank 2

Working title: Label-provenance and calibration audit for historical subgroup reliability

Research question: Does label-reliability filtering plus residual calibration detect elderly age-estimation failure better than naive age/gender balancing under historical domain shift?

Why it ranks second: It directly explains a weak point in my thesis: balancing may have failed because label source, label uncertainty, and residual calibration were not audited before intervention.

Possible method: Build validation subsets by label-confidence proxies; simulate age-label perturbations for elderly and non-elderly groups; compare residual calibration, prediction-interval coverage, and elderly underestimation under natural, balanced, and cascaded models.

Possible data: thesis labels and metadata, age-confidence proxies, predicted ages, residuals, age bins, gender labels, archive/source metadata, model outputs, confidence scores, and any manually verified high-confidence subset.

Evaluation plan: elderly MAE, residual calibration error, interval coverage gap, elderly underestimation rate, worst-source calibration error, balancing-induced vulnerable-group error change, and bootstrap uncertainty.

Fit with my background: high. It builds naturally on my calibration analysis, residual diagnostics, and historical metadata awareness.

Risk level: medium-high. Alternative labels may be unavailable, so the first version may need sensitivity analysis rather than definitive relabeling.

中文判断: 这个方向能让我的 thesis 更 data-centric, 但需要谨慎处理 label confidence 的可用性。

### Rank 3

Working title: Subgroup conditional coverage monitoring under historical shift

Research question: Can subgroup- and route-aware conformal residual diagnostics detect elderly under-coverage before global MAE or marginal coverage degrades?

Why it ranks third: It has strong monitoring and trustworthy-ML fit, but it depends more heavily on enough subgroup calibration support and careful interpretation of conformal assumptions under historical shift.

Possible method: Build split-conformal residual intervals for simple regression, balanced regression, multi-task, and cascaded models; compare marginal, elderly, source-period, and route-specific coverage; test whether local under-coverage appears before global metrics change.

Possible data: thesis predictions, residuals, calibration scores, age group, gender, route assignment, archive source, portrait period, model variant, confidence, and image-quality proxies.

Evaluation plan: marginal coverage, elderly coverage, worst-slice coverage deficit, interval width, underestimation rate, false-safe rate, detection lead time, calibration-cell size, and coverage-width trade-off.

Fit with my background: high. It extends my calibration and residual work into uncertainty-aware monitoring.

Risk level: medium. Historical shift may violate exchangeability, and elderly-source-period cells may be small. The first version should present conformal outputs as empirical diagnostics unless assumptions are defensible.

中文判断: 这是最适合 trustworthy monitoring 的方向, 但需要避免过度承诺 formal guarantee。

## 9. Proposal Seed

English, 153 words:

My proposed research studies how subgroup reliability evidence breaks down under historical distribution shift. In my master thesis on facial age estimation, global MAE hid elderly-group degradation, age/gender balancing sometimes worsened elderly performance, and a gender-conditional cascade was fragile. I now frame these findings as an evidence-validity problem rather than a simple model-improvement problem. Before trusting a balancing, routing, calibration, or adaptation intervention, I will test whether the source data, label provenance, subgroup partition, uncertainty estimate, and decision threshold are valid for the vulnerable subgroup. Historical portrait age estimation provides a concrete visual testbed: archive/source identity may dominate embeddings, age labels may vary in reliability, and pooled metrics may hide elderly-source failures. The project will develop source-aware representation diagnostics, label-provenance sensitivity analysis, and subgroup conditional-coverage monitoring to decide when a subgroup reliability claim is strong enough to support intervention.

中文理解:

我的 proposal 可以围绕 historical distribution shift 下 subgroup reliability evidence 如何失效来组织。硕士论文中的 global MAE masking、elderly degradation、balancing backfire 和 cascaded routing fragility 不再只是单个模型结果, 而是一个 evidence-validity problem: 在相信任何 balancing、routing、calibration 或 adaptation 之前, 需要先验证 source data、label provenance、subgroup partition、uncertainty estimate 和 decision threshold 是否对 vulnerable subgroup 有效。Historical portrait age estimation 是一个很好的 testbed, 因为 archive/source identity 可能支配 embedding, 年龄标签可能随 source 改变可靠性, pooled metrics 也可能掩盖 elderly-source failure。核心贡献可以是 source-aware representation diagnostics、label-provenance sensitivity analysis 和 subgroup conditional-coverage monitoring, 用来判断 subgroup reliability claim 什么时候足够可信, 什么时候还不能支持 intervention。

## 10. Deep Reading Queue

Create at most two deep paper cards next week.

- Priority 1: When multi-institutional dataset aggregation masks shortcut-like behavior in Foundation Models for medical imaging.
- Priority 2: False Confidence: Automated Labels Confound Fairness Audits in Cervical Spine Segmentation.
- Deferred: Dataset effects outweigh algorithmic effects in determining fairness of healthcare machine learning; When Is a Conformal Guarantee Fair?; The Cross-Context Threshold Test; AIA^2: Attribute-Agnostic Imbalance Augmentation for Subgroup Robustness.

Rationale:

Priority 1 is the strongest bridge to visual source shortcuts and aggregate masking. Priority 2 supplies the missing label-provenance layer. Together they can test whether `evidence validity before intervention` is stable enough to promote into topic maps after deep reading.

## 11. Topic Map Decision

No topic maps were updated this week.

Reason:

The week produced a coherent candidate structure: evidence-validity-first subgroup reliability. However, the repository rules say topic maps should be updated only when a stable concept emerges, especially from deep paper cards. Since no new deep paper card was created or reviewed this week, the concept should remain in this weekly report and deep-reading queue for now.

Candidate future topic-map additions after deep reading:

- `topic_maps/distribution_shift.md`: source-aware evidence validity under historical shift.
- `topic_maps/fairness_subgroup_error.md`: label-provenance and subgroup-support gates before fairness intervention.
- `topic_maps/trustworthy_ai.md`: audit-validity monitoring, including local coverage, threshold validity, and false-safe rate.

## 12. Weekly Reflection

English:

This week pushed my research identity toward a more skeptical, data-centric, and audit-oriented form of trustworthy ML. I am becoming less interested in proposing a single correction method and more interested in deciding when correction evidence is valid. My thesis already showed uneven failure: elderly portraits degraded, balancing was unstable, and cascaded routing was fragile. The new insight is that each of these findings depends on the trustworthiness of the evidence surface. If source identity dominates the representation, if labels are source-dependent, if coverage is only marginal, if thresholds change meaning across contexts, or if subgroup partitions are unstable, then an intervention result can look persuasive while solving the wrong problem. My next proposal step should therefore begin with evidence gates: source-aware diagnostics, label-provenance sensitivity, subgroup support checks, calibration and coverage panels, and decision-threshold validity.

中文:

这周让我更接近一种 skeptical、data-centric、audit-oriented 的 trustworthy ML 研究身份。我不再急着提出一个 correction method, 而是更关心 correction evidence 什么时候有效。我的 thesis 已经显示 uneven failure: elderly portraits 退化, balancing 不稳定, cascaded routing 脆弱。新的理解是: 这些发现都依赖 evidence surface 是否可信。如果 source identity 支配 representation, 如果 labels 随 source 改变可靠性, 如果 coverage 只是 marginal, 如果 threshold 在不同 context 中含义变化, 或者 subgroup partition 不稳定, 那么 intervention result 可能看起来很有说服力, 但其实解决了错误问题。下一步 proposal 应该从 evidence gates 开始: source-aware diagnostics、label-provenance sensitivity、subgroup support checks、calibration/coverage panels 和 decision-threshold validity。

## 13. Next Week Plan

- [ ] Deep-read the multi-institutional foundation-model shortcut paper.
- [ ] Create one deep paper card for source-aware representation shortcut diagnosis.
- [ ] Deep-read the false-confidence label-audit paper if time allows.
- [ ] Do not update topic maps until at least one deep paper card confirms `evidence validity before intervention`.
- [ ] Draft a compact experiment table for Rank 1: source probe, task-to-source signal ratio, elderly MAE gap, residual skew, calibration error, and source-held-out validation.
- [ ] Source or citation corrections: re-check full PDFs and final venue metadata before using the two priority papers in a proposal draft.
