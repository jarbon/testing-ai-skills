---
name: tai-ch167-failure-taxonomy-for-ai-systems
description: 'Apply chapter 167 of Testing AI, Failure Taxonomy for AI Systems, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to failure taxonomy for ai systems.'
---

# Failure Taxonomy for AI Systems

Skill name: `tai-ch167-failure-taxonomy-for-ai-systems`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A shared failure language helps teams cluster problems instead of drowning in disconnected bug
reports.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A failure taxonomy gives names to the ways AI systems fail. It helps Confidence Engineers,
engineers, product teams, and executives talk about patterns. Without a taxonomy, every failure
becomes a one-off anecdote. With a taxonomy, failures can be counted, clustered, prioritized,
and turned into regression coverage.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Failure taxonomy should connect to severity, affected slices, root-cause hypotheses, owners,
regression cases, and incident metrics.
