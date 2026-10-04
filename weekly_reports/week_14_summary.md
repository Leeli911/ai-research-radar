# Weekly Research Summary — Week 14

Calendar window: **2026-09-28–2026-10-04**, Asia/Shanghai. Week 14 follows the repository sequence, not ISO numbering. Updated through October 4; this replaces the September 30 partial synthesis for the same window.

**Coverage / 阅读范围:** I reviewed all five available daily notes: [September 30](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/daily_notes/2026-09-30.md), [October 1](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/daily_notes/2026-10-01.md), [October 2](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/daily_notes/2026-10-02.md), [October 3](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/daily_notes/2026-10-03.md), and [October 4](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/daily_notes/2026-10-04.md): 15 selected papers. September 28–29 have no notes. No new deep paper card was available for these selections; no topic maps were changed.

**Evidence boundary / 证据边界:** This is a synthesis of the repository's screening notes and their recorded primary-source checks, not a fresh full-paper verification or a field-wide literature survey. Paper findings below are attributed to those notes; my proposed historical age-regression transfers remain hypotheses. I ground thesis connections in the research profile and distribution-shift proposal Markdown, without claiming a fresh thesis PDF analysis. 我综合的是本周筛选记录，不把选文共性当作全领域趋势，也不把分类、医疗或模拟结果直接当作历史人像回归的保证。

## 1. Technical Patterns / 技术主题

| Repeated pattern | Evidence across the reading | My research implication |
| --- | --- | --- |
| Shift changes several different objects | Sep 30: FOCUS cross-dataset evaluation and SAGE target summaries; Oct 1: GUARD source compatibility; Oct 2: between-/within-group robustness; Oct 3: evaluation-mixture sensitivity | I separate age prevalence, within-age visual conditions, and label/source validity rather than calling every change demographic imbalance. |
| Better summaries need not mean better elderly outcomes | Oct 1: subgroup utility and cumulative disparity; Oct 2: fixed confidence and training-run averages; Oct 3: error ranks and multiplicity | I report absolute elderly error, error tails, and uncertainty alongside aggregate scores, gaps, and model rankings. |
| Intervention strength depends on evidence | Sep 30: SAGE and ACP; Oct 1: GUARD; Oct 2: learned robustness parameters | I compare modest corrections with unchanged regression at matched target-label and validation budgets. More source data or stronger balancing is not automatically more protection. |
| Monitoring signals answer different hypotheses | Oct 2: fixed-confidence blind spots; Oct 4: WATCH, risk-violation testing, and proxy-based TTA monitoring | I distinguish input change, failure of adaptation assumptions, and unacceptable observed risk. Quiet confidence monitoring cannot certify elderly reliability. |
| A warning needs independent confirmation | Oct 2: seed versus sampling variation; Oct 3: unstable subgroup rankings and query access; Oct 4: label timing and sequential assumptions | I separate effect magnitude, statistical support, and actionable evidence. Model-output queries cannot substitute for checked age labels. |

中文：本周的共同技术主线是把“变化了什么、改善了谁、证据有多稳”分开。年龄组成变化不等于组内图像变难；差距缩小不等于老年组改善；置信度稳定不等于误差稳定；风险大也不等于小样本已经足以支持确定结论。

## 2. Conceptual Shifts / 概念变化

My [Week 13 report](/Users/apple/Documents/Codex/2026-05-28/codex-phd-research-radar-1-2/ai-research-radar/weekly_reports/week_13_summary.md) emphasized evidence validity. The September 30 partial report translated this into matching intervention strength to target evidence. Four further notes sharpen that direction into **specifying what a reliability claim measures and what evidence can support it**.

I now need to declare five things before claiming improvement: the target population, the loss or decision consequence, the subgroup, the observation horizon, and the information available to the method. A global-MAE improvement, a smaller disparity, a stable uncertainty histogram, and a valid risk alarm are different claims. Representation instability remains a possible mechanism from my proposal; this week's reading does not establish it as the cause of my elderly failures.

中文：我的方向从“证据决定干预强度”进一步变为“先定义可靠性结论，再判断证据是否足够”。我需要明确总体、损失、子群、时间范围和可用信息。表征不稳定仍是待检验机制，不能因为方向吻合就认定它解释了 thesis 的结果。

## 3. Strongest Connections to My Thesis / 与硕士研究的连接

