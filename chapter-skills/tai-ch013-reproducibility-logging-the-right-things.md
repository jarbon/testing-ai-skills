---
name: tai-ch013-reproducibility-logging-the-right-things
description: 'Apply chapter 13 of Testing AI, Reproducibility: Logging the Right Things, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to reproducibility: logging the right things.'
---

# Reproducibility: Logging the Right Things

Skill name: `tai-ch013-reproducibility-logging-the-right-things`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Non-deterministic bugs are hard to debug unless Confidence Engineers capture the context around
the failure.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Reproducibility in non-deterministic systems is less about forcing the exact same output and
more about preserving enough context to explain and investigate the failure. For example, an LLM
failure may depend on model version, retrieved documents, tool outputs, prompt configuration,
temperature, timestamp, or feature flags.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert logging distinguishes replay data from diagnosis data. Replay data tries to recreate
conditions. Diagnosis data explains why the system behaved that way. Both should be privacy-
aware, access-controlled, and tied to durable artifact IDs.
