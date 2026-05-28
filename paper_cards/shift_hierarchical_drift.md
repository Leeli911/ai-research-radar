# Paper Card - SHIFT Hierarchical Performance Drift

Title: "Who experiences large model decay and why?" A Hierarchical Framework for Diagnosing Heterogeneous Performance Drift
Year: 2025
Venue: ICML 2025 / Proceedings of Machine Learning Research
Link: https://arxiv.org/abs/2506.00756
PMLR: https://proceedings.mlr.press/v267/singh25e.html
Authors: Harvineet Singh, Fan Xia, Alexej Gossmann, Andrew Chuang, Julian C. Hong, Jean Feng
Code / Project page: Unknown
Research line: Distribution Shift and Model Reliability; Fairness, Subgroup Error, and Evaluation
Keywords: performance drift, subgroup degradation, covariate shift, outcome shift, hierarchical testing, subgroup scanning, post-deployment monitoring
Relevance score: 3

## Problem

This paper studies a specific weakness in post-deployment model evaluation: model decay is usually reported as an average performance drop, but the actual harm may be concentrated in specific subgroups. The paper asks two linked questions:

1. Where does unacceptably large subgroup-specific performance decay occur?
2. How can that decay be explained by covariate or outcome shifts?

The key contribution is that the paper does not stop at "the model got worse." It formalizes the more useful diagnostic question: "Which subgroup got worse, and what kind of shift explains the degradation?"

中文判断:

这篇论文最重要的地方是把 performance drift 从平均指标拆成 subgroup-level 问题。它不是只看整体 accuracy 或 loss 有没有下降, 而是找出哪一类样本受到最大影响。这和我的 thesis 中 aggregate MAE 掩盖 elderly-group failure 的现象非常接近。

## How the Paper Formalizes Subgroup-Specific Degradation

The paper defines performance drift as the change in expected loss between a source domain and a target domain. Instead of only measuring the average change over the whole population, SHIFT searches over subgroups whose performance decay is large enough to be practically meaningful.

The formalization has three important parts:

1. **Source and target domains**: the same model is evaluated under two data distributions, such as training/development data versus deployment data, or one deployment context versus another.
2. **Loss-based performance decay**: degradation is measured through a loss function, so the framework is not tied to one metric.
3. **Subgroup-level thresholding**: domain experts define a minimum subgroup size and a minimum decay magnitude. This prevents the method from flagging tiny or practically irrelevant groups.

SHIFT then decomposes subgroup degradation into two broad mechanisms:

- **Covariate shift**: the input distribution changes.
- **Outcome shift**: the conditional relationship between inputs and outcomes changes.

The framework is hierarchical. First, it asks whether any subgroup has large decay due to aggregate covariate or outcome shift. If a problematic subgroup is found, the method searches for more detailed variable-subset-specific explanations.

中文解释:

这篇论文的 formalization 可以理解成三步:

第一步, 先定义两个 domain: 比如训练时期和部署时期, 或旧数据和新数据。

第二步, 用 loss 的变化衡量模型是否退化。这个 loss 可以是分类错误, 也可以被改成其他任务里的误差。

第三步, 不看整体平均 loss, 而是在 subgroup 上找“足够大、足够重要”的退化。这里需要提前设定两个阈值: subgroup 不能太小, performance drop 也不能太小。这样可以避免模型监控系统因为很小的波动而误报。

最关键的是, SHIFT 还会区分退化来自哪里: 是输入分布变了, 还是输入和标签之间的关系变了。这一点对 historical facial age estimation 很重要, 因为历史人像里的变化可能来自图像风格、年龄标注、数据采集方式、群体构成等多个来源。

## Method

SHIFT is a two-stage hierarchical hypothesis testing framework.

At the first stage, SHIFT asks a "Where?" question:

- Is there any subgroup with unacceptably large performance decay due to aggregate covariate shift?
- Is there any subgroup with unacceptably large performance decay due to aggregate outcome shift?

