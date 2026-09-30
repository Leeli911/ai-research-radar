# Weekly Research Summary - Week 14

Week: 14 in the repository report sequence, not the ISO calendar week
Calendar window: 2026-09-28 to 2026-10-04
Coverage through: 2026-09-30, Asia/Shanghai; partial-week synthesis
Daily notes reviewed: [2026-09-30](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/daily_notes/2026-09-30.md), containing three selected papers
Missing elapsed-day notes: 2026-09-28 and 2026-09-29; October 1–4 are still future dates
New paper cards reviewed: none
Topic maps updated: none
Main research identity: diagnosing subgroup reliability under shift and matching intervention strength to available target evidence

**Evidence boundary / 证据边界:** I synthesize all available notes in the current week: one note, not a week of independent observations. Repetition below means convergence across its three papers, not a demonstrated field-wide trend. I rechecked their primary arXiv abstracts and metadata on September 30; full-paper assumptions remain to be verified. My historical age-regression experiments are proposals, not reported results. No notes exist for September 14–27, so I do not infer developments during that gap.

## 1. What Became Clearer / 概念变化

My [Week 13 synthesis](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/weekly_reports/week_13_summary.md) emphasized validating sources, labels, and subgroup support before trusting intervention results. This week's limited reading makes that idea more operational: I need to specify what target evidence is available, what it can identify, and how much intervention it supports. External evaluation data, population summaries, and a small checked target sample are distinct evidence settings. I cannot treat them as interchangeable guarantees of elderly reliability.

My existing [proposal direction](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/grounding/proposal_distribution_shift.md) remains relevant. Representation instability is one candidate explanation to test within a source-aware audit; this week's papers do not establish that it caused my thesis failures. The immediate advance is a more testable evaluation design, rather than a replacement research identity.

中文：此前我的重点是“干预前先验证证据是否可信”。本周进一步明确：目标域究竟提供了外部评估数据、群体统计摘要，还是少量核验标签？这些证据支持的结论和干预强度不同。表征不稳定仍是待检验机制；我目前最适合推进的是跨来源评估，把隐藏的老年组退化与可获得的证据联系起来。

## 2. Technical Patterns and Strongest Papers / 技术模式与核心论文

### A. Distribution shift requires several evaluation axes

