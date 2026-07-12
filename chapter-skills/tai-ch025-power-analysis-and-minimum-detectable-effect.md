---
name: tai-ch025-power-analysis-and-minimum-detectable-effect
description: 'Apply chapter 25 of Testing AI, Power Analysis and Minimum Detectable Effect, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to power analysis and minimum detectable effect.'
---

# Power Analysis and Minimum Detectable Effect

Skill name: `tai-ch025-power-analysis-and-minimum-detectable-effect`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Before asking whether a change won, builders should decide what size of win would actually
matter.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Power analysis asks whether your evaluation has enough data to detect the effect you care about.
Minimum detectable effect asks how large a change must be before the test is likely to notice
it. For example, 30 samples might detect a huge quality drop, but it probably will not reliably
detect a tiny 0.1-point improvement. That is not a failure of math. It is a mismatch between
sample size and decision.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert teams distinguish statistical power from business value. High power helps detect a chosen
effect, but the minimum meaningful effect should come from product risk, user impact, cost, and
operational tradeoffs.
