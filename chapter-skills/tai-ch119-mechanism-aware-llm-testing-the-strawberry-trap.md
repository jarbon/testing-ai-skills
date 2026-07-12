---
name: tai-ch119-mechanism-aware-llm-testing-the-strawberry-trap
description: 'Apply chapter 119 of Testing AI, Mechanism-Aware LLM Testing: The Strawberry Trap, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to mechanism-aware llm testing: the strawberry trap.'
---

# Mechanism-Aware LLM Testing: The Strawberry Trap

Skill name: `tai-ch119-mechanism-aware-llm-testing-the-strawberry-trap`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The famous "how many r's are in strawberry?" question is a useful lesson, but a poor standalone
test.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The question "how many r's are in strawberry?" became famous because many LLMs answered it
incorrectly for a long time. It is tempting to treat that as proof that the model is dumb. The
better lesson is more practical: the test exposes a mismatch between how humans see text and how
many models process text.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to separate capability from mechanism fit. LLMs are powerful sequence models,
but not every task should be solved inside the model's token prediction path. The more exact the
task, the more the product should route to deterministic components, retrieval, calculators,
parsers, validators, or constrained decoding.
