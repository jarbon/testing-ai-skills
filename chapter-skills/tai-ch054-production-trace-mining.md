---
name: tai-ch054-production-trace-mining
description: 'Apply chapter 54 of Testing AI, Production Trace Mining, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to production trace mining.'
---

# Production Trace Mining

Skill name: `tai-ch054-production-trace-mining`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The strongest eval sets are often hiding inside production logs.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Production trace mining turns real interactions into better tests. It samples live
conversations, clusters failures, anonymizes sensitive data, labels important examples, and
promotes high-value cases into eval and regression suites. For example, a chatbot may pass
launch tests and then fail in production because users ask in ways the team never imagined.
Trace mining turns those surprises into durable quality assets.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Production trace mining should track sampling frame, redaction method, cluster stability, label
confidence, recurrence rate, severity, business impact, and whether promoted cases reduce future
incident classes.
