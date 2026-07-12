---
name: tai-ch056-canary-shadow-and-rollback-strategy
description: 'Apply chapter 56 of Testing AI, Canary, Shadow, and Rollback Strategy, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to canary, shadow, and rollback strategy.'
---

# Canary, Shadow, and Rollback Strategy

Skill name: `tai-ch056-canary-shadow-and-rollback-strategy`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Non-deterministic systems should earn traffic gradually, with clear rollback rules.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Canary, shadow, and rollback strategies let teams release AI systems without betting the whole
product on one eval result. They expose the system gradually and measure real behavior before
full rollout. For example, a new support agent can run in shadow mode against real
conversations, then receive 1% of low-risk traffic, then expand only if quality, latency, cost,
escalation, and safety metrics stay inside bounds.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to treat rollout as a measured system. Define exposure units, segment gates,
guardrail metrics, rollback thresholds, statistical confidence requirements, monitoring windows,
human review queues, and post-release trace mining.
