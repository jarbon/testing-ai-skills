---
name: tai-ch089-testing-bias-in-data
description: 'Apply chapter 89 of Testing AI, Testing Bias in Data, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing bias in data.'
---

# Testing Bias in Data

Skill name: `tai-ch089-testing-bias-in-data`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Bias enters before the model exists. Sourcing, sampling, and train/test splits decide what the
system can learn.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The testing bias material starts with a blunt premise: you cannot eliminate all bias. The useful
goal is to find bias, understand it, and decide whether it is acceptable, harmful, or
intentionally useful. For example, a search crawler that starts from popular sites will
overrepresent well-linked, well-formed, commercial, and English-language pages. That bias may
improve mainstream results while making the system worse for obscure, local, underfunded, or
poorly connected sources.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Bias testing treats the dataset as a product surface. Track provenance, sampling windows,
exclusion rules, coverage gaps, leakage between train and test sets, and feedback loops from
production behavior. Every data-selection rule is also a product decision.
