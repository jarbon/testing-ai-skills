---
name: tai-ch026-multiple-comparisons-and-false-discoveries
description: 'Apply chapter 26 of Testing AI, Multiple Comparisons and False Discoveries, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to multiple comparisons and false discoveries.'
---

# Multiple Comparisons and False Discoveries

Skill name: `tai-ch026-multiple-comparisons-and-false-discoveries`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The more slices, variants, and metrics you inspect, the more likely one lucky result will look
real.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Multiple comparisons are a trap in AI evaluation. If you compare many prompts, many models, many
categories, and many metrics, some result will look impressive by chance.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Separate exploratory analysis, confirmatory analysis, and monitoring. Use holdout sets,
preregistered primary metrics, adjusted thresholds, or false-discovery-rate methods when many
comparisons are part of the process. When a dashboard contains dozens of segments, report how
many comparisons were inspected and which ones were planned before the run.
