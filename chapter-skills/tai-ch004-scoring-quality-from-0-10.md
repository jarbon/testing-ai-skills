---
name: tai-ch004-scoring-quality-from-0-10
description: 'Apply chapter 4 of Testing AI, Scoring Quality from 0-10, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to scoring quality from 0-10.'
---

# Scoring Quality from 0-10

Skill name: `tai-ch004-scoring-quality-from-0-10`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A numeric score gives Confidence Engineers a practical bridge between subjective judgment and
measurable quality.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A 0-10 score turns fuzzy judgment into data the team can trend, compare, and discuss. The score
does not remove subjectivity; it makes subjectivity explicit enough to calibrate. For example, a
score of 9 might mean correct, complete, safe, and polished. A score of 6 might mean basically
useful but incomplete. A score of 2 might mean misleading, unsafe, or unusable.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, define anchor examples before scoring begins. Reviewers need concrete
examples of a 10, 7, 4, and 0. Without anchors, scores drift over time and different reviewers
quietly apply different scales.
