---
name: tai-ch141-testing-personalization-lock-in-and-portability
description: 'Apply chapter 141 of Testing AI, Testing Personalization Lock-In and Portability, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing personalization lock-in and portability.'
---

# Testing Personalization Lock-In and Portability

Skill name: `tai-ch141-testing-personalization-lock-in-and-portability`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Personalization becomes infrastructure when users cannot leave without losing the AI that
understands them.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The more an AI system learns about a user, the more valuable it becomes. That value can also
become a trap. If a user's memory, preferences, task history, and workflow conventions cannot
move, then personalization becomes switching cost.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is that portability testing needs export completeness, schema stability, import
fidelity, behavior-parity evals, privacy filtering, consent preservation, and rollback plans.
Measure degradation after migration rather than assuming exported data means exported quality.
