---
name: tai-ch011-rare-failure-hunting
description: 'Apply chapter 11 of Testing AI, Rare Failure Hunting, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to rare failure hunting.'
---

# Rare Failure Hunting

Skill name: `tai-ch011-rare-failure-hunting`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Average quality can look excellent while rare catastrophic failures still make the system
unsafe.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Rare failures matter when severity is high. A system that behaves well 99% of the time can still
be unshippable if the remaining 1% includes privacy leaks, unsafe instructions, or irreversible
actions. For example, an AI agent that usually books the right trip but occasionally confirms
without approval has a rare-failure problem, not a small average-quality problem.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert rare-failure work treats zero observed failures carefully. If you test 100 cases and see
zero failures, you have evidence, not proof. The upper bound on the plausible failure rate may
still be too high for safety-critical behavior.
