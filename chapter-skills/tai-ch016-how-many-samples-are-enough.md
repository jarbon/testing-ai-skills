---
name: tai-ch016-how-many-samples-are-enough
description: 'Apply chapter 16 of Testing AI, How Many Samples Are Enough?, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to how many samples are enough?.'
---

# How Many Samples Are Enough?

Skill name: `tai-ch016-how-many-samples-are-enough`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Sample size is a risk decision. The higher the stakes and the rarer the failure, the more
evidence builders need.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Enough samples means enough evidence for the decision and risk. Low-risk changes can use smaller
samples. High-impact systems need larger samples, deeper review, and targeted tests for rare but
severe failures. For example, a creative rewrite tool and a billing agent should not use the
same sample-size bar. The cost of being wrong is different.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, sample size depends on desired precision, expected failure rate, confidence
level, and minimum detectable effect. Rare failures need targeted hunting because random
sampling can require impractically large counts to observe very low-frequency events.
