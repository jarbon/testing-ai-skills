---
name: tai-ch093-bias-taxonomy-for-ai-systems
description: 'Apply chapter 93 of Testing AI, Bias Taxonomy for AI Systems, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to bias taxonomy for ai systems.'
---

# Bias Taxonomy for AI Systems

Skill name: `tai-ch093-bias-taxonomy-for-ai-systems`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

You cannot test bias well until you name which kind of bias you are looking for.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Bias in AI systems can be statistical, cultural, linguistic, geographic, socioeconomic, gender-
related, racial, age-related, disability-related, political, religious, professional, platform-
specific, or domain-specific. It can appear in what the model knows, what it ignores, what it
assumes, how it speaks, and who it serves well.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, create a bias risk taxonomy for the product domain, then map each bias type to eval
slices, counterfactual tests, raters, severity labels, and mitigation owners. Bias testing
should be domain-specific, not a generic checkbox.
