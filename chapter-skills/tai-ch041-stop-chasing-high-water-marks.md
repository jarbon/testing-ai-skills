---
name: tai-ch041-stop-chasing-high-water-marks
description: 'Apply chapter 41 of Testing AI, Stop Chasing High-Water Marks, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to stop chasing high-water marks.'
---

# Stop Chasing High-Water Marks

Skill name: `tai-ch041-stop-chasing-high-water-marks`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

If you rerun a noisy evaluation enough times, variance will eventually hand you a beautiful
score. That does not make the system better.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Non-deterministic systems produce noisy measurements. If you keep rerunning the same evaluation
and report only the best result, you are not measuring quality. You are selecting a lucky high-
water mark. For example, a prompt may average 8.0 across repeated runs but occasionally score
8.6 by chance. Reporting the 8.6 as the truth is wrong and will mislead the team.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, treat repeated evaluation as a multiple-comparisons problem. Track every run,
predefine stopping rules, preserve holdout sets, and estimate performance from the full run
distribution rather than the maximum observed score.
