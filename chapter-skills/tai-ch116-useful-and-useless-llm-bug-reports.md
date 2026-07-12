---
name: tai-ch116-useful-and-useless-llm-bug-reports
description: 'Apply chapter 116 of Testing AI, Useful and Useless LLM Bug Reports, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to useful and useless llm bug reports.'
---

# Useful and Useless LLM Bug Reports

Skill name: `tai-ch116-useful-and-useless-llm-bug-reports`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A single bad answer is a clue. It is rarely a complete LLM bug report.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Traditional bug reports often assume deterministic software. Steps, expected result, actual
result, and screenshot may be enough. LLMs are different. The same prompt may produce different
outputs, and the root cause may live in the prompt, model version, retrieval context, tools,
memory, safety layer, or product workflow.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Convert individual failures into failure classes. A strong LLM bug report names the population,
not just the example: "refund escalation hallucination in policy-missing chats" is more useful
than "the bot said something wrong."
