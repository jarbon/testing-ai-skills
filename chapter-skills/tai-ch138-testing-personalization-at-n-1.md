---
name: tai-ch138-testing-personalization-at-n-1
description: 'Apply chapter 138 of Testing AI, Testing Personalization at N = 1, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing personalization at n = 1.'
---

# Testing Personalization at N = 1

Skill name: `tai-ch138-testing-personalization-at-n-1`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The most personalized experience has the smallest sample size. That makes quality harder, not
easier.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

In this section, N means the number of users being measured. N = 1 means one user. The product
is not being judged across a segment, cohort, or average population. It is being judged for one
specific person, with their history, preferences, context, and moment.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At N = 1, treat quality as a longitudinal case study supported by population statistics. Use
repeated scenarios, counterfactual memory edits, preference-reversal tests, and time-based drift
checks. Report uncertainty honestly: "this user profile performed well across these sampled
scenarios" is stronger than "the personalized system works."
