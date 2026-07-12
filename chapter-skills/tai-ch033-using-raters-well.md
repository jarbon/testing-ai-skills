---
name: tai-ch033-using-raters-well
description: 'Apply chapter 33 of Testing AI, Using Raters Well, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to using raters well.'
---

# Using Raters Well

Skill name: `tai-ch033-using-raters-well`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Human raters are not a checkbox. They are an evaluation instrument that needs selection,
calibration, workflow design, and quality control.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Raters help test non-deterministic systems when quality cannot be reduced to exact assertions.
They can judge usefulness, tone, relevance, safety, policy fit, and whether an answer actually
solves a user's problem. For example, an LLM judge may score a support answer as complete, while
an experienced support rater notices that it violates refund policy. A domain rater may also see
that a technically correct answer would confuse a real customer.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, treat raters as measurement instruments. Track inter-rater agreement, rater-specific
bias, calibration drift, fatigue effects, adjudication outcomes, and whether the rater
population matches the user population. If raters and users disagree systematically, the eval is
measuring the wrong audience.