- **Aggregate masking:** My global MAE can hide elderly mean error, severe underestimation, or archive-specific failure. The new extension is to check masking inside equal-uncertainty bins and across time as well. I must not merge these distinct aggregation axes into a single fairness score.
- **Balancing instability:** I distinguish an actual change in within-group residuals after retraining from a ranking change caused only by evaluation weights. SAGE and learned robustness motivate partial correction; neither establishes why my original resampling harmed elderly portraits.
- **Subgroup degradation:** I pair elderly error severity with sample counts, uncertainty, and cross-archive replication. An underpowered test does not demonstrate safety; the largest point estimate does not establish a stable worst group.
- **Cascade fragility and simpler regression:** I retain simple regression as the baseline and compare both error and how detectable that error is. Gate confidence, head uncertainty, and end-to-end age error are separate quantities. Routing causality needs controlled analysis, not only an association between cascade use and poor performance.

中文：我最强的 thesis 连接是把老年组失败拆成误差、评估组成、证据精度和可监测性四个问题。平衡与级联都要在相同人物和档案上配对比较；简单回归的优势需要跨档案、跨种子复查，而不是被提升为普遍定律。

## 4. Contradictions and Boundaries / 矛盾与边界

These are tensions between objectives and assumptions, not necessarily contradictory empirical results.

1. **Smaller disparity versus lower harm:** The October 1 retraining note reports that gaps can shrink while both groups deteriorate. I require absolute elderly loss alongside every disparity result.
2. **Robustness gains versus average performance:** The October 2 bilevel-robustness note records a worst-group/average trade-off. I preserve the trade-off rather than report a universal improvement; validation-selected protection may itself fail on a new archive.
3. **Stable confidence versus reliable proxies:** The October 2 confidence paper motivates blind-spot tests; October 4 proxy monitoring depends on proxy validity. These are compatible: I must test the assumption within elderly cases before using the proxy.
4. **Large subgroup warning versus reproducibility:** The October 3 multiplicity note records weak power, unstable rankings, and failure of the near-optimality condition. I use it as a limitation reference, not a validated index to adopt.
5. **Adaptation alarm versus risk alarm:** WATCH can reject an adaptation-compatible null when weights or assumptions fail; this does not uniquely identify harmful concept drift. Observed-loss risk tests require labels, while proxy tests depend on additional assumptions.
6. **Coverage versus useful intervals:** ACP's classification and audit-group results do not automatically protect elderly regression intervals. I retain coverage and width together and verify target calibration assumptions before transfer.

中文：这些张力要求我分别报告绝对损失、组间差距、平均与最差组权衡、代理有效性和证据精度。没有告警不能当作安全证明；分类覆盖保证不能直接移植到年龄区间。

## 5. Top 3 Research Directions / 三个优先方向

I apply the weekly ranking rubric explicitly. Ratings are planning judgments; data availability and publication novelty remain unverified.

| Rank | Direction | Thesis / strategic fit | Feasibility | Proposal potential | Novelty | Data availability | Long-term fit |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Cross-source audit separating mixture effects from elderly error | Very high | High if saved predictions survive | High; concrete first study | Moderate unless it yields reproducible failure diagnosis | Predictions, true ages, person/archive IDs need checking | Very high |
| 2 | Partial balancing under composition and within-group shift | Very high | Moderate; small-head retraining | High; directly tests backfire | Potential empirical contribution, not yet established | Training features, labels, independent archive required | Very high |
| 3 | Evidence-valid subgroup risk monitoring | Very high | Moderate to low until labels/support are confirmed | High; clear monitoring question | Subgroup transfer and power require literature verification | Ordered replay and checked elderly labels required | Very high |

### Rank 1 — Cross-source audit of apparent reliability gains

- **Research question:** With predictions fixed, can changes in elderly prevalence reverse the ranking of simple, balanced, and cascaded age models while within-elderly severe-error risk stays unchanged, and does the pattern recur across held-out archives?
- **Why it matters:** I can separate an evaluation-mixture artifact from an actual benefit of balancing before developing another intervention.
- **Possible data:** Saved model predictions, reference ages and provenance, person IDs, and archive IDs; access remains unconfirmed.
- **Possible method:** Predefine age groups and an evaluation-weight grid on development data. Keep every within-group residual distribution fixed while changing test weights; repeat by archive. Separately compare actual within-group model differences on identical people. Use person-clustered paired uncertainty estimates. Add asymmetric missed-elderly costs only as declared sensitivity scenarios, not inferred social utilities.
- **Evaluation metric:** Global/elderly MAE, signed residual mean (prediction minus reference age), severe-underestimation probability, and model-ranking reversals across the declared grid. Report cell counts and interval uncertainty.
- **Thesis connection:** Directly tests aggregate masking and the interpretation of balancing instability while retaining cascade and simple-regression comparisons.
- **Risk or limitation:** Mixture reweighting cannot simulate within-group visual change. Sparse archives may prevent replication; without source IDs I can perform only a mixture audit, not claim cross-source validation.

