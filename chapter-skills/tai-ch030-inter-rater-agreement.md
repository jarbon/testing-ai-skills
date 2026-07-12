---
name: tai-ch030-inter-rater-agreement
description: 'Apply chapter 30 of Testing AI, Inter-Rater Agreement, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to inter-rater agreement.'
---

# Inter-Rater Agreement

Skill name: `tai-ch030-inter-rater-agreement`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When reviewers disagree often, the evaluation system may need as much attention as the product
being evaluated.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Inter-rater agreement measures whether reviewers apply the evaluation criteria consistently.
Reviewers can be humans, LLM judges, or both. For example, if one reviewer scores an answer 9
and another scores it 3, the issue may be the output, the rubric, the policy, or reviewer
training.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert teams use agreement statistics carefully. Cohen's kappa, Fleiss' kappa, and
Krippendorff's alpha adjust for chance agreement, but they still depend on label design,
prevalence, reviewer training, and whether the task is ordinal or categorical.
