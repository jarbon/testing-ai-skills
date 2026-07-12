---
name: tai-ch168-ai-always-fails
description: 'Apply chapter 168 of Testing AI, AI Always Fails, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai always fails.'
---

# AI Always Fails

Skill name: `tai-ch168-ai-always-fails`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The useful question is not whether AI will fail. It is where, how often, how badly, and whether
you already know which inputs are likely to break it.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI systems always fail somewhere. That is not cynicism. It is a practical testing assumption.
Language models hallucinate, retrievers miss documents, agents pick the wrong tool, classifiers
misread edge cases, generated code compiles while doing the wrong thing, and personalization
systems overfit to partial signals.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat failure discovery as a continuous measurement problem. Combine production trace mining,
synthetic edge-case generation, adversarial testing, human review, clustering, severity scoring,
and slice-level confidence intervals. The output should be a failure taxonomy with owners,
detection signals, regression cases, escalation rules, and release thresholds.
