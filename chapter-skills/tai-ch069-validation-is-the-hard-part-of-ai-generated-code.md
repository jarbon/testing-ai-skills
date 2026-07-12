---
name: tai-ch069-validation-is-the-hard-part-of-ai-generated-code
description: 'Apply chapter 69 of Testing AI, Validation Is the Hard Part of AI-Generated Code, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to validation is the hard part of ai-generated code.'
---

# Validation Is the Hard Part of AI-Generated Code

Skill name: `tai-ch069-validation-is-the-hard-part-of-ai-generated-code`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI makes code generation cheap. It does not make the cost of proving that code safe, correct,
and maintainable cheap.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The seductive part of AI-generated code is speed. A model can produce hundreds or thousands of
lines in minutes, or entire products overnight. The expensive part is figuring out whether those
lines correctly interact with everything already in the system. For example, a generated billing
change may touch discounts, taxes, refunds, invoices, entitlements, audit logs, account
permissions, and support workflows. The code may be short, but the validation surface is large.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Estimate validation effort by interaction graph, not lines of code. Use superlinear growth and
the O(n^2) pairwise surface as planning heuristics for interaction risk, not literal forecasts.
Use dependency analysis, contract checks, risk scoring, mutation testing, property-based tests,
historical defect replay, and production trace replay to keep validation efficient as AI-
generated code volume rises.
