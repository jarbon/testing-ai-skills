---
name: tai-ch018-confidence-intervals-saying-about-like-a-professional
description: 'Apply chapter 18 of Testing AI, Confidence Intervals: Saying "About" Like a Professional, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to confidence intervals: saying "about" like a professional.'
---

# Confidence Intervals: Saying "About" Like a Professional

Skill name: `tai-ch018-confidence-intervals-saying-about-like-a-professional`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Confidence intervals help Confidence Engineers report estimates as ranges instead of pretending
sample results are exact truth.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A confidence interval is a way to say "about" with discipline. It reports an estimate as a
range, acknowledging that a sample is not the full truth. For example, saying pass rate is 92%
sounds exact. Saying the approximate 95% confidence interval is about 87% to 97% tells the team
how much uncertainty remains.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Choose interval methods that match the metric. A pass rate is a proportion and may use Wilson or
exact binomial intervals. An average score often uses a t-based or bootstrap interval,
especially when the score distribution is not normal.
