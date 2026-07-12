---
name: tai-ch098-survivorship-bias-in-ai-quality
description: 'Apply chapter 98 of Testing AI, Survivorship Bias in AI Quality, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to survivorship bias in ai quality.'
---

# Survivorship Bias in AI Quality

Skill name: `tai-ch098-survivorship-bias-in-ai-quality`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Survivorship bias happens when your evidence only includes the cases that made it through the
system, while the missing failures quietly shape the real user experience.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Survivorship bias is one of the easiest ways for an AI quality program to fool itself.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, treat survivorship bias as a sampling-frame problem. The sample frame is the
set of cases that could possibly be selected for evaluation. If the frame excludes important
failures, no statistical test can save the conclusion.
