---
name: tai-ch010-stratified-reporting
description: 'Apply chapter 10 of Testing AI, Stratified Reporting, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to stratified reporting.'
---

# Stratified Reporting

Skill name: `tai-ch010-stratified-reporting`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Overall averages can hide weak segments. Break results down by the categories that matter.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Stratified reporting breaks results into meaningful categories so weak spots do not hide inside
a good average. It shows where quality is strong and where risk clusters. For example, an
assistant may average 8.4 overall but score 6.1 on Spanish billing questions or 5.8 on account
deletion cases.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, define strata before the evaluation and ensure each important stratum
has enough samples to support a decision. Too many tiny categories create noisy numbers; too few
categories hide actionable risk.
