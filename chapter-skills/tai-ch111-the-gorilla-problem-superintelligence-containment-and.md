---
name: tai-ch111-the-gorilla-problem-superintelligence-containment-and
description: 'Apply chapter 111 of Testing AI, The Gorilla Problem: Superintelligence, Containment, and Understanding, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to the gorilla problem: superintelligence, containment, and understanding.'
---

# The Gorilla Problem: Superintelligence, Containment, and Understanding

Skill name: `tai-ch111-the-gorilla-problem-superintelligence-containment-and`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

If a system becomes much smarter than us, containment and inspection cannot be the whole plan.
The gorilla cannot audit the zookeeper.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

This chapter is a future-facing warning about capability gaps. Testing assumes the evaluator can
understand enough of the system to judge the evidence. That assumption becomes weaker as the
system becomes more capable than the people, tools, institutions, and tests around it.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat the gorilla problem as an evaluator-capability mismatch. It is not a mathematical proof
that all future AI is uncontrollable. It is a warning that control plans relying on ordinary
inspection, ordinary persuasion resistance, ordinary sandboxes, or ordinary governance may fail
when capability gaps become large enough.
