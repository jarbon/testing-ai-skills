---
name: tai-ch036-evals-and-benchmarks
description: 'Apply chapter 36 of Testing AI, Evals and Benchmarks, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to evals and benchmarks.'
---

# Evals and Benchmarks

Skill name: `tai-ch036-evals-and-benchmarks`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Benchmarks are useful signals, but many evals are narrower, noisier, or less well-defined than
their leaderboard numbers suggest.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

An eval is a structured measurement of model or system behavior. It defines the task, the input,
the allowed context, the expected output or judgment method, and the scoring rule. A useful eval
does not merely ask, "Did the model say something plausible?" It says what kind of behavior is
being measured, how the answer will be judged, and what decision the result should support.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, audit benchmarks before trusting them. Track task validity, label
quality, contamination risk, environment drift, oracle ambiguity, metric fit, and inter-rater
agreement. A leaderboard score is an input, not a release decision.
