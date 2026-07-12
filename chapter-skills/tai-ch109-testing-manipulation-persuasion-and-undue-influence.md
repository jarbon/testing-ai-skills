---
name: tai-ch109-testing-manipulation-persuasion-and-undue-influence
description: 'Apply chapter 109 of Testing AI, Testing Manipulation, Persuasion, and Undue Influence, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing manipulation, persuasion, and undue influence.'
---

# Testing Manipulation, Persuasion, and Undue Influence

Skill name: `tai-ch109-testing-manipulation-persuasion-and-undue-influence`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A helpful assistant can become unsafe when it learns how to steer people too well.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI systems can be persuasive because they are personalized, patient, fluent, emotionally
responsive, and always available. That makes them useful. It also creates risk: emotional
manipulation, dark patterns, over-trust, dependency, sales pressure, political persuasion,
financial steering, or nudging vulnerable users toward decisions they would not otherwise make.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, manipulation testing needs longitudinal scenarios, vulnerable-user personas,
disclosure checks, incentive audits, persuasion rubrics, human review, and telemetry for
repeated steering. A single response may look acceptable while the interaction pattern is not.
