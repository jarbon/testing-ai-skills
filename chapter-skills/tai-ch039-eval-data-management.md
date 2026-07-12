---
name: tai-ch039-eval-data-management
description: 'Apply chapter 39 of Testing AI, Eval Data Management, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to eval data management.'
---

# Eval Data Management

Skill name: `tai-ch039-eval-data-management`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

If prompts, datasets, rubrics, labels, judges, and model versions are not versioned, the
evaluation cannot be trusted.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Eval data management is the discipline of keeping evaluation artifacts traceable. It sounds
boring until a team cannot explain why last month's score and this month's score are different.
For example, a quality score can change because the model improved, the judge changed, the
rubric changed, the sample changed, or labels were updated. Without versioning, those causes
blur together.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert teams treat evals like experiments and production telemetry at the same time. They keep
immutable run records, separate raw data from derived labels, document schema changes, and make
comparisons only between compatible runs.
