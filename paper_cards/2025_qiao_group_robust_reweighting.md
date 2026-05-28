# Paper Card - Group-Robust Sample Reweighting

Title: Group-robust Sample Reweighting for Subpopulation Shifts via Influence Functions
Year: 2025
Venue: ICLR 2025 Poster
Link: https://openreview.net/forum?id=aQj9Ifxrl6
Authors: Rui Qiao, Zhaoxuan Wu, Jingtan Wang, Pang Wei Koh, Bryan Kian Hsiang Low
Code / Project page: https://github.com/qiaoruiyt/GSR
Research line: Fairness, Subgroup Error, and Evaluation; Distribution Shift and Model Reliability
Keywords: subpopulation shift, group robustness, influence functions, sample reweighting, group labels
Relevance score: 3

## Problem

The paper studies uneven model performance across subpopulations when group proportions shift during deployment. Existing robust methods often need a non-trivial amount of high-quality group labels.

中文判断:

这个问题很现实: 我的人脸年龄估计数据也可能缺完整 subgroup labels。

## Method

The paper proposes Group-robust Sample Reweighting. It uses group-labeled data as a target set to optimize weights for group-unlabeled data. The model first learns representations from unlabeled-group data, then retrains its last layer on influence-function-reweighted data.

Important technical details:

- Uses group-labeled data efficiently
- Reweights group-unlabeled data
- Uses influence functions
- Retrains the last layer

中文判断:

这是一个 correction-oriented 方法, 可以和 SHIFT 的 diagnostic 思路互补。

## Data

The OpenReview summary reports evaluation on subpopulation shifts. Exact datasets and metrics should be extracted from the full paper.

Data shift, subgroup, or authenticity setting:

The central setting is subpopulation shift and group robustness.

中文判断:

需要深读 full paper, 看它用的是哪些 benchmark, 是否能迁移到 facial age estimation。

## Evaluation

The reported evaluation compares robustness to subpopulation shifts and states that GSR outperforms prior approaches that require the same or more group labels.

What comparison or baseline is important?

Group-DRO-style methods, group-balanced validation methods, and other sample reweighting or data-selection methods are likely important comparisons.

Does the evaluation match the real research question?

Mostly yes. It evaluates performance under subpopulation shift and group-label scarcity.

中文判断:

如果我做 proposal, 可以把它作为 "现有 correction 方法", 然后指出 temporal/historical shift 还没有被充分处理。

## Main Finding

GSR improves robustness to subpopulation shifts while using group labels more efficiently than previous approaches.

Why is the result meaningful?

It suggests that group robustness can be improved without requiring complete group annotation.

中文判断:

这对我的背景很实用, 因为历史数据通常标注不完美。

## Limitation

The method still needs some group-labeled data. It may not fully address temporal shift, label shift, or subgroup definitions that change over historical periods.

Could this limitation become a research question?

Yes. A natural research question is how to combine group-efficient reweighting with temporal drift diagnosis.

中文判断:

这篇可以作为方法备选, 但不是最终 PhD topic 本身。

## My Use

Can I cite this paper in my PhD proposal?

Yes, especially when discussing subgroup robustness under limited group labels.

Can it support my research direction?

Yes. It supports the fairness and subgroup error part of the direction.

Which paragraph of my proposal could use it?

The paragraph explaining that group labels are expensive and that robust correction methods need to work with incomplete subgroup information.

Possible interview answer:

"One challenge in subgroup fairness diagnostics is that complete group labels are often unavailable. Recent work on group-robust reweighting uses small group-labeled target sets to improve robustness, which could be adapted to historical visual datasets."

Connection to my thesis on facial age estimation under historical domain shift:

It could inspire a correction step after diagnosing which age or demographic subgroup suffers the largest error under historical shift.

## Follow-up

- [ ] Read full paper
- [ ] Check datasets and exact baselines
- [ ] Compare with thesis balancing or reweighting results
- [ ] Add to fairness subgroup topic map
- [ ] Consider as a method component in proposal