中文：我首先固定预测，只改变评估权重，检验排名反转是否伴随真实老年误差改善。这个低成本实验能澄清“看起来更好”与“老年组确实更好”的区别，但不能模拟新的视觉条件。

### Rank 2 — Partial balancing under compound shift

- **Research question:** Does validation-selected partial balancing reduce elderly MAE more consistently than full balancing when age composition and within-age image quality change together?
- **Why it matters:** My balancing backfire needs competing mechanisms and controlled tests, rather than a retrospective explanation based only on sample counts.
- **Possible data:** Recoverable thesis portraits or frozen features, ages, quality/source metadata, identity-disjoint splits, and one untouched archive.
- **Possible method:** Compare unweighted, fully balanced, and a fixed five-level partial-weight grid with the same backbone and small heads. Select weights on development worst-age-group MAE under a predeclared global-error constraint. Cross composition-only, quality-only, and combined stress tests; then evaluate the untouched archive. Start with matched seeds as a variance pilot. Source-summary noise is a later factor if suitable summaries exist; this baseline is not SAGE or a bilevel-method reproduction.
- **Evaluation metric:** Paired elderly/global MAE differences, severe underestimation, worst prespecified group error, effective sample size, and between-seed spread. Report trade-offs; a small pilot cannot estimate an extreme error quantile precisely.
- **Thesis connection:** Tests balancing instability and whether simple versus conditional heads differ in sensitivity to the same shift.
- **Risk or limitation:** Artificial corruption is not historical change, and weak validation support can select unstable weights. A null benefit of partial balancing would weaken the excessive-correction hypothesis rather than settle all causes.

中文：我用同一骨干、固定权重网格和配对种子，把组成变化与组内质量变化分开测试。部分平衡若无优势，也能排除一种解释；验证集选择本身仍可能不稳定。

### Rank 3 — Subgroup risk monitoring with declared evidence access

- **Research question:** At the same total false-alarm budget, can pooled-plus-elderly monitoring detect increased severe elderly underestimation earlier than pooled-only monitoring under archive shift?
- **Why it matters:** I can translate hidden elderly failure into a specific risk event and assess whether a monitor has enough evidence to detect it.
- **Possible data:** Frozen predictions and independently checked ages, person/archive IDs, and real ordering where available. Otherwise I use explicitly simulated replay, not a historical deployment claim.
- **Possible method:** Fix an elderly threshold, severe-underestimation threshold, and acceptable event probability on development data. Compare paired streams with immediate and fixed delayed labels. Allocate total alpha 0.05 across active tests, checking the individual sequential assumptions before claiming family-wise control. Compare balanced/unbalanced regression and cascades separately. Audit uncertainty proxies offline with labels hidden from the proxy; implement a label-free sequential variant only after its assumptions are checked.
- **Evaluation metric:** False-alarm probability in null replays, missed violations, detection delay in elderly observations and total arrivals, and absolute elderly error. Report proxy high-error recall separately from sequential test validity. Keep raw MAE descriptive; use a bounded binary event for the risk test.
- **Thesis connection:** Tests whether subgroup failure hidden by global MAE becomes visible earlier, and whether simpler regression is also easier to monitor reliably.
- **Risk or limitation:** Sparse elderly cases, dependent observations, label delay, and proxy failure may prevent useful detection. Silence is inconclusive. Age 60 and ten-year underestimation from the daily note remain provisional choices, not verified thesis thresholds.

中文：我把严重低估定义成有界事件，在统一误报预算与标签延迟下比较整体和老年组监控。代理诊断与顺序检验分开；老年样本不足或代理失效时，监控沉默不能支持安全结论。

## 6. Research Function Chain / 研究链条

**Diagnosis:** source-held-out residuals and fixed-mixture audits → **Explanation:** test composition, within-group difficulty, weighting strength, and routing as competing hypotheses → **Intervention:** validation-selected modest correction → **Monitoring:** distinguish distribution, adaptation-assumption, and risk signals → **Evaluation:** compare absolute elderly outcomes, uncertainty, and information budgets.

