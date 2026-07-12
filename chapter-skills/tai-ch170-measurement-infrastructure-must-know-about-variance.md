---
name: tai-ch170-measurement-infrastructure-must-know-about-variance
description: 'Apply chapter 170 of Testing AI, Measurement Infrastructure Must Know About Variance, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to measurement infrastructure must know about variance.'
---

# Measurement Infrastructure Must Know About Variance

Skill name: `tai-ch170-measurement-infrastructure-must-know-about-variance`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

If the measurement system ignores its own variance, it will eventually promote lucky noise as
product improvement.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

When you measure a non-deterministic system over and over, you do not get the same answer. You
get a distribution of answers. The quality metric is a function of the sample size, sample
composition, rater behavior, system behavior, data freshness, timing, and measurement pipeline.
It is not simply "the average," and it is definitely not the best number you happened to see
this week.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, treat the measurement system as part of the experiment. Model rater
variance, sample variance, judge variance, temporal drift, repeated testing, and multiple-
comparison effects. Use predeclared stopping rules, fresh holdouts, bootstrap intervals,
sequential testing discipline, and run logs that preserve every attempt. A release metric should
answer whether the system improved beyond the known noise of both the product and the measuring
instrument.