If the first stage finds a subgroup of concern, the second stage asks a "How?" question:

- Can the subgroup decay be explained by more detailed shifts involving specific variables or variable subsets?

The paper uses subgroup scanning to search for affected groups and hierarchical inference to organize the diagnosis. The output is intended to be interpretable: a practitioner should see not only that performance drift exists, but also which subgroup is affected and which variables may explain the drift.

中文解释:

SHIFT 的方法可以用 “Where + How” 来记。

Where: 哪个 subgroup 发生了严重退化?

How: 这个 subgroup 的退化能不能用某些变量的变化来解释?

例如, 如果一个模型从 hospital A 用到 hospital B, 整体准确率只下降一点, 但老年患者 subgroup 的错误率大幅上升, SHIFT 会先把这个 subgroup 找出来。然后它会继续看, 这个问题是不是和某些变量的分布变化有关, 比如病情严重程度、治疗流程、测量方式等。

迁移到我的研究里, 这个逻辑可以变成: 先找出 historical shift 下哪个 age subgroup 或 gender-conditioned subgroup 的 age estimation error 变差, 再解释这种变差是不是来自图像质量、拍摄年代、年龄分布、性别条件模型结构或标注偏差。

## Data

The paper validates SHIFT with simulations and real-world case studies. The reported task setting is mostly classification-style performance drift, where performance is measured with a loss such as 0-1 misclassification loss. The paper emphasizes real-world deployment contexts where models are transferred across domains or used over time.

Data shift, subgroup, or authenticity setting:

The central setting is post-deployment distribution shift with heterogeneous subgroup effects. This is conceptually close to historical domain shift, although the original paper is not about facial age estimation or historical portrait data.

中文判断:

这篇论文的数据场景不是人脸年龄估计, 但它的问题结构高度相似: 模型被放到另一个 domain 后, 某些 subgroup 的性能退化被平均指标掩盖。我的任务是 regression 而不是 classification, 所以如果借用 SHIFT, 需要把 loss 从 0-1 error 换成 MAE、absolute error、calibration error 或 worst-group MAE。

## Evaluation

The evaluation asks whether SHIFT can:

- detect subgroups with practically meaningful performance decay,
- separate covariate-shift-driven and outcome-shift-driven degradation,
- identify variable-level or variable-subset explanations,
- support targeted corrective actions.

This evaluation design is useful because it treats monitoring as diagnosis, not just alerting. The goal is not only to say "performance changed," but to explain where and why the change happened.

中文判断:

这点对我的 thesis 很有启发。我的结果里, aggregate MAE 可能看起来不错, 但 elderly-group error 可能很差。一个好的 evaluation 不应该只报告整体 MAE, 还应该问:

- 哪个 age group 的 MAE 退化最大?
- 这种退化是否只发生在某个 historical period?
- 是否和 gender-conditional cascade 有关?
- 是否和图像质量或训练数据平衡策略有关?

## How This Explains My Thesis Observation

My thesis observation:

> Good aggregate MAE could hide elderly-group failure.

SHIFT offers a direct conceptual explanation for this. Aggregate MAE averages errors across all samples, so a large error increase in a smaller elderly subgroup can be diluted by stable or improved performance in younger or middle-aged groups. In SHIFT terms, the average performance drift may look modest while a subgroup has unacceptably large decay.

This paper also helps reinterpret the dataset balancing result:

> Dataset balancing sometimes worsened elderly-group performance.

SHIFT suggests that an intervention should target the affected subgroup and the specific shift mechanism. Naive balancing may change the training distribution without addressing the actual covariate or outcome shift responsible for elderly-group degradation. If the elderly-group failure is caused by historical image quality, annotation noise, or a changed relationship between visual age cues and labels, simple balancing may not fix the right mechanism.

中文解释:

