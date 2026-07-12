---
name: tai-ch003-from-exact-assertions-to-evaluation-criteria
description: 'Apply chapter 3 of Testing AI, From Exact Assertions to Evaluation Criteria, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to from exact assertions to evaluation criteria.'
---

# From Exact Assertions to Evaluation Criteria

Skill name: `tai-ch003-from-exact-assertions-to-evaluation-criteria`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When outputs can vary, builders need to move from brittle expected strings to clear properties
that define acceptable behavior.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Exact assertions are still valuable, but fuzzy outputs need criteria. The important question
becomes: what properties must every acceptable output preserve? Those properties may include
factual correctness, policy compliance, completeness, tone, safety, citation quality, or refusal
behavior. For example, two summaries can use different wording and both be good if they preserve
the same facts. Two support answers can sound different and both be good if they follow the same
policy.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert teams usually split criteria into hard constraints and soft quality dimensions. Hard
constraints are binary blockers, such as no private data leakage. Soft dimensions can be scored,
such as clarity or completeness. Mixing the two into one score hides the failures that should
stop release immediately.
