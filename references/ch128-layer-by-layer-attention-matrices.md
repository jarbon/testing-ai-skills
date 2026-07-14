# Section 128: Layer-by-Layer Attention Matrices

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** attention, layer by layer attention matrices  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Attention matrices expose token-to-token routing patterns that can be compared across layers,
prompts, and model versions.

## Actions

- Preserve the unaggregated heads because an average can hide a specialized head or disagreement among heads.
- Save a few representative layers for known-good and known-bad cases.
- Define runnable checks that exercise attention and layer by layer attention matrices.

## Evidence to Produce

- Preserve the unaggregated heads because an average can hide a specialized head or disagreement among heads.
- Save a few representative layers for known-good and known-bad cases.
- Preserve the inputs, versions, configurations, raw outcomes, and results for attention, layer by layer attention matrices needed to reproduce work on Layer-by-Layer Attention Matrices.
- Report results for attention, layer by layer attention matrices by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview


A self-attention matrix shows token-to-token attention for a selected layer and head or an aggregation of heads. Rows represent query-token positions and columns represent attended key-token positions. Early layers often show stronger local relationships, including token identity, punctuation, morphology, positional information, and short-range dependencies. Middle and later layers may show broader contextual relationships or increasing focus on task-relevant tokens. These are tendencies to test, not fixed architectural stages.



Each square in the representative-snapshot figure is a head-averaged token-to-token attention matrix for one layer. The labels are actual token positions selected from the prompt, not abstract concepts. All panels use the same scale. The second figure retains more token positions across four layers, making the causal lower-triangular structure and the bright start-token column easier to see. Those patterns are not bugs in the chart; they are part of this model's internal mechanics.

The testing value comes from comparison: which reproducible relationships change across prompts, model versions, fine-tunes, and known failure cases? Preserve the unaggregated heads because an average can hide a specialized head or disagreement among heads. Similar outputs may arise from different attention patterns, and similar attention patterns may produce different outputs. Attention is comparative evidence, not an explanation of model reasoning.


## Why This Matters


Matrices are especially useful for teaching and debugging. They show that attention is structured, layered, and dynamic, not a single magical highlight over the prompt.

For release work, do not show a single matrix and declare victory. Save a few representative layers for known-good and known-bad cases. Then compare those still frames when a prompt template, model, fine-tune, retrieval format, or safety policy changes.


## High-Stakes Examples


## Expert Notes


Attention matrices should be treated as diagnostic artifacts. Pair them with ablation, activation patching, counterfactual prompts, and output evals before drawing causal conclusions.
