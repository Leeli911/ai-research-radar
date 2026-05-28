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

Use these four lines to keep the radar focused:

1. Distribution Shift and Model Reliability
2. Fairness, Subgroup Error, and Evaluation
3. AI Governance and Decision Support
4. AIGC Authenticity and Multimodal Trust

Related priority keywords:

1. distribution shift, dataset shift, OOD generalization
2. subgroup robustness, fairness under distribution shift
3. trustworthy machine learning, uncertainty estimation, model monitoring, auditing
4. AI governance, decision-relevant evaluation
5. multimodal authenticity, AIGC detection, provenance detection
6. data-centric AI, representation robustness, evaluation infrastructure

## Daily Workflow

Create one note in `daily_notes/YYYY-MM-DD.md`.

The daily note should include:

1. 3 to 5 recent papers or preprints
2. 3 trending technical discussions from research platforms
3. 1 possible PhD research idea
4. 1 short paragraph connecting the material to my thesis background

Daily selection rules:

- Prefer materials from the last 7 days.
- If there are not enough strong matches, expand to the last 30 days and state this clearly.
- Do not include a paper only because it is popular.
- Every item should map to at least one core research line.
- Never invent details. If data, metrics, or venue are unclear, write `Unknown` and add a follow-up action.

## Weekly Workflow

Create one report in `weekly_reports/week_XX_summary.md`.

The weekly report should include:

1. The 5 most important papers of the week
2. 3 emerging research trends
3. 3 possible PhD proposal directions
4. How the directions fit my background
5. The most suitable direction for me and why
6. Directions that are too technical, risky, or weakly aligned

The weekly report should make a judgment. It should not only summarize.

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
- Can I cite it in my PhD proposal?
- Which research line does it support?

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
Please help me maintain a PhD research radar project.

My core research interests are:
1. trustworthy machine learning
2. distribution shift
3. fairness and subgroup error
4. AI governance and decision-relevant model evaluation
5. multimodal authenticity and AIGC detection
6. data-centric AI and model monitoring

Every day, collect and summarize:
1. 3 to 5 recent papers or preprints
2. 3 trending technical discussions from GitHub, arXiv, Hugging Face, Papers with Code, OpenReview, or research lab blogs
3. 1 possible PhD research idea inspired by the collected materials
4. 1 short paragraph explaining how these materials connect to my previous thesis on facial age estimation under historical domain shift

Please save the result as a markdown file in daily_notes/YYYY-MM-DD.md.
Use simple academic English.
Add short Chinese judgment notes where useful.
Avoid hype.
Focus on research value, method, dataset, evaluation, and limitations.
Do not invent missing details.
```

## Quality Bar

A good daily note should be short, specific, and usable later.

Minimum acceptance criteria:

- 3 to 5 papers with real links
- 3 clearly sourced technical discussions
- 1 concrete research idea with method, possible data, and risk
- Clear relation to my thesis background
- At least one follow-up action

A good weekly report should help decide where to invest attention next week.