The chain is strongest in diagnostic design. I have no new experiment establishing a mechanism or subgroup monitoring guarantee. 中文：当前最成熟的是诊断协议，机制解释、干预收益与监控有效性仍需实验支持。

## 7. Proposal Seed

**English:** My thesis showed that historical facial age models can hide elderly underestimation behind acceptable average error, and that balancing or conditional routing can worsen reliability. I propose to study when an apparent reliability improvement represents a reproducible reduction in elderly error. I will first separate evaluation-mixture effects from within-group model differences across archives. I will then test partial balancing under controlled composition and image-quality shifts, retaining simple regression as a baseline. Finally, I will assess whether subgroup risk monitoring detects severe underestimation at a declared false-alarm and label budget. The intended contribution is an evaluation protocol that connects subgroup outcomes to the evidence needed to support them, including explicit cases where sparse labels, unstable rankings, or invalid uncertainty proxies prevent a reliable conclusion.

**中文：** 我的 thesis 显示，可接受的平均误差可能掩盖老年组低估，平衡与条件路由也可能加重失败。我计划研究表面上的可靠性改善何时对应可复现的老年误差下降：先跨档案区分评估组成与组内误差，再检验复合漂移下的部分平衡，最后在明确误报和标签预算下评估子群风险监控。目标是建立连接群体结果与证据要求的协议，并明确小样本、排序不稳或代理失效时不能得出哪些结论。

## 8. Read, Reject, Develop / 精读、取舍与下一步

**Read next:** I revise the September 30 FOCUS/SAGE queue in light of the four new notes. My two deep-reading priorities are **How Much Can Reliability Drift Under a Fixed Confidence Distribution?** (October 2) for monitoring blind spots, and **On Continuous Monitoring of Risk Violations under Unknown Shift** (October 4) for the exact null, bounded loss, label timing, and subgroup error-budget requirements. Both are already daily-card recommendations. I create no cards in this synthesis; any subsequent work must respect the two-card weekly cap.

**Retain/defer:** FOCUS remains my benchmark-design reference; SAGE/GUARD and ACP remain conditional method references. I retain the multiplicity paper as a warning about insufficient evidence and the retraining paper as a later replay-design reference. This prioritization does not discard their unresolved checks.

**Reject:** I reject treating smaller gaps as improvement, output queries as ground-truth labels, stable confidence as safety, or arbitrary archive order as real temporal evidence. I defer new backbones, full bilevel training, and online adaptation until the basic audit is feasible.

**Develop next:** I first inventory predictions, age provenance, person/archive IDs, elderly counts, and available model variants. I then freeze the Rank 1 population weights and error definitions before inspecting test comparisons. If data access fails, I record that boundary rather than fabricate benchmark results.

中文：本周新增阅读后，我把两篇监控论文放到精读首位，FOCUS 保留为评估模板，SAGE 等方法待数据条件明确后再推进。下一步先核实已有预测和元数据，固定第一项实验协议，不直接扩大系统或模型复杂度。

## 9. Topic-Map Decision / 主题图决定

I leave all topic maps unchanged. The candidate structure is **claim-specific subgroup evidence**, distinguishing evaluation composition, intervention support, and monitoring validity. No new deep card for this week's papers establishes it as a stable concept, as required by AGENTS.md. The existing maps already include hidden subgroup error and reliability monitoring; daily-note convergence alone does not justify promotion. Governance and multimodal authenticity receive no new supported structure.

中文：我保留“针对具体结论的子群证据”作为候选结构，但没有新精读卡确认，因此不更新主题图，也不重写已有内容。

## 10. Weekly Reflection / 每周反思

**English:** I am becoming a researcher who asks both where models fail unevenly and what evidence makes that failure measurable, reproducible, and detectable. This week makes my PhD direction narrower: begin with historical age predictions, separate population choices from model behavior, and test monitoring only against a clearly defined risk. My thesis supplies concrete failures, not a license to assume their causes. A useful contribution may be showing precisely when a seemingly fairer model or quieter monitor does not support a stronger reliability claim.

**中文：** 我正在成为一名同时研究“不均匀失败”和“支持失败结论的证据”的研究者。本周让我进一步收窄博士方向：从已有历史年龄预测出发，区分总体选择与模型行为，再围绕明确风险检验监控。Thesis 提供具体问题，而不是现成的因果解释。我的贡献可以是清楚说明：看似更公平的模型或更安静的监控，什么时候并不足以支持更强的可靠性结论。
