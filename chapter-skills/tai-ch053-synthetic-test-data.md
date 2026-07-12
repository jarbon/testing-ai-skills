---
name: tai-ch053-synthetic-test-data
description: 'Apply chapter 53 of Testing AI, Synthetic Test Data, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to synthetic test data.'
---

# Synthetic Test Data

Skill name: `tai-ch053-synthetic-test-data`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Synthetic data can expand coverage, but it can also manufacture a false picture of reality.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Synthetic test data is useful when real examples are rare, sensitive, expensive, or not yet
available. It can create edge cases, adversarial prompts, privacy-safe HIPAA-like examples,
counterfactual bias cases, and regression scenarios.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Track synthetic-data provenance, generator model, prompt, seed, intended risk, reviewer
approval, similarity to real data, and downstream failure discovery. Treat synthetic data as a
hypothesis generator, not a substitute for measured production behavior.
