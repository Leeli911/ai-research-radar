# Weekly Research Summary - Week 12

Week: 12
Date range: 2026-08-10 to 2026-08-16
Daily notes reviewed: 2026-08-10, 2026-08-11, 2026-08-12, 2026-08-13, 2026-08-15
Missing daily notes in window: 2026-08-14, 2026-08-16
New paper cards reviewed: none
Topic maps updated: none. The week produced repeated candidate concepts, but no new deep paper card confirmed one as stable enough for topic-map promotion.
Main research identity: conditional-shift-aware intervention evidence under historical distribution shift

Main purpose: synthesize this week's reading into a proposal direction where I test whether subgroup interventions actually change the failure mechanism, or only move failure across hidden axes while aggregate metrics remain acceptable.

## 1. What Became Clearer This Week?

English:

This week clarified that my thesis problem should not be framed as "balancing failed" in a simple sense. The stronger interpretation is that visible distribution matching can fail when the hidden conditional relationship, label process, uncertainty validity unit, or cross-axis subgroup structure remains unstable. Across the five daily notes, the strongest papers repeatedly made the same point from different domains: MAMA-MIA used external and subgroup-consistency evaluation; fixed-horizon clinical prediction exposed objective-metric mismatch; multi-distribution conformal prediction showed that marginal coverage can hide distribution-specific undercoverage; single-axis fairness intervention work showed that mitigation can move failure to another subgroup axis; TRUECAM combined OOD detection, abstention, conformal prediction, and subgroup-gap tracking; population-transfer and EHR-weighting papers showed that matching visible variables does not guarantee transferability.

This reshapes my thesis findings into a more disciplined mechanism. Aggregate MAE masked elderly failure because the evaluation unit was too coarse. Age or gender balancing could backfire because it changed marginal counts without necessarily fixing conditional shift, source-quality imbalance, or label uncertainty inside elderly portraits. The cascaded gender-conditional model was fragile because hard routing assumed that gender was the right reliability boundary, while the real failure boundary may involve source, period, image quality, label reliability, or embedding geometry.

中文:

这周更清楚的是: 我的 thesis 里 balancing 失败不能简单写成 "balancing 不好"。更强的解释是: visible distribution matching 只能调整表面的 subgroup 数量, 但如果 hidden conditional relationship、label process、uncertainty validity unit 或 cross-axis subgroup structure 不稳定, intervention 仍然可能失败。五篇 daily notes 反复出现同一个逻辑: MAMA-MIA 强调 external test 和 subgroup consistency; fixed-horizon clinical prediction 暴露 objective-metric mismatch; multi-distribution conformal prediction 说明 marginal coverage 会掩盖 subgroup undercoverage; single-axis fairness intervention 说明 mitigation 会把 failure 转移到另一条 subgroup axis; TRUECAM 把 OOD detection、abstention、conformal prediction 和 subgroup gap monitoring 放在同一个 reliability pipeline 里。

所以我的 thesis 可以重新组织成一个 intervention evidence 问题。Global MAE 掩盖 elderly failure, 是因为 evaluation unit 太粗。Age/gender balancing 可能 backfire, 是因为它只修正 visible marginal distribution, 没有修正 elderly portraits 内部的 conditional shift、source-quality imbalance 或 label uncertainty。Gender-conditional cascade 脆弱, 是因为它假设 gender 是正确的 reliability boundary, 但真实 failure boundary 可能在 source、period、image quality、label reliability 或 embedding geometry 上。

## 2. Technical Patterns

### Pattern 1: Distribution shift is moving from marginal shift to conditional reliability shift

English:

The week's strongest distribution-shift pattern is the separation between visible marginal mismatch and hidden conditional mismatch. Population-stratified ML and EHR-transfer papers show that weighting or sample matching can align observed demographics without fixing how features relate to labels in the target population. Structure-aware splitting work shows that random splits can hide deployment-like shift. FEATMAP frames source and acquisition artifacts as representation-space contamination rather than only input-level noise.

中文判断:

