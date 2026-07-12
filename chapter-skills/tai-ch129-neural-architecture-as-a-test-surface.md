---
name: tai-ch129-neural-architecture-as-a-test-surface
description: 'Apply chapter 129 of Testing AI, Neural Architecture as a Test Surface, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to neural architecture as a test surface.'
---

# Neural Architecture as a Test Surface

Skill name: `tai-ch129-neural-architecture-as-a-test-surface`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A transformer is a chain of internal transformations, and each transformation can become a
source of observability evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A transformer model can be viewed as layered computation: tokenization, embeddings, repeated
decoder layers, attention blocks, MLP blocks, residual stream updates, normalization, logits,
and sampling.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, map each architecture block to observability: tokenizer, prompt
assembler, embeddings, layer activations, attention, MLPs, logits, sampler, tool call, parser,
and safety layer. Each block needs versioning and failure labels.
