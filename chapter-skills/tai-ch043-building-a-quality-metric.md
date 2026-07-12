---
name: tai-ch043-building-a-quality-metric
description: 'Apply chapter 43 of Testing AI, Building a Quality Metric, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to building a quality metric.'
---

# Building a Quality Metric

Skill name: `tai-ch043-building-a-quality-metric`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Every AI team needs at least one quality metric that turns messy behavior into release evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

At some point, a team has to turn many observations into a release decision. That usually means
creating at least one quality metric. The metric does not need to capture everything. It does
need to be explicit, repeatable, and useful enough to compare versions.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, separate metric design from release thresholds. Define sub-scores, weights,
hard blockers, slice reporting, confidence intervals, and minimum practical improvement before
the comparison. A good metric is not truth. It is an explicit decision instrument that can be
challenged, audited, and improved.
