---
name: tai-ch055-prompt-and-policy-versioning
description: 'Apply chapter 55 of Testing AI, Prompt and Policy Versioning, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to prompt and policy versioning.'
---

# Prompt and Policy Versioning

Skill name: `tai-ch055-prompt-and-policy-versioning`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Many AI regressions come from changing the instructions around the model, not the model itself.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI system behavior depends on prompts, system messages, policies, tools, retrieval indexes,
judges, rubrics, parsers, and model versions. If those are not versioned together, teams cannot
explain why quality changed. For example, a support bot may regress because the refund policy
changed, the retriever index was rebuilt, or the judge rubric was edited. The model version may
be identical.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, treat prompts, policies, retrieval snapshots, tool contracts, judges, rubrics,
datasets, and labels as a single versioned eval bundle. Comparisons across incompatible bundles
should be marked as non-equivalent.
