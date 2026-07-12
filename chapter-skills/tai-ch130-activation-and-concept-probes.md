---
name: tai-ch130-activation-and-concept-probes
description: 'Apply chapter 130 of Testing AI, Activation and Concept Probes, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to activation and concept probes.'
---

# Activation and Concept Probes

Skill name: `tai-ch130-activation-and-concept-probes`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Activation and feature probes are emerging comparison tools, not validated meters for meaning,
safety, or correctness.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Activation and feature probes are emerging comparison tools, not validated meters for meaning,
safety, or correctness.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat the evaluation itself as a system under test. Version the cases, rubric, model, judge,
data, and release decision so future teams can reproduce the result.
