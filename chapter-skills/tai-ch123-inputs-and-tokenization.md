---
name: tai-ch123-inputs-and-tokenization
description: 'Apply chapter 123 of Testing AI, Inputs and Tokenization, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to inputs and tokenization.'
---

# Inputs and Tokenization

Skill name: `tai-ch123-inputs-and-tokenization`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

White-box testing should begin with the evidence the model actually received, not with an
exciting interpretation of its neurons.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

White-box testing should begin with the evidence the model actually received, not with an
exciting interpretation of its neurons.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat the evaluation itself as a system under test. Version the cases, rubric, model, judge,
data, and release decision so future teams can reproduce the result.
