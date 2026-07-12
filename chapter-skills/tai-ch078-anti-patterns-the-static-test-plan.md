---
name: tai-ch078-anti-patterns-the-static-test-plan
description: 'Apply chapter 78 of Testing AI, Anti-Patterns: The Static Test Plan, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: the static test plan.'
---

# Anti-Patterns: The Static Test Plan

Skill name: `tai-ch078-anti-patterns-the-static-test-plan`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A frozen test plan can look responsible while the AI system keeps changing underneath it.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Traditional test plans often assume a relatively stable product surface. AI systems are less
stable because prompts, models, policies, tools, retrieval indexes, user behavior, and data
distributions change. A static plan can become theater: detailed, polished, and no longer
connected to the current risk.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to maintain a living quality system: versioned evals, changelogs, production
trace mining, drift monitors, rubric updates, and explicit compatibility rules for trend
comparisons.
