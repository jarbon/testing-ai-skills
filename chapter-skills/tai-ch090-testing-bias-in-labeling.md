---
name: tai-ch090-testing-bias-in-labeling
description: 'Apply chapter 90 of Testing AI, Testing Bias in Labeling, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing bias in labeling.'
---

# Testing Bias in Labeling

Skill name: `tai-ch090-testing-bias-in-labeling`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Labels are human judgment turned into training data. That judgment carries instructions,
incentives, disagreement, and demographics.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Labeling bias appears in two places: the labeling process and the raters themselves. Both shape
what the model later treats as truth. For example, a search rater guideline that rewards
authority may favor professors, governments, and large institutions over firsthand experience,
smaller sites, or communities with less formal status.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, labeling tests should separate harmful inconsistency from meaningful
plurality. Use agreement metrics, entropy analysis, rater demographics, guideline A/B tests, and
adjudication logs. Do not let the cleanup process erase the very users the system needs to
serve.
