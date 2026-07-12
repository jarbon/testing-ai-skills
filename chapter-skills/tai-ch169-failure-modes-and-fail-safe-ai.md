---
name: tai-ch169-failure-modes-and-fail-safe-ai
description: 'Apply chapter 169 of Testing AI, Failure Modes and Fail-Safe AI, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to failure modes and fail-safe ai.'
---

# Failure Modes and Fail-Safe AI

Skill name: `tai-ch169-failure-modes-and-fail-safe-ai`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The safest AI systems are designed so likely failures become bounded, visible, reversible, and
boring instead of catastrophic.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Once you accept that AI always fails somewhere, the next question is how the system fails. Some
failures are annoying. Some are expensive. Some are legally risky. Some are physically
dangerous. Some quietly corrupt downstream decisions for months before anyone notices.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, combine AI evals with safety engineering practices such as hazard
analysis, fault-tree analysis, threat modeling, incident response, quality gates, and post-
release monitoring. Design tests around control points: abstention, escalation, permission
checks, rate limits, sandboxing, reversibility, auditability, and human override. A model score
is not enough if the system architecture lets one bad output cause unbounded harm.
