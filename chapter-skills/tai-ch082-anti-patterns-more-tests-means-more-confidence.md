---
name: tai-ch082-anti-patterns-more-tests-means-more-confidence
description: 'Apply chapter 82 of Testing AI, Anti-Patterns: More Tests Means More Confidence, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: more tests means more confidence.'
---

# Anti-Patterns: More Tests Means More Confidence

Skill name: `tai-ch082-anti-patterns-more-tests-means-more-confidence`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A larger eval can still be weak if it is redundant, biased, synthetic in the same way, or
disconnected from risk.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

More tests often help, but count alone is not coverage. Ten thousand easy, repetitive cases can
provide less confidence than a smaller, well-designed suite. For AI systems, the value of an
eval depends on behavioral coverage, risk coverage, label quality, slice coverage, and
production relevance.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Measure marginal value of added cases. Prioritize cases that reduce uncertainty in high-risk
areas, increase slice coverage, expose boundaries, or represent production frequency.
