---
name: tai-ch072-anti-patterns-percent-passed-is-not-quality
description: 'Apply chapter 72 of Testing AI, Anti-Patterns: Percent Passed Is Not Quality, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: percent passed is not quality.'
---

# Anti-Patterns: Percent Passed Is Not Quality

Skill name: `tai-ch072-anti-patterns-percent-passed-is-not-quality`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A 94% pass rate can be comforting, meaningless, or dangerous depending on what failed.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Percent passed is seductive because it looks like a quality metric. It is simple, dashboard-
friendly, and familiar to executives. But for AI systems, percent passed is often a weak
summary. It depends on which tests were selected, how failures were weighted, whether slices
were balanced, and whether a small number of severe failures were hidden inside a large number
of easy cases.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, pair pass rate with severity-adjusted score, blocker rate, confidence
interval, slice-level minimums, and dataset composition. Trend pass rate only when the test
population and scoring rules are comparable.
