---
name: tai-ch046-monitoring-after-release
description: 'Apply chapter 46 of Testing AI, Monitoring After Release, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to monitoring after release.'
---

# Monitoring After Release

Skill name: `tai-ch046-monitoring-after-release`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

For non-deterministic systems, launch is not the end of testing. It is the start of real-world
measurement.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

For non-deterministic systems, launch is the beginning of real-world quality measurement.
Production behavior changes as users, data, policies, dependencies, and models change. For
example, a support assistant can pass pre-release tests and then drift when the policy database
changes or users discover a new edge case.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert monitoring separates data drift, model drift, behavior drift, and evaluation drift. If
the judge changes, apparent product quality can change even when the product did not. Version
every evaluator and baseline.