Historical portrait shift should not be treated as only "training and test images look different." I need to test whether elderly residuals persist after age balancing because `P(age | face evidence, source, quality, period)` changes across archives or historical periods.

### Pattern 2: Subgroup robustness is becoming a cross-axis intervention audit

English:

Single-axis fairness interventions and targeted face-augmentation papers show that improving one subgroup axis can create asymmetric effects elsewhere. A model may improve age fairness while worsening age-source, age-gender, or age-quality intersections. Synthetic augmentation can boost an underperforming group but create a whack-a-mole pattern if new disparities appear in another group.

中文判断:

This is the strongest direct connection to my balancing result. My future experiments should not evaluate age balancing only by overall MAE and elderly MAE. They should audit elderly women, elderly men, elderly-source cells, elderly low-quality portraits, and elderly embedding clusters before and after intervention.

### Pattern 3: Reliability monitoring is becoming validity-unit-aware

English:

Multi-distribution robust conformal prediction and TRUECAM make monitoring more precise. The unit of validity cannot be only the pooled calibration distribution. Useful monitoring signals now include subgroup coverage, worst-distribution coverage, interval width, abstention rate, OOD score, prediction-set size, false-confidence rate, and subgroup gap drift. Fixed-threshold AI-text detection adds the same lesson from a different domain: keeping the deployment rule fixed reveals failure that adaptive evaluation would hide.

中文判断:

My thesis residual and calibration plots can become a monitoring layer. The key experiment is whether source-conditioned or subgroup-conditioned intervals reveal elderly undercoverage before global MAE changes.

### Pattern 4: Evaluation objectives must match the downstream decision

English:

The fixed-horizon clinical prediction paper is useful because it separates a technically impressive metric from a decision-relevant metric. A model can rank cases well but fail for the fixed clinical horizon that matters. This maps directly to historical age estimation: a low global MAE is not necessarily enough if the downstream use depends on reliable elderly estimates, age-bin decisions, demographic reconstruction, or uncertainty-aware deferral.

中文判断:

My proposal should avoid treating MAE as the only objective. It should define the decision target first: point age estimate, age-bin assignment, elderly subgroup reconstruction, uncertainty interval, or abstention for ambiguous historical portraits.

### Pattern 5: Label and data quality are part of subgroup reliability

English:

The label-bias segmentation paper adds an important mechanism. Subgroup failure can come from biased or noisy supervision, not only from representation imbalance. For historical portraits, elderly labels may be noisier, more coarsely recorded, or more dependent on archival metadata quality. Balancing such samples can amplify noise if label-source reliability is ignored.

中文判断:

Elderly degradation may combine visual difficulty with label uncertainty. Future audits should track known-age, estimated-age, metadata-derived age, source quality, and image-quality proxies when possible.

## 3. Conceptual Shifts

### Shift 1

From: failure-unit-first subgroup reliability
To: conditional-mechanism-first intervention evidence

English:

Week 11 asked which unit fails. Week 12 adds a second question: what mechanism makes that unit fail? The candidate mechanisms are marginal sample scarcity, conditional feature-label shift, label-source noise, acquisition or archive contamination, uncertainty undercoverage, and cross-axis intervention side effects. This makes the proposal stronger because diagnosis does not stop at naming the subgroup; it asks why the subgroup is unreliable and which intervention is justified.

中文:

Week 11 关注 "failure unit 是什么"。Week 12 进一步问 "这个 unit 为什么失败"。候选机制包括 marginal sample scarcity、conditional feature-label shift、label-source noise、archive/acquisition contamination、uncertainty undercoverage 和 cross-axis intervention side effect。

### Shift 2

From: balancing as a fairness intervention
To: balancing as a hypothesis that needs external validation

English:

This week makes balancing less like a default fix and more like a testable claim. If age balancing improves visible age counts but worsens elderly-source reliability, then the intervention did not solve the failure mechanism. If weighting visible variables does not improve transferability, then unmeasured source or conditional shift remains. This directly reframes my thesis balancing result.

