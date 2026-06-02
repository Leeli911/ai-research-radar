# Skill: Deep Paper Reading / 深度论文阅读

## Purpose / 目的

**English**

This skill defines how to conduct deep reading for strategically important papers in my academic research radar. It is only used for papers marked as `Recommended for paper card`, `proposal anchor`, or `method reference with high strategic value`.

Daily notes are for screening and direction tracking. Deep paper cards are for converting a small number of anchor papers into reusable PhD research material.

**中文**

这个 skill 用来规定核心论文的深读方式。它只用于被标记为 `Recommended for paper card`、`proposal anchor` 或 `method reference with high strategic value` 的论文。

日报负责筛选和方向判断。深读 paper card 负责把少数关键论文转化成可以用于 proposal、面试和研究设计的材料。

## Research Direction / 当前主线

My current research direction is **subgroup-aware reliability diagnosis under distribution shift**.

The conceptual chain is:

```text
Diagnosis -> Explanation -> Intervention -> Monitoring -> Evaluation
```

Each deep paper card should identify which part of this chain the paper supports.

## Use Rules / 使用规则

- Create at most two deep paper cards per week.
- Do not create deep paper cards for every daily paper.
- Do not turn daily notes into long-form deep reading.
- Use deep reading for three paper types only:
  1. proposal anchor;
  2. method reference with high strategic value;
  3. warning / limitation paper.

## Evidence Labels / 证据标签

Every deep card must clearly separate:

- **Verified from paper:** details directly checked from the paper, official abstract, official proceedings page, or full PDF.
- **My interpretation:** my own research interpretation or transfer to my thesis setting.
- **Needs full-paper verification:** claims that require full PDF, figures, tables, appendix, or code inspection.

This evidence labeling is mandatory. It prevents the card from becoming a confident but weakly verified summary.

## Output Structure / 输出结构

# Deep Paper Card - Short Title

Title:
Authors:
Year / Venue:
Link:
Research function: Diagnosis / Explanation / Intervention / Monitoring / Evaluation
Usefulness: proposal anchor / method reference / warning or limitation paper
Evidence status:

## Part 1: Literature Overview

### 1. Full Citation

Format:
Author(s). (Year). Title. Venue / Journal. DOI or URL.

If DOI is unavailable, use arXiv / OpenReview / PMLR / conference URL.

### 2. Research Background

English:
What scientific problem or technical bottleneck does this paper address?

中文:
用清楚语言解释这篇论文为什么重要。

## Part 2: Core Logic

### 3. Core Hypothesis / Central Idea

- Verified from paper:
- My interpretation:
- Needs full-paper verification:

### 4. Research Pathway

Identify the research paradigm:

- theoretical proof
- algorithmic method
- empirical benchmark
- diagnostic framework
- causal analysis
- monitoring framework
- mixed method

Explain why this pathway fits the problem.

### 5. Methodological Details

#### Object / Data

- dataset name:
- sample size if available:
- source:
- domain:
- subgroup / temporal / shift attributes:

#### Tools / Models

- core algorithm:
- baseline models:
- experimental platform or software if stated:

#### Technical Workflow

Summarize the main experimental or analytical pipeline step by step.

## Part 3: Evidence and Findings

### 6. Core Findings

Separate:

- main finding:
- secondary finding:
- unexpected finding if any:

### 7. Key Evidence and Figure / Table Index

Extract key quantitative results when available.

Include:

- metric names;
- performance changes;
- subgroup gaps;
- calibration / drift / reliability indicators if available.

Figure / Table list:
For each important figure or table:

- Figure / Table number:
- what it shows:
- why it matters:

If the full paper or figures cannot be checked, explicitly write:

```text
Full figure/table verification needed.
```

## Part 4: Critical Evaluation and Research Connection

### 8. Contributions and Limitations

#### Contributions

- theoretical contribution:
- methodological contribution:
- empirical contribution:
- practical relevance:

#### Limitations

- assumptions:
- dataset limitations:
- evaluation weaknesses:
- transferability risks:
- unresolved questions:

Be critical, not promotional.

### 9. Connection to My Research

Connect directly to my research direction:

```text
subgroup-aware reliability diagnosis under distribution shift
```

Also connect to my thesis observations:

- aggregate MAE can hide subgroup failure;
- elderly-group degradation under historical shift;
- balancing may worsen vulnerable subgroup reliability;
- cascaded conditional models can be fragile;
- simpler regression models may generalize more robustly;
- hidden subgroup failure may exist beyond explicit age/gender groups.

### 10. How I Can Use This in My Proposal

This section is mandatory.

Include:

- proposal argument supported by the paper;
- possible proposal sentence;
- method or evaluation design I could adapt;
- warning about limitations or overclaiming.

### 11. Inspiration and Backward Tracing

#### Inspiration

Possible outputs:

- new research question;
- possible method to adapt;
- evaluation design;
- proposal paragraph idea.

#### Must-read References

Recommend 1-2 important references cited by this paper or directly upstream.

For each:

- why it matters;
- what role it plays in the paper's logic;
- whether the reference has been verified or still needs checking.

## Output Requirements / 输出要求

- Bilingual: English first, Chinese explanation after each major section.
- First-person research note voice when connecting to my own work.
- Avoid second-person wording.
- Avoid generic praise.
- Clearly separate verified evidence from interpretation.
- Clearly mark full-paper verification needs.