我的 thesis 里最关键的问题是: 整体 MAE 不能说明每个 subgroup 都可靠。比如年轻组和中年组样本更多, 或者模型在这些组上表现稳定, 它们会把 elderly group 的严重错误“平均掉”。所以 aggregate MAE 好看, 不代表 elderly group 安全。

SHIFT 给了一个更系统的说法: 我需要找的是 subgroup-specific performance decay。也就是说, 不仅要问整体误差是否变大, 还要问 elderly group 的误差是否超过了一个有实际意义的阈值。

它也帮助解释为什么 dataset balancing 可能失败。平衡数据只是改变样本比例, 但如果 elderly group 的问题来自历史照片质量、标注偏差、年龄特征在不同年代的视觉变化, 或 cascaded gender-conditional model 的结构脆弱性, 那么简单 balancing 可能没有解决真正原因, 甚至可能让模型学到更不稳定的表示。

## Adaptation to Historical Facial Age Estimation

SHIFT could be adapted to historical facial age estimation by redefining its source-target setup and performance loss.

Possible source-target definitions:

- Earlier historical period as source, later historical period as target.
- Modern benchmark data as source, historical portrait data as target.
- One archival collection as source, another collection as target.
- Balanced training data as source, naturally imbalanced deployment-like data as target.

Possible subgroup definitions:

- Age group, especially elderly versus non-elderly.
- Gender-conditioned groups if reliable labels exist.
- Historical period groups.
- Image-quality groups such as low contrast, blur, restoration artifacts, or pose variation.
- Intersectional groups such as elderly female portraits in older archival periods.

Possible loss functions:

- MAE by subgroup.
- Worst-group MAE.
- Error tail probability, such as the proportion of samples with absolute error above a threshold.
- Calibration error for predicted age uncertainty if uncertainty estimates are available.
- Reliability volatility across historical periods.

Possible diagnostic workflow:

1. Fit or reuse a facial age estimation model.
2. Define source and target historical domains.
3. Compute subgroup-level performance drift using MAE or absolute error.
4. Use a SHIFT-like subgroup scan to detect whether any subgroup has practically large degradation.
5. Test whether the degradation is better explained by image-quality variables, historical period, group composition, label noise, or model architecture.
6. Compare targeted correction against naive dataset balancing.

中文解释:

如果把 SHIFT 迁移到 historical facial age estimation, 我会先定义两个 domain。比如 1900-1950 年的人像作为 source, 1950-2000 年的人像作为 target, 或者现代数据作为 source、历史人像作为 target。

然后我需要定义 subgroup。最直接的是 age group, 尤其是 elderly group。进一步可以看 gender-conditioned group, historical period, image quality, 以及它们的组合。

接着把分类任务里的 0-1 loss 换成年龄估计任务里的 MAE 或 absolute error。这样就可以问: 哪个 subgroup 的 MAE 在 historical shift 下变差最大?

最后再分析原因。比如 elderly group 的失败到底是因为样本少, 还是因为老照片质量差, 还是因为年龄标签噪声更大, 或者是 cascaded gender-conditional model 在 shift 下不稳定。

## Limitations in Historical Portrait Datasets

Adapting SHIFT to historical portrait datasets would introduce several limitations.

1. **Noisy or missing subgroup labels**

Historical portraits may not have reliable gender, ethnicity, exact age, or acquisition-period metadata. Subgroup scanning becomes less reliable when subgroup definitions are noisy.

2. **Uncertain age labels**

Facial age labels in historical datasets may be estimated, rounded, inferred from archival metadata, or inconsistent across sources. This creates outcome noise, which can be mistaken for model degradation.

3. **Confounding between age, period, and image quality**

Older subjects may be overrepresented in certain historical periods or lower-quality images. The observed elderly-group failure may combine demographic difficulty, temporal shift, and image degradation.

4. **Small subgroup sample sizes**

Elderly groups or intersectional groups may be small. SHIFT requires a minimum subgroup size threshold, so rare but important groups may be difficult to test statistically.

5. **Regression-specific adaptation**

