# ai-research-radar

Codex role: my academic research scout.

The job is not to maximize quantity.

The job is to identify:

- technically meaningful papers
- emerging research directions
- conceptual shifts in trustworthy AI

Prioritize depth over breadth.

Always connect findings to:

1. historical domain shift
2. subgroup robustness
3. fairness diagnostics
4. decision-relevant model evaluation

Avoid generic AI hype.
Avoid startup/product news.
Focus strictly on academic relevance.

This project is a Markdown research radar for PhD preparation.

Its goal is not to collect many AI papers. Its goal is to turn recent research signals into useful PhD material: research questions, proposal directions, interview answers, and supervisor discussion notes.

核心目标不是追热点, 而是每天稳定回答:

1. What new research directions are worth watching?
2. Which papers are related to my research interests?
3. Can these materials become PhD topics, research questions, interview answers, or proposal evidence?
4. How do they connect to my thesis on facial age estimation under historical domain shift?

## Research Anchor

My current background is:

- Facial age estimation
- Historical domain shift
- Computer vision evaluation
- Dataset shift and model reliability

Default writing style:

- English first, simple academic tone
- Chinese notes for judgment, positioning, and personal fit
- No hype
- Focus on research value, method, data, evaluation, and limitations

## Grounding Files

Some grounding PDFs are kept locally and are not committed because they contain personal information. Codex can use them during local runs, but GitHub only stores distilled Markdown summaries.

## Core Research Lines

Use this priority order to keep the radar focused:

1. Subgroup-aware reliability diagnosis under distribution shift
2. Distribution Shift and Model Reliability
3. Fairness, Subgroup Error, and Evaluation
4. Trustworthy AI and Model Monitoring
5. AI Governance, Decision Support, and AIGC Authenticity only when directly linked to reliability under shift

Primary research identity:

> My current research direction is subgroup-aware reliability diagnosis under distribution shift.

The main question is:

> How do historical, temporal, or domain shifts produce subgroup-specific reliability degradation, especially when aggregate metrics hide elderly-group or hidden-subgroup failures?

Conceptual chain:

```text
Diagnosis -> Explanation -> Intervention -> Monitoring -> Evaluation
```

Core thesis observations to preserve:

1. Aggregate MAE can hide subgroup failure.
2. Elderly-group degradation appeared under historical shift.
3. Balancing may worsen vulnerable subgroup reliability.
4. Cascaded conditional models can be fragile under shift.
5. Simpler regression models may generalize more robustly.

Related priority keywords:

1. heterogeneous performance drift, subgroup-specific degradation, hidden stratification
2. temporal distribution shift, domain shift, dataset shift, OOD generalization
3. subgroup robustness, fairness degradation under deployment shift, worst-group reliability
4. representation instability under shift, subgroup-aware monitoring, uncertainty and calibration
5. decision-relevant evaluation, data-centric failure diagnosis, model auditing
6. detector reliability under generator/domain shift, only when AIGC authenticity directly supports the main reliability question

## Daily Workflow

Create one note in `daily_notes/YYYY-MM-DD.md`.

The daily note should include:

1. exactly 3 recent academic papers;
2. a `Research function` label for each paper: Diagnosis / Explanation / Intervention / Monitoring / Evaluation;
3. one focused emerging trend that synthesizes the three papers;
4. two specific, testable research questions;
5. one short personal reflection on how the readings reshape my PhD research identity;
6. at most one `Recommended deep paper card`.

Daily selection rules:

- Prefer materials from the last 7 days.
- If there are not enough strong matches, expand to the last 30 days and state this clearly.
- Do not include a paper only because it is popular.
- Every selected paper should directly support subgroup reliability under shift.
- Do not force 3 technical discussions unless they genuinely add value.
- Never invent details. If data, metrics, or venue are unclear, write `Unknown` and add a follow-up action.

Reject unless directly connected to subgroup reliability under shift:

- generic LLM papers;
- prompt engineering;
- broad AI governance;
- product news;
- systems-heavy infrastructure;
- generic multimodal generation;
- AIGC authenticity without detector reliability under shift.

## Weekly Workflow

Create one report in `weekly_reports/week_XX_summary.md`.

The weekly report should act as a research direction converger. It should not only summarize papers.

The weekly report should include:

1. what became clearer this week;
2. conceptual-chain coverage across Diagnosis, Explanation, Intervention, Monitoring, and Evaluation;
3. the strongest papers and whether they are proposal anchors, method references, background citations, or warning papers;
4. tensions or open problems;
5. the top 3 research directions ranked by thesis fit, feasibility, proposal strength, and risk;
6. one reusable `Proposal Seed`;
7. a deep-reading queue with at most two cards per week.

## Paper Card and Deep Reading Workflow

Daily notes are for screening and direction tracking.

