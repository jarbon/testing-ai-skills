---
name: tai-ch139-testing-when-not-to-personalize
description: 'Apply chapter 139 of Testing AI, Testing When Not to Personalize, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing when not to personalize.'
---

# Testing When Not to Personalize

Skill name: `tai-ch139-testing-when-not-to-personalize`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The best personalized system knows when user preference should not control the answer.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Personalization is useful when user context improves the outcome. It becomes dangerous when
preference is confused with truth, safety, fairness, or public interest. A user may prefer fast
answers, familiar sources, optimistic advice, or a narrow viewpoint. The system still needs to
decide when accuracy, freshness, diversity, legality, and safety matter more.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, define a personalization override policy. Include preference-reversal tests,
counterfactual profiles, safety and authority thresholds, exploration requirements, and
protected domains where personalization must be limited. Measure both personalization lift and
personalization harm.
