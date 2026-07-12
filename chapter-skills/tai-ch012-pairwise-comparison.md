---
name: tai-ch012-pairwise-comparison
description: 'Apply chapter 12 of Testing AI, Pairwise Comparison, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to pairwise comparison.'
---

# Pairwise Comparison

Skill name: `tai-ch012-pairwise-comparison`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When absolute scoring is hard, asking which output is better can produce useful evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Pairwise comparison asks which of two outputs is better. It is often easier and more reliable
than asking for an absolute score, especially when quality is nuanced. For example, reviewers
may argue whether an answer is a 7 or 8, but agree that version B is clearer, safer, and more
faithful than version A.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Blind the version labels, randomize side order, allow ties, and analyze win rate by category.
Pairwise wins do not replace absolute gates because the better of two bad outputs can still be
unacceptable.
