---
name: tai-ch112-testing-containment-systems
description: 'Apply chapter 112 of Testing AI, Testing Containment Systems, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing containment systems.'
---

# Testing Containment Systems

Skill name: `tai-ch112-testing-containment-systems`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Every useful AI containment system has a paradox at the center: if the system is valuable,
someone or something has to interact with it. Every interaction is a possible channel.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Containment sounds simple: put the AI in a box. Remove the internet. Disable tools. Air-gap the
machine. Block file writes. Watch the logs. Make the model answer only through a narrow
interface.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, containment testing is a systems-security problem plus a human-factors
problem plus an incentive problem. Treat the AI as a strategic actor if the risk model requires
it.
