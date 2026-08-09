# Weekly Research Summary - Week 11

Week: 11
Date range: 2026-08-03 to 2026-08-09
Daily notes reviewed: 2026-08-04, 2026-08-09
Missing daily notes in window: 2026-08-03, 2026-08-05, 2026-08-06, 2026-08-07, 2026-08-08
New paper cards reviewed: none
Topic maps updated: none. The week produced a strong candidate concept, but no deep paper card confirmed it as stable enough for topic-map promotion.
Main research identity: failure-unit-first subgroup reliability under historical distribution shift

Main purpose: synthesize this week's reading into a proposal direction where I diagnose the reliability unit before choosing balancing, calibration, residual adaptation, synthetic stress testing, or monitoring interventions.

## 1. What Became Clearer This Week?

English:

This week clarified that my thesis problem is not only about a vulnerable elderly subgroup. The stronger framing is that model reliability under shift depends on whether I have identified the correct failure unit. Across the two daily notes, the most relevant papers repeatedly questioned fixed demographic or class labels: FAREG learns representation-based low-coverage groups, Fine-Grained Class-Conditional Distribution Balancing decomposes coarse classes into latent subsets, StreamFair monitors worst intersectional drift, Face-Fairness uses frozen embeddings for subgroup correction, synthetic medical image work builds targeted audit cohorts, and EXHEART treats time and instrument as deployment-specific reliability axes.

The result is a sharper proposal logic. My thesis findings can be reinterpreted as evidence that global MAE, age/gender balancing, and gender-conditional cascades all assumed the wrong reliability surface. Elderly degradation may still be the most visible symptom, but the true failure unit may be an age-source-quality slice, a representation cluster, a low-coverage conformal group, a temporal archive window, or a cross-instrument analogue such as scanning or restoration pipeline.

中文:

这周最清楚的变化是: 我的 thesis 问题不只是 "elderly subgroup 表现差", 而是我是否选对了 failure unit。两篇 daily notes 里的论文都在反复挑战固定 demographic 或 class label: FAREG 学习 representation-based low-coverage groups, fine-grained balancing 把粗 class 拆成更细的 latent subsets, StreamFair 监控 worst intersectional drift, Face-Fairness 用 frozen embeddings 做 subgroup correction, synthetic medical image work 构造 targeted audit cohorts, EXHEART 把时间和仪器当作 deployment reliability axes。

这让我可以把 thesis findings 重新组织成一个更强的 proposal 逻辑: global MAE、age/gender balancing 和 gender-conditional cascade 都可能假设了错误的 reliability surface。Elderly degradation 仍然重要，但它可能只是可见症状；真正的 failure unit 可能是 age-source-quality slice、representation cluster、low-coverage conformal group、archive temporal window，或者类似 scanning/restoration pipeline 的 cross-instrument shift。

## 2. Technical Patterns

### Pattern 1: Distribution shift is becoming multi-axis and unit-dependent

English:

The week moved distribution shift away from a single source-target comparison. The papers covered temporal intersectional drift, representation-space coverage failure, cross-dataset face authenticity gaps, class-conditional spurious variation, synthetic demographic cohort support, and cross-instrument clinical monitoring. For my historical portrait setting, this means archive source, period, scan quality, image degradation, gender route, and elderly status should be treated as interacting axes, not separate checklist columns.

中文判断:

Historical domain shift 不是一个单一变量。我的实验应比较 source-held-out、period-held-out、quality-stratified 和 learned-slice validation，而不是只报告 random split MAE 或 age/gender table。

### Pattern 2: Subgroup robustness increasingly depends on learned or fine-grained reliability units

English:

FAREG and the ICLR fine-grained balancing paper are the strongest pair this week. Both argue that predefined groups can miss where reliability actually fails. One expresses this through conditional coverage and learned representation groups; the other through fine-grained class-conditional subsets without explicit bias annotations. This gives a direct technical path for testing whether elderly MAE degradation is better explained by fixed age/gender cells or by residual-aware embedding slices.

中文判断:

Subgroup robustness 的关键不只是 "报告更多 demographic groups", 而是把 reliability unit 当作实验对象。对我的 thesis 来说，这正好解释为什么 elderly group 被看见了，但真正机制可能在 elderly-source-quality 或 embedding region 里。

### Pattern 3: Reliability monitoring is becoming trigger-based and subgroup-local

English:

