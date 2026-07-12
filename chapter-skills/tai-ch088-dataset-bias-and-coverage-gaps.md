---
name: tai-ch088-dataset-bias-and-coverage-gaps
description: 'Apply chapter 88 of Testing AI, Dataset Bias and Coverage Gaps, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to dataset bias and coverage gaps.'
---

# Dataset Bias and Coverage Gaps

Skill name: `tai-ch088-dataset-bias-and-coverage-gaps`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A clean-looking evaluation can still be wrong if the sample misses the people, languages, risks,
and workflows that matter.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Dataset bias happens when the evaluation sample does not represent the real product problem.
Coverage gaps are the places the test data simply does not reach.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, maintain a coverage matrix with population share, risk weight, sample count, pass
rate, confidence interval, known exclusions, label quality, and production drift. Make omissions
explicit instead of letting them become hidden assumptions. A small but high-risk slice may
deserve more samples than its traffic share would suggest.