The original paper mostly presents classification-style loss. Historical facial age estimation is a regression task, so the framework needs careful adaptation to MAE, calibration, or tail-error metrics.

6. **Ambiguous corrective actions**

Even if a subgroup is diagnosed as degraded, the right correction may be unclear. Reweighting, recalibration, augmentation, model simplification, or subgroup-specific models could have different effects.

中文解释:

历史人像数据会让 SHIFT 的迁移变难。

第一, subgroup label 可能不可靠。比如 gender 或年龄段可能来自人工推断, 不一定准确。

第二, 年龄 label 本身可能有噪声。有些历史照片的真实年龄可能不是精确记录, 而是估计出来的。

第三, age、历史时期和图像质量可能混在一起。elderly group 错误大, 可能不是因为年龄本身难, 而是因为 elderly 样本更多来自低质量时期或特定档案来源。

第四, elderly group 或交叉 subgroup 样本可能太少, 导致统计诊断不稳定。

第五, 我的任务是 regression, 而 SHIFT 原论文更多用分类 loss, 所以需要重新设计 loss 和显著性阈值。

第六, 诊断出问题不等于知道怎么修。我的 thesis 已经说明 naive balancing 可能反而伤害 elderly group, 所以后续 correction 必须非常谨慎。

## Main Finding

The main value of this paper is that it turns performance drift into a structured diagnostic problem. It separates three questions that are often mixed together:

1. Did performance change?
2. Which subgroup was harmed?
3. What type of shift may explain the harm?

For my research, this distinction is more useful than average robustness claims. It gives a concrete framework for arguing that historical domain shift should be evaluated through subgroup-specific degradation, not aggregate MAE alone.

中文判断:

这篇论文可以作为我的 PhD proposal 核心参考之一。它帮我把 thesis 里的经验观察转成研究问题:

平均 MAE 为什么不够?
哪个 subgroup 退化最严重?
退化来自什么 shift mechanism?
什么 correction 比 naive balancing 更可靠?

## My Use

Can I cite this paper in my PhD proposal?

Yes. It directly supports the argument that average performance drift is insufficient and that subgroup-specific degradation needs explicit diagnostic methods.

Can it support my research direction?

Yes. It is highly aligned with a direction on subgroup-aware reliability diagnostics under historical domain shift.

Which paragraph of my proposal could use it?

The paragraph that motivates a shift from aggregate evaluation to subgroup-aware reliability monitoring. It can support a claim such as:

> Recent work on heterogeneous performance drift shows that average model decay can hide severe subgroup-specific degradation. My thesis on facial age estimation under historical domain shift provides a computer vision case where this issue becomes visible through elderly-group failure hidden by aggregate MAE.

Possible interview answer:

My thesis showed that aggregate MAE can hide elderly-group failure under historical domain shift. This paper gives a formal framework for that observation: model decay should be diagnosed at the subgroup level, and the diagnosis should distinguish whether degradation is driven by covariate shift, outcome shift, or more specific variable-level changes. I see this as a bridge from my thesis to a broader PhD project on subgroup-aware reliability under distribution shift.

Connection to my thesis on facial age estimation under historical domain shift:

SHIFT provides the clearest method-level bridge so far. It can help transform my thesis observation into a general research agenda: diagnose which subgroups lose reliability under historical shift, explain the mechanism of degradation, and compare targeted correction against naive balancing or fragile cascaded models.

## Follow-up

- [ ] Read the full PMLR version and extract the exact real-world case studies.
- [ ] Map SHIFT's covariate/outcome shift decomposition to facial age estimation variables.
- [ ] Define regression-compatible performance decay tests using MAE and tail error.
- [ ] Identify which metadata are available in my historical portrait dataset.
- [ ] Compare SHIFT-style diagnosis with simple subgroup MAE tables from my thesis.
- [ ] Draft a proposal paragraph on subgroup-aware performance drift in historical visual recognition.