中文:

Balancing 现在更像一个需要验证的 hypothesis, 而不是默认修复工具。Age balancing 是否有用, 取决于它是否真的改变 elderly failure mechanism, 而不是只让 age counts 更平均。

### Shift 3

From: subgroup degradation as a static score
To: failure movement after intervention

English:

The key evaluation after an intervention is no longer only whether the target group improved. I need to ask where failure moved. Did elderly MAE improve while elderly low-quality portraits became worse? Did calibration improve while interval width burden moved to one source? Did source-aware weighting improve global transfer while worsening an elderly-gender intersection?

中文:

Intervention 后不能只问 target group 是否变好, 还要问 failure 移动到哪里。这个 framing 可以把 aggregate masking、balancing instability 和 subgroup degradation 放在同一个实验表格里。

### Shift 4

From: point-error diagnosis
To: uncertainty-aware reliability decisions

English:

This week strengthens a practical monitoring layer around conformal intervals, OOD scores, abstention, ambiguity filtering, and subgroup coverage. My thesis used residual and calibration diagnostics, but the proposal can now ask whether a model should return a wider age interval or defer the estimate for elderly historical portraits under archive shift.

中文:

我的 thesis 主要分析 point estimate residuals。现在可以进一步研究: 对于高风险 elderly historical portraits, 模型是否应该输出更宽的 age interval 或 abstain, 而不是强行给一个看似精确的年龄。

## 4. Conceptual Chain Coverage

- Diagnosis: strengthened by external validation, structure-aware splits, conditional shift analysis, label-bias auditing, acquisition-signature diagnosis, and subgroup/intersection panels.
- Explanation: strengthened by the distinction between marginal distribution matching and conditional reliability under source, quality, label, and representation shift.
- Intervention: strengthened by cross-axis auditing of balancing, reweighting, synthetic augmentation, representation harmonization, and uncertainty-aware abstention.
- Monitoring: strengthened by multi-distribution conformal coverage, OOD detection, fixed-threshold transfer, interval width, abstention, false-confidence rate, and subgroup gap drift.
- Evaluation: strengthened by decision-relevant objectives, subgroup-consistency scoring, worst-intersection metrics, coverage gaps, external source validation, and intervention side-effect panels.

Gap this week:

The week has broad and repeated evidence, but still lacks deep paper verification. The strongest candidate concepts should remain in the report and deep-reading queue until at least one paper card confirms method details and proposal feasibility.

中文判断:

这周的 conceptual structure 很强, 但还没有 deep paper card。Topic map 暂时不更新是合适的; 应先 deep-read cross-axis intervention、multi-distribution conformal prediction 或 TRUECAM。

## 5. Strongest Papers This Week

### Paper 1

Title: Single-Axis Fairness Interventions Produce Asymmetric Cross-Axis Effects in Clinical Prediction
Link: https://www.medrxiv.org/content/10.64898/2026.06.16.26355120v1
Research function: Evaluation and Intervention
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It gives the cleanest language for my thesis balancing backfire: an intervention can improve one axis while silently degrading another.
Connection to my thesis: Age balancing should be audited across gender, source, image quality, era, and label-source intersections, not only age groups.
Limitation: It is clinical and preprint-stage, so the method needs adaptation and source-status verification before formal proposal use.
中文判断: 这是本周最强 balancing instability anchor。

### Paper 2

Title: Multi-Distribution Robust Conformal Prediction
Link: https://arxiv.org/abs/2601.02998
Research function: Monitoring and Evaluation
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It turns aggregate masking into an uncertainty-validity problem. Marginal coverage can hide subgroup or source undercoverage.
Connection to my thesis: Elderly residual variance can be reframed as a coverage and interval-validity problem under historical source shift.
Limitation: Small age-source cells may require hierarchical grouping, shrinkage, or conservative reporting.
中文判断: 这是 uncertainty-aware monitoring 的最强 anchor。

### Paper 3

