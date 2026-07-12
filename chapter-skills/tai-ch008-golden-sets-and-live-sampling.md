---
name: tai-ch008-golden-sets-and-live-sampling
description: 'Apply chapter 8 of Testing AI, Golden Sets and Live Sampling, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to golden sets and live sampling.'
---

# Golden Sets and Live Sampling

Skill name: `tai-ch008-golden-sets-and-live-sampling`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Stable regression examples and fresh real-world samples solve different problems. Mature AI
testing needs both.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Golden sets and live sampling answer different questions. Golden sets preserve known important
cases. Live sampling discovers what is happening now. For example, a golden set might contain
past policy failures, while live sampling captures this week's new user questions and emerging
abuse patterns.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Golden sets should be versioned, deduplicated, labeled by risk, and periodically refreshed. Live
samples should preserve privacy and represent the current traffic mix instead of only the cases
that are easiest to review.
