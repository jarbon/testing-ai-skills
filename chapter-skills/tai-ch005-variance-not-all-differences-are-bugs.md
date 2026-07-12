---
name: tai-ch005-variance-not-all-differences-are-bugs
description: 'Apply chapter 5 of Testing AI, Variance: Not All Differences Are Bugs, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to variance: not all differences are bugs.'
---

# Variance: Not All Differences Are Bugs

Skill name: `tai-ch005-variance-not-all-differences-are-bugs`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Good testing distinguishes harmless variation from variation that changes facts, safety,
reliability, or user trust.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Variance is the spread of behavior across runs. In a non-deterministic system, some spread is
expected and even useful. The evaluator's job is to decide which differences preserve the user's
outcome and which differences change the truth, risk, action, or experience.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Report variance by dimension. Score variance, factual variance, latency variance, ranking
variance, policy variance, and action variance are not interchangeable. A single average can
hide the type of instability users will actually feel.
