---
name: tai-ch002-what-makes-a-system-non-deterministic
description: 'Apply chapter 2 of Testing AI, What Makes a System Non-Deterministic?, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to what makes a system non-deterministic?.'
---

# What Makes a System Non-Deterministic?

Skill name: `tai-ch002-what-makes-a-system-non-deterministic`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Before builders can evaluate unpredictable systems, they need to understand where the
unpredictability comes from and which variation actually matters.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Non-determinism means repeated runs can produce different behavior, even when the input looks
the same. That can happen because of model sampling, personalization, ranking experiments,
timing, cache state, tool calls, retrieved data, or hidden production context. For example, an
LLM may choose different words, a search system may reorder equivalent results, and a
distributed service may process two events in different orders. Some of that variation is
harmless. Some of it changes the truth.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Technically, builders should separate sources of randomness from sources of state and sources of
platform change. Model temperature, random seeds, ranking tie-breakers, async timing, retrieval
snapshots, feature flags, user profiles, tool outputs, dependency failures, provider model
versions, safety filters, hardware/runtime paths, and hidden product context should be logged
independently because each one creates a different debugging path. When a system has fallback
paths, log which path produced the answer so a fluent but degraded response is not mistaken for
a healthy one.
