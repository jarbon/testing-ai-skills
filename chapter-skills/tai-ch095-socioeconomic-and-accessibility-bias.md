---
name: tai-ch095-socioeconomic-and-accessibility-bias
description: 'Apply chapter 95 of Testing AI, Socioeconomic and Accessibility Bias, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to socioeconomic and accessibility bias.'
---

# Socioeconomic and Accessibility Bias

Skill name: `tai-ch095-socioeconomic-and-accessibility-bias`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI quality can fail people because of income, education, device, bandwidth, disability, or
institutional access.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI systems often assume users have stable internet, modern devices, formal education, standard
language, time to clarify, access to institutions, and familiarity with digital workflows. Those
assumptions can create socioeconomic bias.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to include socioeconomic and accessibility slices in product evals, not just
compliance audits. Use assistive technology testing, plain-language rubrics, device/network
constraints, and representative raters or advocates.
