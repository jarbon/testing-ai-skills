---
name: tai-ch023-p-values-evidence-not-permission
description: 'Apply chapter 23 of Testing AI, P-Values: Evidence, Not Permission, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to p-values: evidence, not permission.'
---

# P-Values: Evidence, Not Permission

Skill name: `tai-ch023-p-values-evidence-not-permission`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

P-values can support a comparison, but they do not decide whether a product is safe, useful, or
worth shipping.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A p-value is evidence about surprise under a null assumption. It is not a probability that the
new version is better, and it is not permission to ship. For example, p = 0.02 says the observed
difference would be fairly surprising if there were truly no difference under the test
assumptions. It does not say the difference is important.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert reports treat p-values as continuous evidence, not as a yes/no permission slip. A useful
report pairs the p-value with the other facts needed to make a responsible decision:
