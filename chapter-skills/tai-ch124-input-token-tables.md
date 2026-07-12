---
name: tai-ch124-input-token-tables
description: 'Apply chapter 124 of Testing AI, Input Token Tables, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to input token tables.'
---

# Input Token Tables

Skill name: `tai-ch124-input-token-tables`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Before builders inspect attention or activations, they need to see exactly what the model
received as tokens.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Tokenization is the first transformation in a language model. A user types words, punctuation,
code, or symbols, but the model receives token ids at positions. That translation can create
surprising testing failures.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Token tables should include tokenizer version, position, token id, byte span, original text
span, and any preprocessing. This matters for multilingual text, code, identifiers, numbers,
names, and pasted documents.
