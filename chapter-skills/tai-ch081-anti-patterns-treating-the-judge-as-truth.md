---
name: tai-ch081-anti-patterns-treating-the-judge-as-truth
description: 'Apply chapter 81 of Testing AI, Anti-Patterns: Treating the Judge as Truth, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: treating the judge as truth.'
---

# Anti-Patterns: Treating the Judge as Truth

Skill name: `tai-ch081-anti-patterns-treating-the-judge-as-truth`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

LLM judges are useful evaluators, not objective measurement devices handed down from the sky.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

LLM-as-a-judge can scale evaluation dramatically. It can score open-ended outputs, apply
rubrics, explain failures, and triage large datasets. But an LLM judge is still a model. It has
bias, variance, prompt sensitivity, position effects, calibration issues, and blind spots.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, track judge-human agreement, judge variance, position bias, rubric
sensitivity, model-version drift, and category-specific reliability. Treat judge output as
evidence with uncertainty.
