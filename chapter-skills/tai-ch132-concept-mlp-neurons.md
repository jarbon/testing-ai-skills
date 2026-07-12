---
name: tai-ch132-concept-mlp-neurons
description: 'Apply chapter 132 of Testing AI, Concept MLP Neurons, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to concept mlp neurons.'
---

# Concept MLP Neurons

Skill name: `tai-ch132-concept-mlp-neurons`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Candidate concept neurons can be useful probes for ideas like privacy, security, uncertainty, or
hallucination, but they are not magic meaning cells.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Some individual MLP neurons or units may fire strongly around recurring ideas such as testing,
security, privacy, uncertainty, toxicity, hallucination, medical risk, or code execution. These
can become candidate concept probes.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Validate concept neurons with counterfactual datasets, ablations, activation patching, and slice
labels. Do not promote a neuron to a production signal until it predicts something useful on
held-out cases.
