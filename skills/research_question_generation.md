# Skill: Research Question Generation / 研究问题生成

## Purpose / 目的

**English**

This skill defines how to generate strong PhD-level research questions from daily papers and weekly synthesis. A good research question should be specific, testable, technically plausible, aligned with trustworthy ML, and naturally extend my thesis.

**中文**

这个 skill 用来生成 PhD-level research questions。好的研究问题应该具体、可测试、技术上可行、和 trustworthy ML 对齐，并且自然延伸我的 thesis。

## Required Criteria / 必须满足

A research question must be:

- specific;
- testable;
- technically plausible;
- grounded in my thesis observations;
- connected to distribution shift, subgroup reliability, or decision-relevant evaluation;
- narrow enough to design experiments around.

中文:

研究问题不能太大、太虚或太泛。它必须能落到数据、模型、指标或实验设计上。

## Avoid / 避免

Avoid:

- vague fairness questions;
- generic AI questions;
- broad governance questions without technical method;
- overly ambitious systems projects;
- architecture novelty without diagnostic value;
- questions that cannot be tested with realistic data.

## Templates / 模板

### 1. Distribution Shift Diagnostics

English:

How does [type of distribution shift] affect [model behaviour] for [specific subgroup] in [task/domain]?

Example:

How does historical domain shift affect elderly-group MAE and residual variance in facial age estimation?

中文:

[某种 distribution shift] 如何影响 [具体 subgroup] 在 [任务] 中的 [模型行为]？

### 2. Subgroup Reliability Monitoring

English:

Can [monitoring signal] detect early degradation in [subgroup] before aggregate metrics change?

Example:

Can residual skew and calibration error detect elderly-group degradation before global MAE increases?

中文:

[某个 monitoring signal] 能否在整体指标变化前，提前发现 [subgroup] 的可靠性下降？

### 3. Decision-Relevant Evaluation

English:

When does [evaluation metric] become insufficient for [decision context], and what subgroup-aware metric better captures risk?

Example:

When is aggregate MAE insufficient for age-based historical demographic analysis, and can worst-group MAE better capture reliability risk?

中文:

在什么决策场景下，[某个整体指标] 不够？什么 subgroup-aware metric 更能反映风险？

### 4. Representation Stability Analysis

English:

How does [domain shift] change latent representations, and are these changes associated with [subgroup-specific error pattern]?

Example:

How does historical portrait shift alter facial age representations, and is representation drift associated with elderly-group underestimation?

中文:

[某种 domain shift] 如何改变 latent representation？这种变化是否和 [某个 subgroup 错误模式] 有关？

## Output Format / 输出格式

For each generated question:

- Research question:
- Why it matters:
- Possible data:
- Possible method:
- Evaluation metric:
- Thesis connection:
- Risk or limitation:

