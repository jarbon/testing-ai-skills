---
name: tai-ch057-cost-and-token-budget-testing
description: 'Apply chapter 57 of Testing AI, Cost and Token Budget Testing, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to cost and token budget testing.'
---

# Cost and Token Budget Testing

Skill name: `tai-ch057-cost-and-token-budget-testing`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI quality includes whether the system can afford to behave that way.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Cost and token budget testing measures token growth, runaway loops, repeated tool calls, cache
misses, p95 and p99 cost, and quality per dollar. It matters because AI systems can fail
economically before they fail functionally. For example, a RAG answer may be correct but include
40 irrelevant chunks, double latency, and cost ten times more than needed.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Cost testing should track token budgets by span, cache hit rate, retry count, tool-call count,
model mix, latency percentiles, queue behavior, and marginal quality per dollar by task
category.