StreamFair, EXHEART, and the synthetic stress-cohort paper all make monitoring more operational. Useful signals include worst-intersection EO gaps, EWMA/CUSUM drift statistics, conditional coverage gaps, subgroup calibration drift, threshold instability, cross-instrument validation gaps, and agreement between synthetic and real subgroup error rankings. The shared pattern is that monitoring should localize degradation and decide when an intervention is justified.

中文判断:

我的 monitoring 方向可以从 "看 residual plot" 变成更具体的 audit loop: 先监控 source/period/embedding drift 和 elderly residual skew，再用 support threshold、bootstrap uncertainty 或 calibration gap 决定是否触发 recalibration 或 residual correction。

### Pattern 4: Interventions are safer when layered on a stable base model

English:

Several papers favor lightweight reliability layers over full model replacement: StreamFair updates a residual module only after drift alarms, Face-Fairness remaps logits using frozen embeddings, and FAREG adjusts prediction sets around discovered low-coverage groups. This aligns with my thesis finding that simpler regression generalized better than complex cascaded routing. The new direction is not to keep the model simple and stop there, but to pair a stable model with targeted reliability diagnosis and correction.

中文判断:

这周进一步支持 "stable base model + reliability layer"。我的 simple regression finding 可以发展成 frozen age model + subgroup calibration/residual layer，而不是继续追更复杂 cascade 或 architecture novelty。

### Pattern 5: Balancing remains useful only if the balancing unit is correct

English:

The strongest reinterpretation of my balancing instability comes from fine-grained class-conditional balancing. Balancing visible age or gender counts may fail if the true spurious mechanism is tied to archive source, image quality, era, pose, or embedding geometry. Synthetic subgroup data may help audit sparse groups, but it can also create false confidence if the generated cohort does not reproduce the real historical artifact structure.

中文判断:

Balancing 不是被否定，而是需要前置诊断。我的 thesis 里 balancing backfire 可以被写成 "intervention targeted the wrong reliability unit"。

## 3. Conceptual Shifts

### Shift 1

From: recalibration-first reliability audit
To: failure-unit-first intervention design

English:

Week 10 emphasized target-domain validation and recalibration before complex adaptation. Week 11 adds an earlier question: what exactly is the unit whose reliability should be validated or recalibrated? Recalibration is still important, but it should be applied after I know whether the failure unit is visible age, age-gender-source, image quality, learned embedding slice, or temporal archive window.

中文:

Week 10 的重点是先做 target-domain validation 和 recalibration。Week 11 把问题再前移一步: 我到底要验证或校准哪个 reliability unit？Recalibration 仍然重要，但应建立在 failure unit diagnosis 之后。

### Shift 2

From: elderly degradation as a subgroup result
To: elderly degradation as a visible symptom of a hidden reliability surface

English:

The elderly label remains central because it is where my thesis observed severe degradation. But this week makes the mechanism less obvious. Elderly failure may be caused by source support, historical image degradation, latent facial representation geometry, route uncertainty, or low conditional coverage.

中文:

Elderly group 仍然是核心，但它不一定是完整机制。它可能只是 source support、historical image degradation、latent representation geometry、route uncertainty 或 low conditional coverage 的表现位置。

### Shift 3

From: fixed subgroup monitoring
To: learned, intersectional, and stress-tested monitoring

English:

Monitoring should not only track age and gender groups selected in advance. It should also test learned low-reliability groups, worst intersections, synthetic or augmented stress cohorts, and time/source deployment axes. The challenge is keeping these units interpretable and stable enough for proposal-level evidence.

中文:

Monitoring 不能只看预设 age/gender groups，还要看 learned low-reliability groups、worst intersections、synthetic stress cohorts 和 time/source axes。但这些 units 必须有稳定性和可解释性，否则 proposal 证据会不够扎实。

## 4. Conceptual Chain Coverage

- Diagnosis: strengthened by representation-based group discovery, fine-grained class-conditional slice discovery, synthetic underrepresented cohort audits, temporal drift checks, and cross-instrument or source validation.
- Explanation: strengthened by the idea that aggregate masking and balancing backfire may come from choosing the wrong reliability unit rather than from subgroup labels alone.
- Intervention: strengthened by residual adapters, embedding-conditioned logit or residual correction, fine-grained balancing, synthetic stress testing, source-aware recalibration, and threshold control.
- Monitoring: strengthened by worst-intersection drift detectors, conditional coverage diagnostics, subgroup calibration drift, residual skew, threshold instability, and multi-axis pseudo-deployment evaluation.
- Evaluation: strengthened by worst-slice MAE, elderly underestimation rate, conditional coverage, group calibration, worst-intersection gaps, synthetic-real agreement, and harm rate for non-target groups after intervention.

