---
name: tai-ch020-comparing-versions-with-t-tests
description: 'Apply chapter 20 of Testing AI, Comparing Versions with t-tests, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to comparing versions with t-tests.'
---

# Comparing Versions with t-tests

Skill name: `tai-ch020-comparing-versions-with-t-tests`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A t-test can help Confidence Engineers decide whether a difference in average scores is likely
to be real or just sampling noise.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A t-test helps compare average scores between versions while accounting for variation and sample
size. It asks whether an observed average difference is larger than you would expect from noise
alone under the test assumptions. For example, if a new prompt scores 0.5 points higher on
average, a t-test helps decide whether that improvement is likely to be real enough to discuss
seriously.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, use paired tests when the same cases run through both versions. Pairing
reduces noise from case difficulty. Also inspect assumptions: outliers, non-normal differences,
multiple comparisons, and category-specific regressions can all make a tidy p-value misleading.
