---
name: tai-ch118-how-modern-llms-work-a-block-diagram
description: 'Apply chapter 118 of Testing AI, How Modern LLMs Work: A Block Diagram, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to how modern llms work: a block diagram.'
---

# How Modern LLMs Work: A Block Diagram

Skill name: `tai-ch118-how-modern-llms-work-a-block-diagram`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A simple architecture map helps Confidence Engineers know where failures can enter the system.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

At a simplified level, an LLM receives text, converts it into tokens, maps tokens to embeddings,
processes those embeddings through transformer layers, produces logits for possible next tokens,
and samples or selects the next token. This repeats until the output is complete.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, attach observability to each block: inputs, versions, costs, latency,
confidence signals, and failure labels. Good LLM testing turns the architecture into measurable
checkpoints rather than treating the model as a single black box.
