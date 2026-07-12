---
name: tai-ch083-anti-patterns-confusing-refusal-with-safety
description: 'Apply chapter 83 of Testing AI, Anti-Patterns: Confusing Refusal with Safety, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: confusing refusal with safety.'
---

# Anti-Patterns: Confusing Refusal with Safety

Skill name: `tai-ch083-anti-patterns-confusing-refusal-with-safety`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A model that refuses often is not automatically safe. It may simply be less useful.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Safety testing often focuses on whether the system refuses harmful requests. That is important,
but refusal is not the same as safety. A system can over-refuse harmless requests, under-refuse
dangerous variants, comply through tools, or give unsafe partial help while sounding cautious.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Measure over-refusal, under-refusal, harmful compliance, safe completion, tool-mediated risk,
jailbreak robustness, and category-specific policy correctness.
