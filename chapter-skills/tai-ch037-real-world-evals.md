---
name: tai-ch037-real-world-evals
description: 'Apply chapter 37 of Testing AI, Real-World Evals, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to real-world evals.'
---

# Real-World Evals

Skill name: `tai-ch037-real-world-evals`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Public evals are useful because they make measurement concrete. They are also limited because
every eval measures a particular shape of task.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Real-world evals are not magic leaderboards. They are worked examples of measurement design.
Each one defines a task shape, a set of cases, a scoring rule, and an aggregation method. Once
you see that pattern, the famous evals become less mysterious and more useful.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat the evaluation itself as a system under test. Version the cases, rubric, model, judge,
data, and release decision so future teams can reproduce the result.
