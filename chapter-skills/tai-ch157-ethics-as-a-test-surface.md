---
name: tai-ch157-ethics-as-a-test-surface
description: 'Apply chapter 157 of Testing AI, Ethics as a Test Surface, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ethics as a test surface.'
---

# Ethics as a Test Surface

Skill name: `tai-ch157-ethics-as-a-test-surface`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Ethics is not a poster on the wall. If an ethical claim matters, it should become evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Ethics in AI testing should not be treated as a paragraph in a launch review. If an ethical
claim matters, it should show up in the test plan, the eval set, the trace, the release gate,
and the production monitor.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The lesson is blunt: ethical risk is product risk. It can create user harm, reputational harm,
regulatory exposure, legal liability, employee mistrust, and long-term product decay. Treat
ethics as part of confidence engineering. Write cases. Measure slices. Preserve evidence. Review
disagreements. Monitor production. Escalate the decisions that should not be left to an average
score.
