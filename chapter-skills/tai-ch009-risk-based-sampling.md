---
name: tai-ch009-risk-based-sampling
description: 'Apply chapter 9 of Testing AI, Risk-Based Sampling, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to risk-based sampling.'
---

# Risk-Based Sampling

Skill name: `tai-ch009-risk-based-sampling`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Testing effort should follow risk. High-impact failures deserve more samples, stricter gates,
and deeper review.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Risk-based sampling puts more measurement effort where failure hurts more. Equal sampling feels
tidy, but users experience consequences, not test-plan symmetry. For example, billing, privacy,
account deletion, medical advice boundaries, and policy enforcement deserve deeper sampling than
low-risk style variations.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert risk sampling combines likelihood, severity, detectability, reversibility, and exposure.
A rare failure with irreversible harm may deserve more testing than a frequent cosmetic issue.
