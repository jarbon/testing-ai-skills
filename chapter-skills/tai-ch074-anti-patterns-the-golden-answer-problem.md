---
name: tai-ch074-anti-patterns-the-golden-answer-problem
description: 'Apply chapter 74 of Testing AI, Anti-Patterns: The Golden Answer Problem, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: the golden answer problem.'
---

# Anti-Patterns: The Golden Answer Problem

Skill name: `tai-ch074-anti-patterns-the-golden-answer-problem`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Many AI tasks do not have one correct answer, and pretending they do creates bad evals.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Golden answers are powerful when there is a single ground truth. Arithmetic, schema validation,
and many deterministic workflows benefit from exact expected answers. But chat, search,
summarization, recommendations, code review, and agent behavior often have multiple good
answers. A single golden answer can turn evaluation into answer memorization.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Use multiple reference answers, required-fact extraction, rubric scoring, pairwise preference,
and human calibration. Treat exact-match accuracy as one tool, not the default metric for open-
ended tasks.