**Verified from abstract:** [FOCUS: Benchmarking Retinal Model Generalization from Foundation Vision Encoders to Multimodal LLMs](https://arxiv.org/abs/2609.33158) evaluates retinal classification across ten datasets, considering ranking, calibration, subgroup disparities, and image quality. The authors report heterogeneous external transfer after fine-tuning and no consistently dominant model family. The arXiv record lists NeurIPS 2026 Evaluations & Datasets acceptance.

**Research function:** Diagnosis → Evaluation; potential input to Monitoring. **Usefulness:** proposal anchor for evaluation design.

**My interpretation:** I can test whether model rankings change when historical portraits are evaluated by archive, age group, and quality rather than pooled MAE. This connects directly to aggregate masking and subgroup degradation in my thesis. Retinal classification results do not establish which age-regression model will be best.

中文：我最需要借鉴的是跨数据集、分组、校准和图像质量共同构成的评估设计。医学分类结果不能直接作为历史年龄回归的证据，但可以指导我检验整体排名是否掩盖老年组失败。

### B. Adaptation strength depends on target-summary uncertainty

**Verified from abstract:** [Summary-powered prediction under distribution shift](https://arxiv.org/abs/2609.30908) proposes SAGE, a one-step update using target subgroup summaries. Its step size accounts for sampling and distributional uncertainty. The comparison with entropy balancing and the asymptotic risk results depend on the paper's shift model; the abstract also reports empirical comparisons.

**Research function:** Explanation → Intervention → Evaluation. **Usefulness:** method reference for examining balancing strength.

**My interpretation:** My balancing failures motivate a controlled intervention-strength experiment. This paper supplies a possible statistical framing, not a retrospective explanation of why elderly error increased. I still need to verify exactly which summaries and outcome information SAGE requires; archive counts alone may not suffice to estimate its update.

中文：我可以把平衡策略当作有强度、也有不确定性的干预进行检验。SAGE 尚不能解释我论文中的失败原因；实施前必须核对摘要需要哪些变量，不能默认年龄或性别计数足以完成方法。

### C. Reliability monitoring needs failure evidence, not only drift signals

**Verified from abstract:** [Audited Conformal Prediction for Classification under Unknown Distribution Shift](https://arxiv.org/abs/2606.14909) uses a small labeled target sample to train a failure auditor. It distinguishes a strategy with marginal coverage and improved empirical conditional performance from another with explicit group-conditional guarantees, and examines set-size trade-offs.

**Research function:** Monitoring → Intervention → Evaluation. **Usefulness:** method reference and warning about pooled coverage.

**My interpretation:** I can investigate residual-risk auditing for elderly portraits, but classification guarantees do not automatically transfer to regression intervals. The exact assumptions, sample splitting, and group definitions need full-paper verification. This is a June method paper read this week, not a September publication.

中文：监控需要区分分布变化与实际失败风险，也需要区分整体覆盖率、特定组覆盖率和任意条件覆盖率。我的回归扩展只能作为待验证设计，不能直接继承分类论文的保证。

**Repeated pattern / 重复主题:** Across these readings, I see target-specific evaluation and limits on pooled reliability claims. The genuinely new connection for my notes is that the form and quality of target evidence should constrain the intervention I attempt. This remains a candidate synthesis from one day's reading.

## 3. Strongest Connections to My Thesis / 与硕士论文的连接

| My thesis observation | My proposed reinterpretation | Test that could challenge it |
| --- | --- | --- |
| Aggregate MAE masked elderly failure | Pooling across archives and quality strata may add another layer of masking. | Compare global, elderly, and archive-specific elderly MAE on identical held-out portraits; inspect model-ranking reversals. |
| Balancing sometimes worsened elderly performance | Correction strength or poor within-group support may matter alongside marginal counts. | Vary balancing strength on a fixed evaluation population; report effective sample size and elderly error across seeds. |
| Cascaded conditional models were fragile | Routing errors and downstream age errors may respond differently to source shift. | Evaluate route-specific residuals and, where trustworthy gender labels exist, compare predicted versus reference routing as a diagnostic. |
| Simpler regression generalized better | A stable base model may offer a useful starting point for a limited reliability correction. | Compare frozen regression, a simple residual correction, and the cascade under matched target evidence and held-out evaluation. |

中文：我把这些解释保留为可证伪假设。跨来源关联不能直接证明来源造成退化；平衡失败也可能来自标签噪声、样本支持不足或训练差异。简单回归是重要基线，但本周阅读不能证明它总是更好。

## 4. Contradictions and Open Problems / 矛盾与未决问题

- **Population improvement versus elderly protection:** A target-average improvement need not reduce elderly error. I will report both and treat subgroup harm as an outcome, not assume that a population objective protects every group.
- **Summary access versus label access:** Summary-based adaptation and a labeled-target auditor have different information budgets. I will evaluate them in separate evidence settings, with matched-budget comparisons within each setting.
- **Auditing versus balancing:** An auditor detects risk; balancing changes a predictor. I will measure detection quality for auditors and prediction changes for interventions, then compare complete policies on the same untouched test set. A single “auditing beats balancing” score would obscure the distinction.
- **Coverage versus usefulness:** Wider intervals can raise coverage without improving point predictions. I will pair group coverage with interval width and MAE, and keep empirical improvements separate from formal guarantees.

中文：核心矛盾是总体收益不等于老年组保护、不同方法获得的信息不同、诊断与修正的目标不同，以及覆盖率提升可能伴随区间负担增加。这些问题需要由实验协议明确区分。

## 5. Conceptual Chain Coverage / 研究链条

- **Diagnosis:** source-held-out residual panels can localize masking.
- **Explanation:** summary uncertainty, limited subgroup support, and routing fragility remain competing hypotheses.
- **Intervention:** I can compare bounded balancing or correction strengths after diagnosis.
- **Monitoring:** residual-risk auditing is promising when checked target labels exist; unlabeled drift alone cannot confirm elderly error.
- **Evaluation:** the common endpoint is held-out subgroup error and uncertainty quality under a declared evidence budget.

**Gap / 缺口:** I have no new experiment, verified regression guarantee, or temporal alert result. 当前链条在评估设计上最强，在机制验证和真正的提前预警上仍缺证据。

## 6. Top 3 Research Directions / 研究方向排序

I apply the weekly rubric explicitly. These are planning judgments, not measured scores; data access and publication novelty remain unverified.

| Rank and direction | Thesis / strategic fit | Technical feasibility | Proposal potential | Novelty | Data availability | Long-term identity fit |
| --- | --- | --- | --- | --- | --- | --- |
| 1. Cross-source audit of elderly age reliability | Very high | High if predictions and source IDs are recoverable | High: clear failure and evaluation target | Moderate; needs contribution beyond metric reporting | Thesis artifacts are a candidate, access unchecked | Very high |
| 2. Balancing strength under uncertain target summaries | Very high | Moderate; summary sufficiency must be checked | High: directly tests intervention backfire | Promising empirical question; literature check needed | Requires reliable summaries and held-out labels | High |
| 3. Target-label budgets for residual-risk auditing | High | Moderate; splitting reduces scarce subgroup support | High, but regression validation adds work | Uncertain relative to existing regression auditing | Requires a separately checked target sample | High |

### Rank 1 — Cross-source audit of elderly age reliability

- **Research question:** Does source-held-out evaluation change the ranking of simple regression, balanced models, and cascaded models when elderly MAE replaces global MAE as the primary outcome?
- **Why it matters:** This is the closest, most feasible extension of my thesis and supplies the baseline for the other directions.
- **Possible data:** Original predictions or rerunnable models, reference ages and their provenance, person IDs, archive IDs, and quality metadata if recoverable.
- **Possible method:** Predefine elderly groups and source splits; prevent portraits of the same person entering both development and evaluation. Compare all models on the same targets, with quality and label-confidence sensitivity checks. Audit embeddings only as an optional explanatory follow-up.
- **Evaluation metric:** Global and elderly MAE; worst-source elderly MAE with cell counts and uncertainty; signed residual mean using predicted minus reference age; frequency of ranking reversals. Estimate paired model differences with resampling at the independent person level where applicable.
- **Thesis connection:** Directly tests masking, subgroup degradation, balancing instability, and cascade fragility.
- **Risk or limitation:** Source and age composition may be confounded; sparse archive-age cells may prevent stable rankings. Without recoverable source IDs, I cannot claim a cross-source benchmark.

中文：我优先检验“按老年组和来源重新评估后，模型排名是否变化”。这最贴近已有经验，也能为后续方法提供共同基线；若来源元数据不可恢复，跨来源结论就不能成立。

### Rank 2 — Balancing strength under uncertain target summaries

- **Research question:** At fixed evaluation composition, does partial age/gender reweighting reduce elderly error more consistently than full target-summary matching as summary noise increases?
- **Why it matters:** It turns my balancing backfire into a narrow, falsifiable intervention question.
- **Possible data:** Source training examples, target summaries with documented provenance, and target development/test labels kept separate. Simulated summary noise is a controlled stress test, not evidence of actual archive noise.
- **Possible method:** Compare no weighting, naive balancing, full entropy balancing, and a predeclared grid interpolating between unit and balanced weights. Select strength using development evidence only. Add SAGE only after confirming summary requirements and applicable assumptions; my interpolation baseline is not a SAGE implementation.
- **Evaluation metric:** Change in elderly and global MAE, worst-source elderly error, variability across seeds, and weighted effective sample size, (sum of weights)^2 / sum of squared weights.
- **Thesis connection:** Tests whether correction strength and sample support help explain balancing instability.
- **Risk or limitation:** Matching observed summaries cannot repair all conditional shifts. Poor overlap can make even partial weighting unstable; using test-derived summaries or labels outside the declared access setting would invalidate the comparison.

中文：我先比较不加权、部分加权和完全匹配，不把自定义基线误称为 SAGE。目标是检验干预强度与摘要噪声的关系；结果若无改善，也能约束“平衡过强”这一解释。

### Rank 3 — Target-label budgets for residual-risk auditing

- **Research question:** At a fixed target-label budget, can a residual-risk auditor improve elderly interval coverage over global and fixed-group split-conformal regression baselines without excessive interval widening?
- **Why it matters:** This connects my residual diagnostics to a measurable uncertainty intervention.
- **Possible data:** Frozen age predictions and available embeddings, quality/source/route features, and checked target ages. Define true-age groups for evaluation; deployment-time grouping requires observable attributes or separately validated proxies.
- **Possible method:** Allocate separate target subsets to auditor fitting, calibration, and final testing; freeze groups before calibration. Compare budget curves under the same splits. Start with a small residual predictor and predeclared groups. Treat the regression design as an experiment, with any coverage claim conditional on its own assumptions.
- **Evaluation metric:** Elderly and worst-source coverage deficit at a predeclared nominal level, interval width, point MAE, and auditor detection of a prespecified large-error event. Report subgroup sample sizes and uncertainty across repeated splits.
- **Thesis connection:** Tests whether a reliability layer can expose undercoverage hidden by aggregate metrics without changing the base model.
- **Risk or limitation:** Small elderly samples may make three-way splitting impractical; arbitrary future shifts can invalidate calibration transfer. Detection delay is a later endpoint only if authentic observation order and label-arrival times are available.

中文：我把少量标签用于拟合、校准和独立测试，分别衡量覆盖率、区间宽度与失败检测。没有真实时间顺序和标签延迟记录时，我只报告离线审计，不声称实现提前预警。

## 7. Proposal Seed

**English:**

My master's thesis showed that historical facial age models can achieve acceptable aggregate error while degrading sharply for elderly portraits, and that balancing or conditional routing can worsen this failure. I propose to study what target-domain evidence is sufficient to evaluate and improve subgroup reliability under archive shift. I will begin with source-held-out comparisons of simple regression, balanced training, and cascaded models, measuring elderly error and signed residuals alongside global performance. I will then test whether uncertainty in target summaries should limit reweighting strength, and whether a small checked target sample supports useful residual-risk auditing. All comparisons will declare their information budgets, separate development from evaluation, and report sparse-group uncertainty. The intended contribution is a reproducible protocol linking evidence availability to intervention choice, with explicit cases where additional labels, metadata, or a simpler model are needed before a reliability claim is justified.

**中文理解：**

我的硕士研究发现，整体误差可接受时，老年人像仍可能明显退化，平衡训练和条件路由也可能加重失败。我计划研究跨档案来源变化下，需要哪些目标域证据才能评估并改善群体可靠性。首先比较简单回归、平衡模型和级联模型的老年组误差与残差，再检验摘要不确定性是否应限制加权强度，以及少量核验标签能否支持残差风险审计。所有实验明确证据预算，分离开发与测试，并报告小样本不确定性，形成连接证据可用性与干预选择的可复现协议。

## 8. Deep Reading and Topic Maps / 精读与主题图

1. **Read first — FOCUS:** Verify dataset splitting, label harmonization, subgroup support, and calibration measures before translating the benchmark design. This is the existing daily note's recommended paper card and my first priority.
2. **Read second — SAGE:** Verify the required summaries, outcome information, shift assumptions, and step-size selection before choosing an implementation. This is a weekly method-reading priority; any subsequent card remains within the two-card weekly cap.

**Deferred:** ACP full reading follows once target labels and the regression calibration design are feasible. I retain the earlier source-shortcut and label-provenance questions as background checks rather than expanding the immediate queue. I reject generic model-family leaderboard comparisons and unverified claims that balancing or auditing solves elderly reliability.

**Topic-map decision:** I made no edits. The existing distribution-shift, subgroup-error, and trustworthy-AI maps already cover masking, burden movement, and subgroup coverage. The candidate addition—matching intervention strength to available target evidence—has not been established by a new deep paper card. Governance and multimodal-authenticity maps receive no new supported structure from this reading. No deep cards were created in this run.

中文：先精读 FOCUS 的评估协议，再核对 SAGE 的信息需求。当前只保留候选概念，不更新主题图；精读确认后才考虑增加有证据支持的小节。

## 9. Next Week Plan / 下一步

- [ ] Confirm recoverable predictions, archive IDs, person IDs, age-label provenance, and elderly sample counts before committing to the benchmark.
- [ ] Draft one fixed source-held-out evaluation table for Rank 1; define groups and endpoints before inspecting test differences.
- [ ] Deep-read FOCUS, then SAGE; create at most two cards only after checking the full papers.
- [ ] Resolve source-to-protocol gaps: SAGE summary sufficiency, ACP sample splitting and group guarantees, and FOCUS subgroup sample support.
- [ ] Revisit this same partial-week report when additional September 28–October 4 notes arrive, rather than duplicate the window in a new report.

中文：我下一步先核实数据可用性并固定评估协议，再决定方法扩展。若本周出现新笔记，我会补充本报告，避免把同一周重复编号。

## 10. Weekly Reflection / 每周反思

**English:**

This short reading window makes my research direction more concrete without settling its mechanisms. I am becoming a researcher who asks what evidence supports a subgroup reliability claim, how that evidence changes under shift, and which intervention it can justify. My thesis gives me an empirical starting point; the immediate task is to make its model comparisons reproducible across sources. I will keep representation and routing hypotheses alive, while letting held-out evidence determine whether they explain elderly degradation.

**中文：**

这次阅读让我的研究方向更具体，但并未确定失败机制。我正在成为一名关注群体可靠性证据的研究者：一个结论由什么证据支持，这些证据在分布变化下是否仍然成立，又能支持多强的干预？我的硕士论文提供了起点，当前最重要的是建立可复现的跨来源比较。我会继续检验表征与路由假设，同时让独立评估决定它们能否解释老年组退化。
