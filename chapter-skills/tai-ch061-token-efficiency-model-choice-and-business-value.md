---
name: tai-ch061-token-efficiency-model-choice-and-business-value
description: 'Apply chapter 61 of Testing AI, Token Efficiency, Model Choice, and Business Value, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to token efficiency, model choice, and business value.'
---

# Token Efficiency, Model Choice, and Business Value

Skill name: `tai-ch061-token-efficiency-model-choice-and-business-value`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The best AI system is not the biggest model or the cheapest model. It is the model path that
creates the most trustworthy value for the risk, cost, latency, and business constraints.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Cost and token-budget testing asks whether a workflow can afford to behave the way it behaves.
Model-choice testing asks a different question: which model path should do the work at all?

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, build an efficient frontier for AI quality. Compare marginal quality
gain against marginal cost, latency, privacy exposure, security risk, regional availability, and
continuity risk. Track cost per successful outcome, not cost per request. Maintain fallback
models, provider substitution tests, cached-path tests, and region-aware deployment checks so
the business can keep operating when a model, vendor, region, or policy changes.
