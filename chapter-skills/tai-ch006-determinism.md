---
name: tai-ch006-determinism
description: 'Apply chapter 6 of Testing AI, Determinism, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to determinism.'
---

# Determinism

Skill name: `tai-ch006-determinism`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Sometimes the right testing move is to turn down variation so the product, judge, or validation
system becomes easier to reason about.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Non-deterministic testing does not mean every system should be as random as possible. In many
products, variation is the point: a chatbot can phrase an answer naturally, a search engine can
adapt to freshness and context, and a coding agent can choose a different implementation path.
But there are also moments when you want less variation.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Temperature, top_p, and top_k all affect sampling from the model's next-token probability
distribution. They are usually applied after the model computes logits and before the next token
is sampled. In many implementations, temperature rescales logits, top_p truncates by cumulative
probability, and top_k truncates by rank. Different providers may apply these controls in
different orders or expose only some of them.
