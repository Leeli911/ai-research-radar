# Research Profile / 研究身份画像

## 1. Academic Background / 学术背景

**English**

I am trained in data science, with a master's degree from Uppsala University and earlier training in mathematics and applied mathematics. My technical background is grounded in computer vision, representation learning, model evaluation, subgroup analysis, calibration, and reliability monitoring. I also have professional experience with large-scale behavioral data, user-segment evaluation, production monitoring dashboards, and decision-oriented analytics.

My strongest empirical research experience comes from building and evaluating facial age and gender estimation models on historically structured portrait data. A related academic project on facial kinship recognition also strengthened my experience with embedding-based verification and diagnostic evaluation.

**中文**

我的背景是 data science，同时有数学与应用数学训练。硕士阶段主要做 computer vision、representation learning、模型评估、subgroup analysis、calibration 和 reliability monitoring。我也有实际工作经验，接触过大规模行为数据、用户分群评估、生产监控 dashboard 和 decision-oriented analytics。

我的核心研究经验不是单纯训练一个视觉模型，而是在历史人像数据中观察模型如何在不同年龄组、性别组和数据分布下产生不稳定表现。另一个 kinship recognition 项目也让我熟悉了 embedding-based verification 和 diagnostic evaluation。

## 2. Master Thesis / 硕士论文

**English**

My master thesis was titled **From Faces to Ages: Enhancing Historical Recognition with Transfer Learning**. It studied historical facial age estimation under domain shift. The task was motivated by historical demographic reconstruction and inclusive biometric modelling, using transfer learning to estimate age and gender from portrait images.

The thesis compared five neural architectures sharing a ConvNeXtV2-style backbone, including age regression, age-group classification, multi-task age-gender models, and a cascaded gender-conditional age estimation model.

**中文**

我的硕士论文题目是 **From Faces to Ages: Enhancing Historical Recognition with Transfer Learning**。它研究的是历史人像中的年龄估计问题，本质上是一个 historical domain shift 下的 facial age estimation 任务。

我比较了五类模型，包括连续年龄回归、年龄组分类、多任务年龄-性别预测，以及先预测 gender 再进入不同 age regression head 的 cascaded conditional model。这个工作让我看到，模型结构更复杂并不一定意味着在分布变化下更可靠。

## 3. Actual Technical Work / 实际技术工作

**English**

My thesis work included:

- historical facial age estimation;
- transfer learning with shared visual backbones;
- subgroup-wise evaluation by age group and gender;
- calibration analysis and prediction confidence inspection;
- residual diagnostics, including underestimation and variance patterns;
- balancing experiments for age and gender representation;
- comparison between regression, classification, multi-task, and cascaded conditional models;
- standardized evaluation panels including validation MAE, residual plots, scatter plots, and subgroup metrics.

**中文**

我的实际技术工作包括历史人像年龄估计、迁移学习、subgroup-wise evaluation、calibration analysis、residual diagnostics、数据平衡实验和多模型比较。我不只是看整体 MAE，而是看不同 age group、gender group 和模型结构下的误差模式。

这部分工作对我很重要，因为它让我意识到：模型评估不是一个单一平均指标问题，而是一个关于 subgroup reliability、distribution shift 和 decision-relevant monitoring 的问题。

## 4. Key Empirical Findings / 关键实证发现

**English**

1. **Aggregate metrics can hide subgroup failure.**  
   Good global MAE could mask severe elderly-group degradation.

2. **Balancing can worsen vulnerable subgroup performance.**  
   Dataset balancing improved some aggregate or group-level patterns, but sometimes increased elderly-group error.

3. **Cascaded conditional models were fragile.**  
   The gender-conditional cascaded model could perform well in general but degrade sharply for elderly age estimation under shift.

4. **Simpler regression models generalized better.**  
   Simpler regression-based designs were often more stable than more complex conditional routing strategies.

5. **Residual diagnostics revealed hidden structure.**  
   Elderly samples showed systematic underestimation and larger prediction variance, which were not fully visible from global metrics.

**中文**

我的几个核心发现是：

1. 整体 MAE 好看，不代表每个 subgroup 都可靠。elderly group 的失败可能被平均掉。
2. 数据平衡不一定解决 fairness，有时反而让 elderly-group performance 更差。
3. Cascaded gender-conditional model 在分布变化下比较脆弱。
4. 更简单的 regression model 有时比复杂模型更稳。
5. Residual plots 和 calibration analysis 能暴露整体指标看不到的问题。

