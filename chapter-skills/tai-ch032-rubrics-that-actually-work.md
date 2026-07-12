---
name: tai-ch032-rubrics-that-actually-work
description: 'Apply chapter 32 of Testing AI, Rubrics That Actually Work, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to rubrics that actually work.'
---

# Rubrics That Actually Work

Skill name: `tai-ch032-rubrics-that-actually-work`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A good rubric turns fuzzy judgment into repeatable evaluation. A bad rubric creates fake
precision.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Rubrics are the operating system of non-deterministic testing. They tell humans, LLM judges, and
product teams what quality means before anyone starts arguing about individual outputs. For
example, a support assistant rubric might evaluate policy correctness, completeness, tone, user
actionability, and safety. A medical summary rubric should weight factual accuracy and omission
risk far more heavily than polish.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, test the rubric itself. Measure reviewer agreement, track which
dimensions cause confusion, maintain anchor examples, version rubric changes, and avoid changing
the rubric mid-experiment unless you restart or clearly segment the results.