Title: Implementing trust in non-small cell lung cancer diagnosis with a conformalized uncertainty-aware AI framework
Link: https://www.nature.com/articles/s41551-026-01694-8
Research function: Monitoring and Intervention
Usefulness: proposal anchor and Recommended for paper card
Why it matters: It provides a deployable reliability pipeline with OOD detection, ambiguity filtering, conformal prediction, abstention, external validation, and subgroup gap evaluation.
Connection to my thesis: It suggests a concrete monitoring layer for historical age estimation: source/OOD score, interval width, abstention rate, elderly coverage, and false-confidence rate.
Limitation: The task is pathology classification, so age-regression adaptation is required.
中文判断: 这是把 thesis residual diagnostics 转成 monitoring workflow 的强方法参考。

### Paper 4

Title: Data Representation Bias and Conditional Distribution Shift Drive Predictive Performance Disparities in Multi-Population Machine Learning
Link: https://pubmed.ncbi.nlm.nih.gov/42244624/
Research function: Diagnosis and Explanation
Usefulness: proposal-supporting mechanism paper
Why it matters: It separates representation bias, marginal shift, and conditional shift, which is exactly the distinction needed to explain why balancing may fail.
Connection to my thesis: Elderly degradation may persist after balancing because the feature-label relationship changes across archive, source, quality, or age-label reliability.
Limitation: The empirical domain is genotype-phenotype prediction, not computer vision.
中文判断: 它适合支撑 "conditional shift versus marginal balancing" 的概念。

### Paper 5

Title: The MAMA-MIA Challenge: Advancing Generalizability and Fairness in Breast MRI Tumor Segmentation and Treatment Response Prediction
Link: https://arxiv.org/abs/2603.01250
Research function: Evaluation
Usefulness: proposal anchor and paper-card candidate
Why it matters: It makes subgroup consistency part of external evaluation rather than an afterthought.
Connection to my thesis: It gives a template for combining external source validation with age-related subgroup consistency.
Limitation: It is a challenge paper, so I need deep reading to extract the exact scoring design and failure patterns.
中文判断: 它适合支撑 subgroup-consistent external evaluation。

## 6. Strongest Connections to My Thesis

### Aggregate masking

English:

Aggregate masking now has four forms: pooled prediction error, pooled coverage, random-split performance, and objective-mismatched evaluation. Global MAE can hide elderly failure in the same way marginal conformal coverage can hide elderly undercoverage, random splits can hide archive shift, and ranking metrics can hide fixed-horizon decision failure.

中文:

Aggregate masking 不只是 global MAE 问题。它也可以表现为 marginal coverage、random split performance 和 objective mismatch。我的 thesis 可以作为这个更广泛问题的 historical face-age example。

### Balancing instability

English:

Balancing instability is the strongest weekly thesis connection. The papers suggest three mechanisms for backfire: balancing aligns visible marginal counts but not conditional feature-label relationships; single-axis balancing moves failure to other subgroup intersections; and balancing noisy or biased labels can amplify unreliable supervision.

中文:

Balancing backfire 可以被解释为三种机制: visible marginal counts 被对齐, 但 conditional relationship 没有被修正; single-axis intervention 把 failure 移到其他 subgroup intersection; label noise 或 label bias 被放大。

### Subgroup degradation

English:

Elderly degradation should remain central, but it is now best treated as a visible entry point into a hidden reliability mechanism. The next analysis should ask whether elderly failure is caused by age semantics, archive/source composition, image quality, label reliability, representation support, conditional shift, or uncertainty undercoverage.

中文:

Elderly degradation 仍然是中心, 但它更像 diagnosis entry point。真正机制可能是 age semantics、archive/source composition、image quality、label reliability、representation support、conditional shift 或 uncertainty undercoverage。

### Cascade fragility

English:

Cascade fragility can be reinterpreted as routing by the wrong reliability boundary. If gender is not the axis that stabilizes the feature-label relationship under historical shift, then a gender-conditional cascade can amplify error. A safer design may be a stable base regressor plus subgroup/source-aware monitoring and residual calibration.

中文:

