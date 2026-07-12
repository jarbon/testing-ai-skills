---
name: tai-ch048-regression-testing-when-outputs-keep-changing
description: 'Apply chapter 48 of Testing AI, Regression Testing When Outputs Keep Changing, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to regression testing when outputs keep changing.'
---

# Regression Testing When Outputs Keep Changing

Skill name: `tai-ch048-regression-testing-when-outputs-keep-changing`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When exact outputs drift, regression testing has to protect invariants, not fossilize
yesterday's wording.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Regression testing for non-deterministic systems is not about freezing every output. It is about
detecting when behavior gets worse on the properties that matter. For example, a summary can
change wording without regressing, but it regresses if it drops a key risk, invents a fact, or
becomes less usable for the target user.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to keep separate baselines for examples, rubrics, labels, model versions, and
judge versions. A regression can come from the product, the evaluator, the dataset, or the
policy changing underneath the test.
