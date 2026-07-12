---
name: tai-ch125-attention-diagnostics
description: 'Apply chapter 125 of Testing AI, Attention Diagnostics, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to attention diagnostics.'
---

# Attention Diagnostics

Skill name: `tai-ch125-attention-diagnostics`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Attention views can direct an investigation, but they are not transcripts of reasoning and they
do not prove causality.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Attention views can direct an investigation, but they are not transcripts of reasoning and they
do not prove causality.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat the evaluation itself as a system under test. Version the cases, rubric, model, judge,
data, and release decision so future teams can reproduce the result.