Gender-conditional cascade 的问题可能是 route boundary 错了。如果 gender 不是稳定 feature-label relationship 的关键 axis, hard routing 会放大 shift 下的错误。

## 7. Tensions and Open Problems

### Tension 1: Conditional shift is powerful but hard to prove

Conditional shift can explain balancing backfire, but historical portrait metadata may be incomplete. I need proxy-based analysis with clear limits rather than overclaiming causal mechanisms.

### Tension 2: Intersectional auditing improves diagnosis but creates sparse cells

Age-source-quality-gender intersections are meaningful, but elderly cells may be small. Minimum support thresholds, bootstrap intervals, hierarchical grouping, and sensitivity checks are necessary.

### Tension 3: Uncertainty monitoring may reveal unreliability without solving it

Conformal intervals, OOD scores, and abstention can expose failure, but the proposal must specify what action follows: interval widening, manual review, source-aware recalibration, residual correction, or rejection of a model for that subgroup.

### Tension 4: Synthetic and augmented data can diagnose or distort

Synthetic elderly portraits may help stress-test hidden failure, but they can also invent artifacts that do not match historical image degradation. Synthetic cohorts should be treated first as sensitivity analysis, not training ground truth.

## 8. Top 3 Research Directions

### Rank 1

Working title: Conditional-shift-aware intervention audit for historical facial age estimation

Research question: In historical facial age estimation, when age or gender balancing improves visible distribution balance, does elderly reliability still degrade because of conditional shift across archive source, image quality, era, gender, or label reliability?

Why it ranks first: It has the strongest thesis fit and proposal potential. It directly explains aggregate masking, balancing instability, subgroup degradation, cascade fragility, and historical domain shift in one experiment.

Possible data: Thesis portrait images, age labels, gender labels, natural and balanced training splits, predictions, residuals, embeddings, archive/source metadata if available, period proxies, image-quality scores, and label-source confidence if available.

Possible method: Compare natural training, age-balanced training, gender-balanced training, source-aware weighting, and intersection-aware weighting; evaluate fixed age/gender groups, age-source-quality intersections, and embedding clusters; test whether residual patterns persist after visible balancing.

Evaluation metric: Global MAE, elderly MAE, worst-intersection MAE, residual underestimation rate, residual IQR, subgroup calibration error, conditional residual shift, cross-axis degradation delta, and bootstrap confidence intervals.

Thesis connection: This directly formalizes why balancing sometimes worsened elderly performance and why global MAE was insufficient.

Risk or limitation: Metadata and subgroup support may be limited, so proxy variables and small-cell uncertainty must be handled explicitly.

中文判断: 这是最适合主线 proposal 的方向, 因为它把 thesis 的 empirical surprise 变成 testable mechanism。

### Rank 2

Working title: Validity-unit-aware uncertainty monitoring for historical portraits

Research question: Can subgroup- and source-conditioned uncertainty monitoring detect elderly undercoverage, false confidence, or needed abstention before global MAE changes?

Why it ranks second: It is technically feasible and strongly aligned with trustworthy ML. It extends my thesis residual diagnostics into a deployment-style monitoring contribution.

Possible data: Thesis predictions, residuals, validation/test splits, age and gender groups, source/period proxies, embeddings, image-quality scores, and calibration data.

Possible method: Compare pooled conformal intervals, age-group intervals, source-conditioned intervals, multi-distribution robust intervals, and OOD/image-quality-triggered abstention; evaluate simple regression, multi-task, and cascaded models.

Evaluation metric: Marginal coverage, elderly coverage, worst-source elderly coverage, interval width, abstention rate, false-confidence rate, subgroup calibration error, OOD score separation, global MAE, and early-warning lead time.

Thesis connection: This extends aggregate masking from point error to uncertainty validity and tests whether elderly residual variance can be monitored before average performance fails.

Risk or limitation: Conformal validity depends on exchangeability and enough calibration support; source-aware calibration may require conservative grouping.

