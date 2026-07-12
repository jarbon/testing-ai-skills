---
name: tai-ch022-chi-squared-tests-for-categorical-ai-quality
description: 'Apply chapter 22 of Testing AI, Chi-Squared Tests for Categorical AI Quality, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to chi-squared tests for categorical ai quality.'
---

# Chi-Squared Tests for Categorical AI Quality

Skill name: `tai-ch022-chi-squared-tests-for-categorical-ai-quality`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Chi-squared tests help compare counts, categories, and failure distributions when quality is not
a smooth 0-10 score.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Use chi-squared tests when the outcome is categorical: pass or fail, safe or unsafe, grounded or
hallucinated, answer or refuse, correct tool or wrong tool, satisfied or escalated.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Check whether the test assumptions fit the data. Chi-squared tests expect independent
observations and enough expected count in each cell. If expected counts are tiny, use Fisher's
exact test or combine categories carefully before testing. Fisher's exact test does not require
knowing what changed inside a black-box AI system. It only needs the observed counts and a valid
comparison design. The hard part is not opening the model; the hard part is making sure the
cases, categories, and sampling process are meaningful.
