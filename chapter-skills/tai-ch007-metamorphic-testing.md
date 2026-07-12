---
name: tai-ch007-metamorphic-testing
description: 'Apply chapter 7 of Testing AI, Metamorphic Testing, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to metamorphic testing.'
---

# Metamorphic Testing

Skill name: `tai-ch007-metamorphic-testing`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When there is no single correct answer, builders can change the input and check whether
important relationships still hold.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Metamorphic testing checks relationships between outputs instead of requiring one exact answer.
It is especially useful when there are many acceptable outputs but some properties must remain
stable. For example, rewriting a user question should not change the underlying refund policy.
Translating a prompt should not remove a safety constraint.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert metamorphic suites define relation types explicitly: invariance, monotonicity, symmetry,
subset consistency, ranking stability, or conservation of key facts. Each relation should have a
clear oracle for what must remain true after transformation.