Gap this week:

The main gap is verification depth. The week has two strong daily notes and six relevant papers, but no new deep paper card. The candidate concept of `failure-unit selection before subgroup intervention` should be kept in the weekly report and deep-reading queue rather than promoted to topic maps yet.

中文判断:

这周概念方向很强，但还缺 deep paper verification。`failure-unit selection before subgroup intervention` 值得保留，但应先 deep-read FAREG 或 fine-grained balancing paper，再决定是否进入 topic map。

## 5. Strongest Papers This Week

### Paper 1

Title: Fine-Grained Class-Conditional Distribution Balancing for Debiased Learning
Link: https://openreview.net/forum?id=pxh7lfn0HT
Research function: Diagnosis / Intervention / Evaluation
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It directly addresses the core tension in my thesis balancing result: robust balancing requires the right failure-relevant unit, not just visible class or demographic counts.
Connection to my thesis: It helps reinterpret elderly balancing backfire as possible age/gender balancing against the wrong source-quality or embedding-level failure slice.
Limitation: The paper is classification-centered, so my age-estimation extension would need age-bin prediction, residual-slice discovery, or regression-compatible grouping.
中文判断: 这是本周最强 deep-card candidate，因为它能把 balancing instability 变成 proposal-level mechanism。

### Paper 2

Title: Fair Conformal Classification via Learning Representation-Based Groups
Link: https://arxiv.org/abs/2605.12195
Research function: Diagnosis / Monitoring / Evaluation
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It turns aggregate masking into a conditional coverage problem and gives a method for learning hidden reliability groups when protected attributes or visible subgroup labels are insufficient.
Connection to my thesis: It suggests testing whether elderly underestimation corresponds to low-coverage embedding regions rather than fixed age-gender groups alone.
Limitation: It is conformal classification, so direct use in my thesis setting requires conformal regression intervals or an age-bin classification variant.
中文判断: 这是 uncertainty-aware reliability 的最强 candidate，适合支持 learned reliability units 和 conditional coverage。

### Paper 3

Title: StreamFair: Online Fair Adaptation Under Temporal Intersectional Drift
Link: https://openreview.net/forum?id=uOFS6DS8YK
Research function: Monitoring / Intervention / Evaluation
Usefulness: method reference with strong proposal value after full-manuscript verification
Why it matters: It shows a concrete trigger-based reliability workflow: monitor worst-intersection drift and update only a lightweight residual module when subgroup harm appears.
Connection to my thesis: It supports a historical-portrait pseudo-deployment experiment where elderly-source residual drift triggers calibration or residual correction instead of full retraining.
Limitation: The available record is a conference-talk page, and the domain is tabular socioeconomic data rather than visual age regression.
中文判断: 它适合提供 monitoring 和 intervention trigger vocabulary，但要先验证 full paper。

### Paper 4

Title: Toward Calibrated, Fair, and accurate Deepfake Detection
Link: https://arxiv.org/abs/2606.09881
Research function: Intervention / Monitoring / Evaluation
Usefulness: method reference with secondary-focus value
Why it matters: It uses frozen face embeddings for demographic-label-light reliability correction, which is technically close to my facial representation background.
Connection to my thesis: It suggests using frozen portrait embeddings to condition a residual or calibration layer for elderly-source failure without hard gender routing.
Limitation: Deepfake detection is a secondary domain for my radar, so it should not replace the historical facial age proposal center.
中文判断: 它适合作为 face-representation correction reference，也能连接 multimodal authenticity，但不是主线 anchor。

### Paper 5

Title: Demographically-Conditioned Synthetic Medical Images for Bias Mitigation and Bias Detection in Disease Classifiers
Link: https://arxiv.org/abs/2607.14984
Research function: Diagnosis / Intervention / Evaluation
Usefulness: method reference with high strategic value
Why it matters: It treats synthetic subgroup data as a tool for bias detection and sparse subgroup support, not just generic augmentation.
Connection to my thesis: It suggests creating or augmenting elderly-source stress cohorts to test whether residual skew and interval undercoverage appear before aggregate MAE changes.
Limitation: Synthetic data can create false confidence if it fails to reproduce historical portrait artifacts, age cues, or source-specific degradation.
中文判断: 这篇适合支持 stress-test audit，但必须把 synthetic cohorts 当作 sensitivity analysis，而不是 ground truth。

