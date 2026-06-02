# AGENTS.md

## Project Role

This repository is my academic research radar. It supports PhD preparation by turning papers, thesis observations, and proposal ideas into a coherent research identity.

## Execution Workflow

Every substantial research task should follow this order:

1. **Read `grounding/`**
   - Grounding files define who I am as a researcher.
   - They contain my thesis background, research profile, and proposal direction.
   - Use them before interpreting papers or generating new research questions.

2. **Load relevant `skills/`**
   - Skills define how analysis should be performed.
   - Use only the skills relevant to the task.
   - Apply skill rubrics explicitly when screening papers, connecting papers to my thesis, generating research questions, or writing weekly synthesis.

3. **Generate the requested output**
   - Outputs should be concise, bilingual when requested, technically grounded, and written in first-person research note voice.
   - Avoid direct reader-address wording in research notes.

## Grounding Files

The core grounding files are:

- `grounding/research_profile.md`
- `grounding/thesis.pdf`
- `grounding/proposal_decision_reliability.pdf`
- `grounding/proposal_distribution_shift.pdf`
- `grounding/cv.pdf`

The grounding files define:

- my academic background;
- my master thesis;
- my empirical findings;
- my current research motivation;
- my preferred and avoided research directions.

## Skills

The core skills are:

- `skills/paper_screening.md`
- `skills/thesis_connection.md`
- `skills/research_question_generation.md`
- `skills/weekly_synthesis.md`
- `skills/deep_paper_reading.md`


## Deep Paper Reading Workflow

Daily notes are for screening and direction tracking. Deep paper cards are for strategically important papers only.

Use `skills/deep_paper_reading.md` only when a paper is marked as:

- `Recommended for paper card`;
- `proposal anchor`;
- `method reference with high strategic value`;
- `warning / limitation paper`.

Do not create deep paper cards for every daily paper. Create at most two deep paper cards per week.

Every deep paper card must:

- identify the paper's research function in the chain `Diagnosis -> Explanation -> Intervention -> Monitoring -> Evaluation`;
- separate `Verified from paper`, `My interpretation`, and `Needs full-paper verification`;
- include a section titled `How I Can Use This in My Proposal`;
- connect directly to my thesis observations;
- keep first-person research note voice in thesis-connection sections;
- avoid second-person wording.

Topic maps should be updated only when a deep paper card produces a stable concept, not whenever a new paper is added.

## Daily Note Generation Rules

Daily note generation must always:

1. Ground on my thesis findings:
   - aggregate metrics can hide subgroup failure;
   - balancing sometimes worsened elderly-group performance;
   - cascaded conditional models were fragile under shift;
   - simpler regression models generalized better.

2. Apply `skills/paper_screening.md`:
   - screen papers for relevance, method value, citation value, feasibility, and long-term fit.

3. Apply `skills/thesis_connection.md`:
   - explicitly connect each selected paper to my thesis observations.

4. Apply `skills/research_question_generation.md`:
   - generate specific, testable, technically plausible research questions.

5. Add `Research function` for each selected paper:
   - Diagnosis / Explanation / Intervention / Monitoring / Evaluation.

6. Recommend at most one deep paper card at the end of each daily note. Do not automatically create the deep card.

7. Maintain first-person research note voice:
   - write as my own reflective research notes;
   - use "my thesis" and "my research direction";
   - avoid direct reader-address phrasing.

## Weekly Synthesis Rules

Weekly synthesis must apply `skills/weekly_synthesis.md` and should:

- identify repeated themes;
- detect conceptual shifts;
- identify contradictions;
- rank strongest research opportunities;
- update topic maps when needed;
- reflect on how my research identity is evolving;
- include one short `Proposal Seed` that can be reused in PhD proposal drafting.

## Content Boundaries

Prefer:

- distribution shift;
- subgroup reliability;
- fairness degradation under shift;
- representation stability;
- uncertainty-aware monitoring;
- decision-relevant model evaluation;
- data-centric diagnosis of hidden subgroup failure.

Avoid:

- generic AI hype;
- product/startup news;
- architecture novelty without evaluation insight;
- systems-heavy infrastructure work;
- vague fairness or governance discussion without technical grounding.