Deep paper cards are for strategically important papers only. Use `skills/deep_paper_reading.md` when a paper is marked as:

- Recommended for paper card;
- proposal anchor;
- method reference with high strategic value;
- warning / limitation paper.

Do not create deep paper cards for every daily paper. Create at most two deep paper cards per week.

Every deep paper card must:

- identify its research function in the conceptual chain;
- clearly separate `Verified from paper`, `My interpretation`, and `Needs full-paper verification`;
- include `How I Can Use This in My Proposal`;
- connect to thesis observations;
- avoid generic praise and overclaiming.

## Paper Card Workflow

When a paper is important enough to reuse in a proposal or interview, create a paper card in `paper_cards/`.

File naming rule:

```text
year_firstauthor_shorttitle.md
```

Example:

```text
2024_smith_subgroup_shift_monitoring.md
```

Each paper card should answer:

- What problem does the paper study?
- What method does it use?
- What data and evaluation are used?
- What is the main finding?
- What is missing or weak?
- How can I use this in my PhD proposal?
- Which research line and research function does it support?

## Project Structure

```text
ai-research-radar/
├── README.md
├── sources/
│   ├── paper_sources.md
│   ├── lab_sources.md
│   └── phd_position_sources.md
├── daily_notes/
│   ├── 2026-05-28.md
│   └── daily_note_template.md
├── paper_cards/
│   └── paper_template.md
├── topic_maps/
│   ├── distribution_shift.md
│   ├── trustworthy_ai.md
│   ├── fairness_subgroup_error.md
│   ├── ai_governance.md
│   └── multimodal_authenticity.md
└── weekly_reports/
    ├── week_01_summary.md
    └── weekly_report_template.md
```

## Daily Prompt

Use this prompt when asking Codex to maintain the project:

```text
Run my daily academic research radar.

Repository:
ai-research-radar

Execution protocol:
1. Read AGENTS.md, grounding/research_profile.md, and grounding/proposal_distribution_shift.md.
2. Load skills/paper_screening.md, skills/thesis_connection.md, and skills/research_question_generation.md.
3. Generate today’s note as daily_notes/YYYY-MM-DD.md.

Primary research identity:
My current research direction is subgroup-aware reliability diagnosis under distribution shift.

Conceptual chain:
Diagnosis -> Explanation -> Intervention -> Monitoring -> Evaluation

Select exactly 3 recent academic papers.

For each paper, include:
- English Summary: problem, method, evaluation, findings
- 中文解释
- Research function: Diagnosis / Explanation / Intervention / Monitoring / Evaluation
- Screening Score using the /25 rubric from skills/paper_screening.md
- Connection to My Thesis, explicitly connecting to at least two thesis observations
- Usefulness: proposal anchor / method reference / background only / reject after reading

Then generate:
- one focused Emerging Trend in English and Chinese
- two specific, testable Research Questions in English and Chinese
- one Personal Reflection in English and Chinese
- Recommended deep paper card: at most one paper, with a one-sentence reason

Deep reading rule:
Do not create a full paper card automatically.
The actual deep paper card should be created manually using skills/deep_paper_reading.md.

Important:
Do not force 3 technical discussions unless they genuinely add value.
Depth and fit are more important than breadth.
Use first-person research note voice.
Do not invent missing details.
```

## Weekly Prompt

Use this prompt when asking Codex to synthesize a week:

```text
Run weekly academic synthesis.

Repository:
ai-research-radar

Read:
- AGENTS.md
- grounding/research_profile.md
- grounding/proposal_distribution_shift.md
- all daily_notes from this week
- all new paper_cards from this week
- skills/weekly_synthesis.md
- skills/research_question_generation.md

Output:
weekly_reports/week_XX_summary.md

Main purpose:
Do not only summarize papers. Use this report to refine my PhD research direction and produce one reusable Proposal Seed.

Required sections:
1. What became clearer this week?
2. Conceptual chain coverage
3. Strongest papers
4. Tensions or open problems
5. Top 3 research directions
6. Proposal Seed
7. Deep reading queue
8. Next week plan

Proposal Seed limits:
English: 120-180 words.
中文理解: 150-250 字.

Deep reading limit:
Create at most two deep paper cards per week.
```

## Quality Bar

A good daily note should be short, specific, and usable later.

Minimum acceptance criteria:

- exactly 3 strongly aligned papers with real links
- one synthesized emerging trend, not three forced discussion items
- two concrete research questions with method, possible data, evaluation metric, and risk
- clear relation to my thesis background and at least two thesis observations per selected paper
- `Research function` label for each paper
- at most one recommended deep paper card
- at least one follow-up action, including source correction when needed

A good weekly report should help decide where to invest attention next week and should produce one reusable Proposal Seed.