## 6. Strongest Connections to My Thesis

### Aggregate masking

English:

Aggregate masking now becomes unit-dependent masking. Global MAE, average accuracy, marginal conformal coverage, and overall detector accuracy can all look acceptable while a learned slice, worst intersection, elderly-source cell, or low-coverage representation region fails. This strengthens my thesis finding because it shows that the masking problem is not limited to point-estimate MAE.

中文:

Aggregate masking 现在变成 unit-dependent masking。Global MAE、average accuracy、marginal coverage 或 overall detector accuracy 都可能掩盖 learned slice、worst intersection、elderly-source cell 或 low-coverage representation region 的失败。

### Balancing instability

English:

Balancing instability is the week's strongest thesis connection. My earlier age/gender balancing result may have backfired because the intervention changed visible counts without changing the true failure mechanism. If elderly error is concentrated in archive-source-quality slices or embedding regions, then visible-group balancing can move samples around while preserving or amplifying the harmful structure.

中文:

Balancing instability 可以重新解释为 "平衡错了单位"。如果 elderly error 真正集中在 archive-source-quality slice 或 embedding region，那么 age/gender count balancing 可能没有处理机制，甚至放大了 harmful structure。

### Subgroup degradation

English:

Subgroup degradation is still centered on elderly reliability, but the elderly label should be treated as a diagnostic entry point. The evaluation should ask whether degradation remains after conditioning on source, period, gender route, quality, representation cluster, and calibration cell.

中文:

Subgroup degradation 仍然以 elderly reliability 为中心，但 elderly label 应作为 diagnosis entry point，而不是完整解释。需要继续检查 source、period、gender route、quality、representation cluster 和 calibration cell。

### Cascade fragility

English:

Cascade fragility becomes easier to explain as a routing-unit mismatch. The gender-conditional cascade assumed that gender was the right branch variable. This week suggests the actual failure boundary may be a softer representation or source-quality boundary, making frozen-model correction or residual calibration safer than hard routing.

中文:

Cascade fragility 可以写成 routing-unit mismatch。Gender route 可能不是正确 failure boundary；更合理的 boundary 可能在 representation 或 source-quality space 里。

## 7. Tensions and Open Problems

### Tension 1: Learned groups can improve diagnosis but weaken interpretability

Representation-based groups and fine-grained slices may reveal hidden failure, but the proposal needs stability checks, overlap analysis with age/gender/source/quality, and example inspection to keep the result interpretable.

### Tension 2: Synthetic cohorts can expose sparse failure but may invent the wrong evidence

Synthetic elderly-source cohorts can help stress-test sparse groups, but they are only useful if generated images preserve real age cues, source artifacts, and historical degradation patterns.

### Tension 3: Triggered adaptation needs enough subgroup support

Worst-intersection drift alarms and residual correction layers can overreact when elderly-source cells are small. Minimum support thresholds, bootstrap intervals, and persistence rules are needed before triggering intervention.

### Tension 4: Balancing, calibration, and residual adaptation may optimize different reliability targets

Fine-grained balancing may reduce worst-slice MAE, conformal recalibration may improve coverage, and residual adaptation may reduce underestimation. The proposal should evaluate these as different interventions rather than forcing a single metric to decide everything.

## 8. Top 3 Research Directions

### Rank 1

Working title: Failure-unit-first reliability audit for historical facial age estimation

Research question: In historical facial age estimation, do learned fine-grained reliability units explain elderly-group MAE degradation better than fixed age-gender or age-gender-source groups?

Why it ranks first: It has the best strategic fit, feasibility, and proposal potential. It directly explains aggregate masking, balancing backfire, and cascade fragility without abandoning the empirical center of my thesis.

Possible data: Thesis portrait images, age labels, gender labels, archive/source metadata, period labels, image-quality proxies, model embeddings, predictions, residuals, and calibration or interval estimates.

Possible method: Train a stable age-regression baseline; extract embeddings; construct fixed age/gender/source groups; discover residual-aware or coverage-aware fine-grained slices; test slice stability with bootstrap resampling; inspect overlap with age, gender, source, quality, and period; then compare which unit best predicts elderly residual skew and worst-slice MAE.

Evaluation metric: Global MAE, elderly MAE, worst-slice MAE, elderly underestimation rate, residual variance, subgroup calibration error, conditional coverage, slice stability, interpretability overlap, and non-elderly harm rate after intervention.

