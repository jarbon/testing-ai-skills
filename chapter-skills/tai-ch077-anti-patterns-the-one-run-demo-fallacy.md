---
name: tai-ch077-anti-patterns-the-one-run-demo-fallacy
description: 'Apply chapter 77 of Testing AI, Anti-Patterns: The One-Run Demo Fallacy, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: the one-run demo fallacy.'
---

# Anti-Patterns: The One-Run Demo Fallacy

Skill name: `tai-ch077-anti-patterns-the-one-run-demo-fallacy`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A beautiful demo proves what the system can do once, not what it will do reliably.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

One-run demos are powerful. They make AI systems feel magical. They get you funding. They also
create false confidence. With non-deterministic systems, a single great output can be a lucky
sample. It does not show average quality, failure rate, tail risk, or behavior under real
traffic.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, separate capability demos, smoke tests, benchmark runs, and release
evals. A demo can inspire investment, but only repeated, sampled, versioned evidence should
support shipping.
