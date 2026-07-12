---
name: tai-ch071-anti-patterns-the-boolean-pass-fail-trap
description: 'Apply chapter 71 of Testing AI, Anti-Patterns: The Boolean Pass/Fail Trap, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: the boolean pass/fail trap.'
---

# Anti-Patterns: The Boolean Pass/Fail Trap

Skill name: `tai-ch071-anti-patterns-the-boolean-pass-fail-trap`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A single green or red result can hide the very uncertainty builders need to explain.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Boolean pass/fail is one of the oldest instincts in testing. It works well when the system is
deterministic, idempotent, the expected result is precise, and one run tells you the truth. AI
systems break that assumption. A chatbot, ranking model, agent, or generated-code assistant can
produce acceptable variation, marginal variation, and severe failure from similar inputs. Red or
green alone collapses that reality into a false certainty.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Keep boolean blockers for truly binary constraints, but report ordinary quality as a
distribution. Use severity weighting, confidence intervals, slice minimums, and repeated runs so
the release decision reflects observed behavior instead of one crisp label.