中文判断: 这是最自然的 monitoring 方向, 可以把 residual plots 升级成 uncertainty-aware reliability protocol。

### Rank 3

Working title: Deployment-like evaluation design for historical age-model selection

Research question: How do archive-aware, period-aware, structure-aware, and decision-target-aware validation protocols change the ranking of simple regression, balanced, multi-task, and cascaded age-estimation models?

Why it ranks third: It has strong feasibility and direct thesis continuity, but it is slightly broader than the first two directions. It can serve as the experimental foundation for them.

Possible data: Thesis dataset, model predictions from thesis architectures, archive/source metadata or proxies, period labels, image-quality scores, age-bin decision targets, and residual/correctness panels.

Possible method: Compare random splits, archive holdouts, period holdouts, source-quality stratified splits, and age-bin decision evaluation; test whether the model selected by global MAE differs from the model selected by elderly reliability, worst-slice MAE, coverage, or decision-target metrics.

Evaluation metric: Model-rank disagreement, global MAE, elderly MAE, worst-group MAE, age-bin error, residual skew, subgroup calibration error, subgroup coverage, and decision-specific failure rate.

Thesis connection: This directly retests the thesis conclusion that simpler regression generalized better than complex cascaded routing under more deployment-like validation.

Risk or limitation: Archive and period proxies may be noisy, so the protocol must separate confirmed metadata from diagnostic proxies.

中文判断: 这是很稳的 experimental protocol 方向, 适合作为 proposal 方法基础。

## 9. Topic Map Decision

Topic maps reviewed as candidates from the project rules: `topic_maps/distribution_shift.md`, `topic_maps/fairness_subgroup_error.md`, `topic_maps/trustworthy_ai.md`, `topic_maps/ai_governance.md`, and `topic_maps/multimodal_authenticity.md`.

No topic map was edited this week.

Reason:

- The project rule says topic maps should be updated only when a deep paper card produces a stable concept.
- This week had no new deep paper cards.
- Existing topic maps already contain related Week 03 and Week 04 concepts on hidden slices, burden movement, subgroup trust boundaries, and mechanism-first diagnosis.
- The Week 12 candidate concepts are strong, but they need deep paper verification before promotion.

Candidate concepts to promote after deep reading:

- Conditional shift versus marginal balancing
- Failure movement after intervention
- Validity unit across data, labels, and uncertainty
- Cross-axis subgroup intervention audit
- Decision-target-aware external validation

中文判断:

这周不更新 topic maps 是合适的。虽然 concept 已经重复出现, 但还缺 deep paper card 来确认方法细节和适用边界。下一步应先 deep-read single-axis intervention、multi-distribution conformal prediction 或 TRUECAM。

## 10. Proposal Seed

English, reusable paragraph:

My proposed PhD direction studies conditional-shift-aware subgroup reliability under distribution shift. Building on my thesis on historical facial age estimation, I will investigate why aggregate performance can hide elderly-group degradation and why interventions such as visible age balancing or gender-conditional routing can worsen vulnerable subgroup reliability. The core claim is that subgroup interventions should be evaluated as mechanism-specific hypotheses rather than assumed fixes. I will compare random, archive-aware, period-aware, and source-quality validation protocols; audit whether balancing changes marginal counts or the conditional feature-label relationship; and monitor subgroup reliability through residual diagnostics, subgroup calibration, conformal coverage, OOD scores, and abstention. The goal is to design an evaluation workflow that identifies whether elderly degradation comes from representation scarcity, conditional shift, label uncertainty, source contamination, or uncertainty undercoverage before choosing balancing, recalibration, residual correction, or deferral.

中文理解:

我的 PhD proposal 可以围绕 conditional-shift-aware subgroup reliability under distribution shift 展开。我的 thesis 已经显示 global MAE 会掩盖 elderly degradation, visible age balancing 有时会伤害 elderly performance, gender-conditional cascade 也比较脆弱。下一步我可以把这些结果组织成一个更清楚的框架: subgroup intervention 不能被当成默认修复, 而应该被当成 mechanism-specific hypothesis。具体来说, 我会比较 random、archive-aware、period-aware 和 source-quality validation protocols; 审计 balancing 是只改变 marginal counts, 还是改变 conditional feature-label relationship; 再用 residual diagnostics、subgroup calibration、conformal coverage、OOD scores 和 abstention 监控 subgroup reliability。

