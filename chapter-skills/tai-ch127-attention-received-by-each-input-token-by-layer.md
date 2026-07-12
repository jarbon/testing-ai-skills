---
name: tai-ch127-attention-received-by-each-input-token-by-layer
description: 'Apply chapter 127 of Testing AI, Attention Received by Each Input Token by Layer, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to attention received by each input token by layer.'
---

# Attention Received by Each Input Token by Layer

Skill name: `tai-ch127-attention-received-by-each-input-token-by-layer`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Attention received by token and layer helps Confidence Engineers notice whether constraints,
negations, citations, or safety terms were ignored.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Instead of asking where one token looked, this view asks which input tokens received attention
across layers. Some tokens become central. Others are ignored.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to measure attention received by categories of tokens: constraints,
negations, tool outputs, citations, user identity, dates, amounts, and safety policy terms.
Report regressions by slice, not only by average attention.
