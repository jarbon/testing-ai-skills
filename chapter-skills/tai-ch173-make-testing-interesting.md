---
name: tai-ch173-make-testing-interesting
description: 'Apply chapter 173 of Testing AI, Make Testing Interesting, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to make testing interesting.'
---

# Make Testing Interesting

Skill name: `tai-ch173-make-testing-interesting`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Quality work gets better when people actually want to read the failures.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Testing can be dry. Regression suites, failure reports, dashboards, and eval runs can become a
wall of sameness. That is dangerous. If nobody wants to read the results, the quality system can
be technically correct and socially invisible.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, treat interesting test design as part of quality communication. A
useful eval artifact has technical fidelity and human salience. It preserves exact inputs,
outputs, versions, scores, traces, and statistics, but also gives people names, narratives, and
summaries they can remember.
