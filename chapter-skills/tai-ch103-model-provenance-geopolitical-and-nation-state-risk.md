---
name: tai-ch103-model-provenance-geopolitical-and-nation-state-risk
description: 'Apply chapter 103 of Testing AI, Model Provenance, Geopolitical, and Nation-State Risk, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to model provenance, geopolitical, and nation-state risk.'
---

# Model Provenance, Geopolitical, and Nation-State Risk

Skill name: `tai-ch103-model-provenance-geopolitical-and-nation-state-risk`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Where a model is built, hosted, governed, and tuned can matter for security, privacy,
continuity, and bias.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI teams often compare models by price, latency, and quality. Security-minded teams also need to
ask where the model came from, who controls it, where data is processed, what laws apply, how
updates happen, and whether the model may contain intentional or unintentional political,
cultural, or strategic bias.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Evaluate model provenance, hosting jurisdiction, data-retention policy, auditability, update
cadence, incident history, export controls, continuity plans, and bias on region-sensitive eval
sets. The goal is evidence-based risk classification, not vague fear.
