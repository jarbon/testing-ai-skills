---
name: tai-ch070-halting-g-del-and-the-limits-of-testing-ai-generated-c
description: 'Apply chapter 70 of Testing AI, Halting, Gödel, and the Limits of Testing AI-Generated Code, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to halting, gödel, and the limits of testing ai-generated code.'
---

# Halting, Gödel, and the Limits of Testing AI-Generated Code

Skill name: `tai-ch070-halting-g-del-and-the-limits-of-testing-ai-generated-c`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Some limits are not tooling problems. They are built into computation, logic, and the difference
between proof and evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The halting problem and Gödel's incompleteness theorems are not daily testing techniques, and
they are not literal proofs about every product test you will run. They are useful limits and
analogies: reminders that perfect verification of rich systems has boundaries. For example, no
test suite can prove that every arbitrary AI-generated program will always terminate, always
behave safely, and always satisfy every future requirement in every environment.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Use formal verification where scope is narrow and specifications are stable, but pair it with
runtime guards, resource limits, trace monitoring, property-based tests, fuzzing, and production
feedback. Theory is a warning against overconfidence, not an excuse for vague testing. It
explains why validation must be layered.
