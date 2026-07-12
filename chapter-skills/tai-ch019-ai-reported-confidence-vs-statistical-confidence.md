---
name: tai-ch019-ai-reported-confidence-vs-statistical-confidence
description: 'Apply chapter 19 of Testing AI, AI-Reported Confidence vs. Statistical Confidence, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai-reported confidence vs. statistical confidence.'
---

# AI-Reported Confidence vs. Statistical Confidence

Skill name: `tai-ch019-ai-reported-confidence-vs-statistical-confidence`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

An LLM saying it is confident is not the same as a confidence interval calculated from sample
data.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI-reported confidence and statistical confidence are different things. An LLM's confidence is a
self-assessment of a single judgment. Statistical confidence comes from sample data and observed
variation. For example, a judge may say it is highly confident that one answer deserves an 8.
That does not tell you the true average quality of the whole system.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert teams calibrate AI confidence. They check whether high-confidence judge decisions
actually agree with expert humans more often than low-confidence decisions. If not, the
confidence label is not useful for routing or release decisions.
