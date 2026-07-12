---
name: tai-ch177-prediction-3-products-become-dynamic-by-default
description: 'Apply chapter 177 of Testing AI, Prediction 3: Products Become Dynamic by Default, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to prediction 3: products become dynamic by default.'
---

# Prediction 3: Products Become Dynamic by Default

Skill name: `tai-ch177-prediction-3-products-become-dynamic-by-default`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The product under test becomes a distribution of generated experiences, not one stable screen.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Static products are easier to test because the same user sees the same thing. AI products will
be less like that.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Dynamic products need dynamic evidence: slice reporting, stateful traces, personalization
audits, accessibility checks, and release gates that measure generated behavior across contexts.
