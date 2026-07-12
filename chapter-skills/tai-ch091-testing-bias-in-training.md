---
name: tai-ch091-testing-bias-in-training
description: 'Apply chapter 91 of Testing AI, Testing Bias in Training, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing bias in training.'
---

# Testing Bias in Training

Skill name: `tai-ch091-testing-bias-in-training`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Feature selection, weights, hyperparameters, and training runs can all encode bias even when the
data looks reasonable.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Training bias is not only about data. It also comes from the way engineers represent the world
to the model: features, weights, hyperparameters, reward functions, and model-selection
criteria. For example, a search feature that helps distinguish flower pages by average color may
improve one benchmark while enabling unwanted correlations with skin color, hair color,
clothing, or other sensitive visual signals elsewhere.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, bias testing should include feature attribution, slice analysis,
counterfactual examples, retraining-to-retraining variance, and drift reports. A model with the
same global metric can still be a different product for important subgroups.