Thesis connection: This directly tests aggregate masking, elderly degradation, balancing instability, cascade fragility, and historical domain shift.

Risk or limitation: Learned units may be unstable or hard to explain. The project needs a clear reliability-unit validation protocol before using them to justify interventions.

中文判断: 这是本周最适合作为主线的方向，因为它把我的 thesis findings 统一到 "先诊断 failure unit" 这个 proposal claim。

### Rank 2

Working title: Evidence-triggered reliability layers under historical portrait shift

Research question: Can a frozen age-estimation model plus a lightweight residual or calibration layer reduce elderly-source degradation when updates are triggered only by subgroup drift or low-coverage signals?

Why it ranks second: It builds on the Week 10 recalibration-first frame and this week's stable-base-model pattern. It is technically feasible and can be tested without training many new architectures.

Possible data: Thesis portraits, source or period ordered validation windows, age/gender/source labels, embeddings, model predictions, residuals, prediction intervals, and image-quality proxies.

Possible method: Freeze a stable regression model; monitor elderly-source residual skew, score drift, embedding drift, calibration error, and conditional coverage; trigger isotonic, conformal, or small residual correction only after pre-specified alarms; compare against always-update, never-update, balancing, and cascade baselines.

Evaluation metric: Elderly MAE, worst age-source MAE, residual skew, underestimation rate, subgroup calibration error, interval coverage, alarm frequency, detection delay, false alarm rate, and harm rate for non-elderly groups.

Thesis connection: This tests whether my simple regression finding can become a stable base for subgroup reliability correction, while avoiding the fragility of hard cascades.

Risk or limitation: Alarm rules may be noisy in sparse elderly-source cells. Minimum support and persistence thresholds are required.

中文判断: 这是很自然的第二方向，适合把 simple regression、calibration 和 monitoring 连接起来。

### Rank 3

Working title: Synthetic and source-conditioned stress tests for hidden elderly degradation

Research question: Can synthetic or augmented elderly-source stress cohorts reveal historical-domain subgroup degradation before aggregate validation MAE changes?

Why it ranks third: It has strong monitoring and audit value, but it carries higher validity risk because synthetic historical portraits may not preserve real age, source, and image-degradation mechanisms.

Possible data: Real thesis portraits, elderly/non-elderly labels, source and period metadata, image-quality proxies, model predictions, residuals, and carefully validated synthetic or augmented elderly-source images.

Possible method: Generate or augment controlled elderly-source cohorts; compare their embedding distributions and nearest real examples against real portraits; evaluate whether residual skew, interval undercoverage, and threshold errors on stress cohorts predict real subgroup degradation; use synthetic data first for audit sensitivity rather than training.

Evaluation metric: Synthetic-real embedding distance, source/quality overlap, elderly MAE, residual skew, underestimation rate, interval coverage, source-specific calibration error, stress-test sensitivity, and agreement between synthetic and real subgroup error rankings.

Thesis connection: This extends aggregate masking and elderly degradation into an early-warning audit design for sparse subgroup support.

Risk or limitation: Synthetic cohorts may produce misleading evidence if generator artifacts differ from historical portrait artifacts.

中文判断: 这是长期有价值的 monitoring/stress-test 方向，但应作为第三方向，因为 validity 风险比前两个方向高。

## 9. Topic Map Decision

Topic maps reviewed as candidates from the project rules: `topic_maps/distribution_shift.md`, `topic_maps/fairness_subgroup_error.md`, `topic_maps/trustworthy_ai.md`, `topic_maps/ai_governance.md`, and `topic_maps/multimodal_authenticity.md`.

No topic map was edited this week.

Reason:

- The project rule says topic maps should be updated only when a deep paper card produces a stable concept.
- This week had no new deep paper cards.
- Both daily notes recommended topic-map updates only after deep paper confirmation.
- The candidate concept is strong but still needs verification from a deep reading of FAREG or the fine-grained balancing paper.

Candidate concepts to promote after deep reading:

- Failure-unit selection before subgroup intervention
- Learned reliability units under distribution shift
- Stable base model plus subgroup reliability layer
- Fine-grained balancing under historical source shift
- Synthetic subgroup stress cohorts as audit sensitivity tools

中文判断:

这周不更新 topic maps 是正确的。`failure-unit selection before subgroup intervention` 很有潜力，但需要 deep paper card 先确认方法细节、适用条件和实验可行性。

