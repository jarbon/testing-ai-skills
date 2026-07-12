---
name: tai-ch114-testing-llm-training-data-and-ai-pollution
description: 'Apply chapter 114 of Testing AI, Testing LLM Training Data and AI Pollution, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing llm training data and ai pollution.'
---

# Testing LLM Training Data and AI Pollution

Skill name: `tai-ch114-testing-llm-training-data-and-ai-pollution`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The model learns from the data it eats, including bad data, stale data, biased data, and
increasingly AI-generated data.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

LLMs are trained on enormous mixtures of text, code, documents, conversations, and sometimes
synthetic data. That scale creates power, but it also hides problems: private information,
copyrighted material, toxic content, benchmark leakage, duplicates, outdated facts, language
imbalance, and low-quality AI-generated content.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, test training-data risk through provenance audits, data cards, contamination
checks, deduplication reports, benchmark-leakage probes, memorization tests, synthetic-data
ratio tracking, and downstream slice evals. For closed models, treat these as vendor-risk
questions and product-level stress tests.