这些发现共同说明：真正的问题不是“哪个模型平均误差最低”，而是“哪个模型在分布变化和 subgroup 差异下仍然可靠”。

## 5. Evolving Research Motivation / 研究动机的演变

**English**

My thesis started as a computer vision evaluation project. Over time, the empirical findings pushed me toward a broader question: how should machine learning systems be evaluated when data distributions change and subgroup failures are hidden by aggregate metrics?

This moves my interest from computer vision evaluation toward:

- distribution shift;
- subgroup reliability;
- fairness degradation;
- representation instability;
- uncertainty-aware monitoring;
- decision-relevant model evaluation.

**中文**

我的研究兴趣是从 computer vision evaluation 出发的。但 thesis 的结果让我意识到，真正有研究价值的问题不是单个模型在测试集上多准，而是模型在 historical shift、subgroup imbalance 和不同 decision context 下是否可靠。

所以我的兴趣正在从“视觉模型评估”转向“distribution shift 下的 subgroup reliability 和 decision-relevant monitoring”。

## 6. Current Core Research Questions / 当前核心研究问题

**English**

1. How does distribution shift create subgroup-specific reliability degradation?
2. Why can aggregate metrics hide serious subgroup failures?
3. When do balancing or fairness interventions improve reliability, and when do they worsen vulnerable subgroup performance?
4. How does representation instability under shift affect subgroup-level error?
5. How can monitoring systems detect early signs of subgroup degradation before deployment harm becomes visible?

**中文**

我现在最关心的问题是：

1. Distribution shift 如何导致 subgroup-specific degradation？
2. 为什么 aggregate metrics 会掩盖 subgroup failure？
3. Balancing 或 fairness intervention 什么时候有帮助，什么时候会伤害 vulnerable subgroup？
4. 表征在 shift 下不稳定时，是否会导致某些 subgroup 误差上升？
5. 如何提前监控 subgroup degradation，而不是等到整体指标崩溃后才发现？

## 7. Preferred Future Directions / 偏好的未来方向

**English**

My preferred directions are:

- subgroup-aware distribution shift diagnostics;
- representation stability analysis under domain or temporal shift;
- subgroup reliability monitoring after deployment;
- uncertainty-aware evaluation for vulnerable groups;
- decision-relevant evaluation protocols that connect errors to downstream consequences;
- data-centric diagnosis of hidden subgroup failure.

**中文**

我最适合继续发展的方向是：

- subgroup-aware distribution shift diagnostics；
- representation stability under shift；
- subgroup reliability monitoring；
- uncertainty-aware evaluation；
- decision-relevant model evaluation；
- data-centric failure diagnosis。

这些方向都能自然延伸我的 thesis，而不是突然跳到一个完全陌生的研究领域。

## 8. Directions I Intentionally Avoid / 有意避免的方向

**English**

I intentionally avoid directions that are weakly connected to my empirical background:

- generic AI hype;
- pure large-model product benchmarking;
- systems-heavy distributed infrastructure;
- architecture novelty without evaluation insight;
- vague fairness discussions without concrete metrics, data, or failure modes;
- governance work that lacks technical grounding.

**中文**

我需要避免的方向包括：

- 泛泛追 AI 热点；
- 只做大模型产品或榜单比较；
- 过重的 systems 或 infrastructure 研究；
- 只提出新架构但没有 evaluation insight；
- 没有具体指标和数据的泛泛 fairness 讨论；
- 缺少技术 grounding 的 AI governance。

## 9. What Kind of Researcher I Am Becoming / 我正在成为什么样的研究者

**English**

I am becoming a researcher who studies how machine learning models fail unevenly under changing data conditions. My focus is on diagnosing hidden subgroup degradation, understanding why interventions such as balancing or conditional routing can become fragile, and designing evaluation methods that are technically grounded and decision-relevant.

**中文**

我正在成为一种研究者：关注模型在分布变化下如何“不均匀地失败”。我关心的是隐藏 subgroup failure 如何发生，为什么一些看似公平或复杂的策略会在 shift 下变脆弱，以及如何设计更有解释力、更贴近真实决策风险的评估方法。

## Grounding Notes / 资料说明

**English**

This profile is grounded in `grounding/thesis.pdf`, `grounding/cv.pdf`, `grounding/proposal_decision_reliability.pdf`, and the existing project notes.

**中文**

本 profile 基于 `grounding/thesis.pdf`、`grounding/cv.pdf`、`grounding/proposal_decision_reliability.pdf` 和现有项目笔记整理。