## 11. Weekly Reflection

English:

This week's reading reshaped my direction by making intervention evidence more central than intervention choice. I am no longer only asking whether balancing, reweighting, synthetic augmentation, representation harmonization, or conformal monitoring is useful. I am asking what failure mechanism each intervention assumes, and whether the evidence supports that assumption under historical source and subgroup shift.

My thesis findings now feel like a compact case study of a broader problem. Aggregate MAE hid elderly degradation, balancing sometimes worsened the elderly group, and the cascaded conditional model was fragile because each step relied on a reliability assumption that was not fully tested. My evolving PhD direction should therefore focus on building evaluation protocols that expose these assumptions: where the failure unit is, which conditional relationship changed, whether uncertainty remains valid for elderly-source slices, and whether an intervention moves risk elsewhere.

I am becoming a researcher who treats subgroup reliability as an evidence chain. The chain begins with visible degradation, tests marginal versus conditional mechanisms, audits intervention side effects across axes, and adds uncertainty-aware monitoring when reliable point estimation is not supported. This keeps my work close to historical facial age estimation while making the contribution broader and technically defensible.

中文:

这周的阅读让我把 research direction 更明确地放在 intervention evidence 上, 而不是 intervention choice 上。我现在不只是问 balancing、reweighting、synthetic augmentation、representation harmonization 或 conformal monitoring 是否有用。我更关心每个 intervention 假设了什么 failure mechanism, 以及这个假设在 historical source shift 和 subgroup shift 下是否有证据支持。

我的 thesis 现在像一个更大问题的 compact case study。Global MAE 掩盖 elderly degradation, balancing 有时伤害 elderly group, cascaded conditional model 脆弱, 是因为每一步都依赖某种 reliability assumption, 但这些 assumption 没有被充分测试。我的 PhD 方向应该围绕 evaluation protocol 展开: failure unit 在哪里, 哪个 conditional relationship 改变了, uncertainty 对 elderly-source slices 是否仍然 valid, intervention 是否把风险移到了别处。

我正在成为一种把 subgroup reliability 看成 evidence chain 的研究者。这个 chain 从 visible degradation 开始, 然后区分 marginal versus conditional mechanisms, 审计 intervention side effects across axes, 最后在 reliable point estimation 不成立时加入 uncertainty-aware monitoring。这样既保留 historical facial age estimation 的 grounding, 也能形成更广泛、更技术扎实的 contribution。

## 12. Deep Reading Queue

Create at most two deep paper cards this week.

- Priority 1: `Single-Axis Fairness Interventions Produce Asymmetric Cross-Axis Effects in Clinical Prediction`
- Priority 2: `Multi-Distribution Robust Conformal Prediction`
- Deferred: `Implementing trust in non-small cell lung cancer diagnosis with a conformalized uncertainty-aware AI framework`; `The MAMA-MIA Challenge`; `Data Representation Bias and Conditional Distribution Shift Drive Predictive Performance Disparities in Multi-Population Machine Learning`; `Towards Fairness under Label Bias in Image Segmentation`; `FEATMAP`

## 13. Next Week Plan

- [ ] Deep-read the single-axis fairness intervention paper and decide whether `failure movement after intervention` is stable enough for topic-map promotion.
- [ ] Deep-read `Multi-Distribution Robust Conformal Prediction` if time allows and extract a regression-compatible version of source/subgroup validity units.
- [ ] Draft a thesis-extension experiment that separates marginal age balancing from conditional elderly-source reliability.
- [ ] Keep topic maps unchanged until at least one deep paper card verifies the Week 12 candidate concepts.
- [ ] Verify preprint status for the clinical and population-transfer papers before using them in formal proposal text.
