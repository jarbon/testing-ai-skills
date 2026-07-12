---
name: tai-ch128-layer-by-layer-attention-matrices
description: 'Apply chapter 128 of Testing AI, Layer-by-Layer Attention Matrices, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to layer-by-layer attention matrices.'
---

# Layer-by-Layer Attention Matrices

Skill name: `tai-ch128-layer-by-layer-attention-matrices`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Attention matrices make the model less mysterious by showing how focus changes from early layers
to later layers.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A self-attention matrix shows token-to-token attention for a selected layer and head or an
aggregation of heads. Early layers may focus on local syntax or nearby tokens. Later layers may
show broader task structure.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Attention matrices should be treated as diagnostic artifacts. Pair them with ablation,
activation patching, counterfactual prompts, and output evals before drawing causal conclusions.
