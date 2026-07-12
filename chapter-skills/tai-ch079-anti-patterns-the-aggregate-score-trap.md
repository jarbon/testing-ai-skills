---
name: tai-ch079-anti-patterns-the-aggregate-score-trap
description: 'Apply chapter 79 of Testing AI, Anti-Patterns: The Aggregate Score Trap, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: the aggregate score trap.'
---

# Anti-Patterns: The Aggregate Score Trap

Skill name: `tai-ch079-anti-patterns-the-aggregate-score-trap`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Overall quality can improve while important users, languages, tasks, or risk categories get
worse.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Aggregate scores are useful for summaries, but they are dangerous when they hide slices. An AI
system can look better overall and still regress for a critical group. For example, a model
upgrade may improve common English support questions while making Spanish account recovery
worse. The average score rises while a real product risk grows.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Define slice thresholds before the run. Use confidence intervals per slice, risk-weighted
reporting, and minimum quality bars for groups where failure has high cost.
