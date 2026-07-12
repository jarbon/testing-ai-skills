---
name: tai-ch175-prediction-1-validation-becomes-the-compute-sink
description: 'Apply chapter 175 of Testing AI, Prediction 1: Validation Becomes the Compute Sink, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to prediction 1: validation becomes the compute sink.'
---

# Prediction 1: Validation Becomes the Compute Sink

Skill name: `tai-ch175-prediction-1-validation-becomes-the-compute-sink`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When generation becomes cheap, validation becomes the expensive part of engineering.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

When generation is cheap, teams generate more candidates. More candidates require more
filtering. More filtering requires more evals, judges, traces, simulations, canaries, safety
checks, and production monitoring.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat validation compute as product infrastructure. Budget it by risk, uncertainty, and business
value instead of letting every generated candidate receive the same shallow check.
