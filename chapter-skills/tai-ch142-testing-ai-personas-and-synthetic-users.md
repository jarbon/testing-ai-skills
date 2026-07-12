---
name: tai-ch142-testing-ai-personas-and-synthetic-users
description: 'Apply chapter 142 of Testing AI, Testing AI Personas and Synthetic Users, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing ai personas and synthetic users.'
---

# Testing AI Personas and Synthetic Users

Skill name: `tai-ch142-testing-ai-personas-and-synthetic-users`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Synthetic users can expand coverage, but they are test instruments. They are not reality.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI personas and synthetic users are useful because they let teams explore more situations than a
human rater budget can cover. They can simulate new users, experts, confused users, angry users,
multilingual users, accessibility needs, privacy-sensitive users, enterprise admins, or
developers with specific workflows.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat personas as generators and probes, not judges of record. Track persona prompt, model,
seed, intended population, known limitations, calibration results, and which failures were
confirmed by human review or production traces. Synthetic users are excellent for finding
questions. They are dangerous when treated as answers.
