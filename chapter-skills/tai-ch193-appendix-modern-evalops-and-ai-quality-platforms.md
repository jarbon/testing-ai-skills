---
name: tai-ch193-appendix-modern-evalops-and-ai-quality-platforms
description: 'Apply chapter 193 of Testing AI, Appendix: Modern EvalOps and AI Quality Platforms, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: modern evalops and ai quality platforms.'
---

# Appendix: Modern EvalOps and AI Quality Platforms

Skill name: `tai-ch193-appendix-modern-evalops-and-ai-quality-platforms`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Modern AI evaluation is a lifecycle: datasets, tasks, scorers, experiments, traces, online
monitors, human review, and release gates feeding each other.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Most teams start with a spreadsheet of prompts and a score column. That is fine for the first
week. It is not enough once an AI feature becomes production software.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, treat EvalOps like software delivery infrastructure. Version datasets, scorer code,
judge prompts, rubrics, model routes, tool schemas, retrieval snapshots, random seeds, and
environment state. Record cost and latency per case. Keep immutable run records. Separate
offline evals from online monitors. Track scorer drift and human-review overturn rates. Promote
production failures into regression suites with ownership and expiry rules.
