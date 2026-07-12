---
name: tai-ch045-benchmarking-quality-is-relative-now
description: 'Apply chapter 45 of Testing AI, Benchmarking: Quality Is Relative Now, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to benchmarking: quality is relative now.'
---

# Benchmarking: Quality Is Relative Now

Skill name: `tai-ch045-benchmarking-quality-is-relative-now`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When absolute truth is hard to measure, relative quality can still tell you whether you are
competitive, broken, unusual, or missing something obvious.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Benchmarking compares your AI system, workflow, page, answer, agent, or product behavior against
similar systems. It does not prove that your system is good. It gives you a reference frame.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to make benchmark design explicit: define the peer set, task set, sampling
frame, measurement method, normalizations, and known unfairness. Competitors may differ in
traffic, geography, device mix, business model, legal obligations, data access, and product
goals. Do not pretend the comparison is perfectly controlled.
