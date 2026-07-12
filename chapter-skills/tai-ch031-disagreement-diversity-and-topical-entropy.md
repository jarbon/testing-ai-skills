---
name: tai-ch031-disagreement-diversity-and-topical-entropy
description: 'Apply chapter 31 of Testing AI, Disagreement, Diversity, and Topical Entropy, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to disagreement, diversity, and topical entropy.'
---

# Disagreement, Diversity, and Topical Entropy

Skill name: `tai-ch031-disagreement-diversity-and-topical-entropy`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Human and AI disagreement is not always a defect. Sometimes it is a signal that different users
value different good answers.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Inter-rater agreement is useful, but perfect agreement is not always the goal. Humans can
disagree. LLM judges can disagree. Humans and LLM judges can disagree with each other. Some of
that disagreement means the rubric is vague, the policy is unclear, or the judge needs
calibration. But some disagreement is legitimate.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Model disagreement should be represented explicitly. Separate label noise, rubric ambiguity,
judge failure, expert uncertainty, and legitimate preference diversity. Use cluster analysis,
preference labels, slice reporting, and pairwise preference data when a single score hides
meaningful groups.
