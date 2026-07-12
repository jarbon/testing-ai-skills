---
name: tai-ch135-testing-deep-personalization
description: 'Apply chapter 135 of Testing AI, Testing Deep Personalization, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing deep personalization.'
---

# Testing Deep Personalization

Skill name: `tai-ch135-testing-deep-personalization`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Personalized AI will not have one correct answer. It will have behavior that must be right for
this user, in this context, under these constraints.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Deep personalization changes the testing problem because the system no longer behaves the same
way for everyone. It adapts to memory, preferences, history, goals, risk level, device,
language, accessibility needs, and sometimes emotional state. For example, a health coach,
coding assistant, sales assistant, or learning tutor may give different advice to two users with
the same prompt because their histories and constraints are different. That can be valuable, but
it creates a much larger quality surface.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, deep personalization testing should combine counterfactual profile testing, privacy
audits, memory provenance, user-segment sampling, preference-reversal tests, drift monitoring,
consent checks, and calibration of when the system should ask instead of infer.