## 10. Proposal Seed

English, reusable paragraph:

My proposed PhD direction studies failure-unit-first subgroup reliability under distribution shift. Building on my thesis on historical facial age estimation, I will investigate why aggregate performance can hide elderly-group degradation and why interventions such as visible-group balancing or gender-conditional routing can become fragile when the true failure unit is hidden. The core idea is to diagnose the reliability unit before choosing the intervention. I will compare fixed demographic groups, source and period intersections, image-quality strata, learned embedding slices, and conditional coverage groups under historical portrait shift. Then I will test whether targeted interventions, including source-aware recalibration, residual correction layers, fine-grained balancing, and synthetic stress cohorts, improve elderly residual stability, worst-slice reliability, and subgroup calibration without harming other groups.

中文理解:

我的 PhD proposal 可以围绕 failure-unit-first subgroup reliability under distribution shift 展开。我的 thesis 已经显示 global MAE 会掩盖 elderly degradation，visible-group balancing 有时会伤害 elderly performance，gender-conditional cascade 也比较脆弱。下一步我可以把这些结果组织成一个更具体的框架: 先诊断真正的 reliability unit，再选择 intervention。具体来说，我会比较固定 age/gender groups、source/period intersections、image-quality strata、learned embedding slices 和 conditional coverage groups，然后测试 source-aware recalibration、residual correction、fine-grained balancing 和 synthetic stress cohorts 是否能改善 elderly residual stability、worst-slice reliability 和 subgroup calibration，同时不伤害其他 groups。

## 11. Weekly Reflection

English:

This week's reading reshaped my direction by making my thesis findings feel less like separate observations and more like one mechanism. Aggregate masking, balancing backfire, elderly degradation, and cascade fragility all point to a failure-unit problem. I should not only ask whether a model is fairer or more robust on visible groups. I should ask whether the evaluation unit matches where the model actually fails under historical source and period shift.

I am becoming a researcher who studies subgroup reliability as a diagnostic sequence. The sequence starts with visible failure, tests whether that failure is explained by source, period, quality, representation, or coverage structure, and only then chooses calibration, balancing, residual adaptation, stress testing, or monitoring. This keeps my work close to my historical facial age-estimation thesis while making the contribution broader: a method for deciding what should be monitored and corrected when aggregate metrics hide subgroup failure.

中文:

这周的阅读让我感觉 thesis findings 不再是几个分散现象，而是指向同一个机制: aggregate masking、balancing backfire、elderly degradation 和 cascade fragility 都可能来自 failure-unit selection 问题。我不应该只问一个模型在 visible groups 上是否更 fair 或更 robust，而要先问 evaluation unit 是否对应模型在 historical source 和 period shift 下真实失败的位置。

我正在成为一种把 subgroup reliability 看成 diagnostic sequence 的研究者。这个 sequence 从 visible failure 开始，继续检查这个 failure 是否由 source、period、quality、representation 或 coverage structure 解释，然后再决定 calibration、balancing、residual adaptation、stress testing 或 monitoring。这样既保留我的 historical facial age-estimation thesis grounding，又能把贡献扩展成一个更一般的问题: 当 aggregate metrics 掩盖 subgroup failure 时，如何决定应该监控和修正的对象。

## 12. Deep Reading Queue

Create at most two deep paper cards this week.

- Priority 1: `Fine-Grained Class-Conditional Distribution Balancing for Debiased Learning`
- Priority 2: `Fair Conformal Classification via Learning Representation-Based Groups`
- Deferred: `StreamFair: Online Fair Adaptation Under Temporal Intersectional Drift`; `Demographically-Conditioned Synthetic Medical Images for Bias Mitigation and Bias Detection in Disease Classifiers`; `Toward Calibrated, Fair, and accurate Deepfake Detection`; `EXHEART`

## 13. Next Week Plan

- [ ] Deep-read the fine-grained class-conditional balancing paper and decide whether `failure-unit selection before subgroup intervention` is stable enough for topic-map promotion.
- [ ] Deep-read FAREG if time allows and extract a regression-compatible version of learned low-coverage reliability units.
- [ ] Draft a thesis-extension experiment comparing fixed age/gender cells, age-source-quality cells, and learned residual slices.
- [ ] Keep topic maps unchanged until at least one deep paper card verifies the candidate concept.
- [ ] Check source details for StreamFair before treating it as a proposal citation.
