---
name: tai-ch063-ai-generated-code-that-looks-right-but-is-wrong
description: 'Apply chapter 63 of Testing AI, AI-Generated Code That Looks Right but Is Wrong, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai-generated code that looks right but is wrong.'
---

# AI-Generated Code That Looks Right but Is Wrong

Skill name: `tai-ch063-ai-generated-code-that-looks-right-but-is-wrong`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI-generated code often fails in a dangerous way: it looks clean, compiles, and still implements
the wrong behavior.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The most common AI-generated code issue is not messy syntax. It is plausible code that solves a
nearby problem instead of the actual problem. The names look right. The structure looks
familiar. The bug hides in the assumptions. For example, an AI coding assistant may implement a
discount rule for total cart value, but the product requirement says the discount applies only
to eligible items. The code passes simple tests and fails real billing behavior.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Use property-based tests, metamorphic tests, boundary matrices, and requirement-to-test
traceability. AI-generated code should be judged by behavioral evidence, not by whether it looks
idiomatic.
