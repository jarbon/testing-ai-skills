---
name: tai-ch131-concept-signal-profiles
description: 'Apply chapter 131 of Testing AI, Concept Signal Profiles, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to concept signal profiles.'
---

# Concept Signal Profiles

Skill name: `tai-ch131-concept-signal-profiles`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Residual, attention, and MLP signals answer different testing questions about what the model
carries, attends to, and transforms.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A concept signal profile can combine several views: residual stream signal, attention signal,
and MLP signal. These are not interchangeable.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Use multiple internal signals and external behavior together. The strongest evidence is
convergent: output behavior, trace evidence, attention, activation profiles, and expert review
point in the same direction.
