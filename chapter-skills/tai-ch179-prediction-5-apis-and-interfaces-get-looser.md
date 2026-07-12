---
name: tai-ch179-prediction-5-apis-and-interfaces-get-looser
description: 'Apply chapter 179 of Testing AI, Prediction 5: APIs and Interfaces Get Looser, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to prediction 5: apis and interfaces get looser.'
---

# Prediction 5: APIs and Interfaces Get Looser

Skill name: `tai-ch179-prediction-5-apis-and-interfaces-get-looser`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI-native systems exchange intent, constraints, state, and tokens as much as fixed calls and
fixed screens.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Traditional APIs compress behavior into stable calls. That will remain important for high-
integrity systems, but more AI-native systems will exchange richer packets of intent, context,
constraints, examples, tool schemas, and tokens.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Loose interfaces do not mean loose quality. They require stronger contracts around intent,
constraints, permissions, provenance, generated artifacts, and validation before side effects
reach users.
