---
name: tai-ch075-anti-patterns-filing-every-bad-output-like-a-bug
description: 'Apply chapter 75 of Testing AI, Anti-Patterns: Filing Every Bad Output Like a Bug, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: filing every bad output like a bug.'
---

# Anti-Patterns: Filing Every Bad Output Like a Bug

Skill name: `tai-ch075-anti-patterns-filing-every-bad-output-like-a-bug`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

One bad AI output is usually evidence of a behavior pattern, not a single defect with a surgical
fix.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

In deterministic software, a bug report often points to a fixable defect. Click this button, see
this crash, patch this code path. AI failures are different. One bad output may be a sample from
a broader probability distribution. Fixing that one output can move the distribution and create
new failures somewhere else.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

AI issue tracking should include cluster id, slice, severity, sample count, confidence,
regression cases, mitigation hypothesis, and post-fix distribution movement. The fix is not done
when one example disappears.
