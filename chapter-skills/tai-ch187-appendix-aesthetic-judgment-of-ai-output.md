---
name: tai-ch187-appendix-aesthetic-judgment-of-ai-output
description: 'Apply chapter 187 of Testing AI, Appendix: Aesthetic Judgment of AI Output, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: aesthetic judgment of ai output.'
---

# Appendix: Aesthetic Judgment of AI Output

Skill name: `tai-ch187-appendix-aesthetic-judgment-of-ai-output`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI output can be correct and still feel cheap, awkward, off-brand, or untrustworthy.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Aesthetic judgment is not decoration. It is part of quality. Users decide whether an AI system
feels credible, careful, useful, and worth trusting through the surface of its output: wording,
rhythm, layout, visual balance, tone, specificity, and taste.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, aesthetic evaluation should combine rubric scoring, pairwise preference
tests, inter-rater agreement, calibrated LLM judges, reference exemplars, and production outcome
metrics such as edit time, acceptance rate, abandonment, conversion, escalation, or user trust.
