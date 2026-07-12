---
name: tai-ch096-measuring-bias-with-slices-counterfactuals-and-raters
description: 'Apply chapter 96 of Testing AI, Measuring Bias with Slices, Counterfactuals, and Raters, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to measuring bias with slices, counterfactuals, and raters.'
---

# Measuring Bias with Slices, Counterfactuals, and Raters

Skill name: `tai-ch096-measuring-bias-with-slices-counterfactuals-and-raters`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Bias testing needs comparison. Slices and counterfactuals turn vague concern into measurable
evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Bias testing starts by defining slices: groups, languages, regions, user needs, risk levels, and
contexts that should be measured separately. Then Confidence Engineers create comparable cases
across those slices. Counterfactual tests change one sensitive or contextual attribute while
keeping the rest of the case similar.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Combine slice metrics, counterfactual pairs, inter-rater agreement, severity scoring, confidence
intervals, and qualitative review. Bias reports should explain both measured disparity and
likely user harm.
