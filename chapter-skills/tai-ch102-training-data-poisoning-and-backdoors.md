---
name: tai-ch102-training-data-poisoning-and-backdoors
description: 'Apply chapter 102 of Testing AI, Training Data Poisoning and Backdoors, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to training data poisoning and backdoors.'
---

# Training Data Poisoning and Backdoors

Skill name: `tai-ch102-training-data-poisoning-and-backdoors`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Bad data can teach a model behavior that only appears when the trigger is right.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Training data poisoning happens when harmful, misleading, biased, low-quality, or deliberately
crafted examples enter a learning pipeline and change future behavior. The poison may enter
pretraining data, fine-tuning data, reinforcement-learning feedback, preference labels,
synthetic data, eval data, RAG documents, memory stores, tool descriptions, or production
feedback loops.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, use data provenance, anomaly detection, trigger sweeps, canary tokens,
source reputation, fine-tune review, RAG document quarantine, feedback-loop rate limits,
synthetic-data labeling, and adversarial evals. Backdoor testing should include negative
controls: similar inputs without the trigger should not fail, and trigger-like inputs in
harmless contexts should not create false alarms.
