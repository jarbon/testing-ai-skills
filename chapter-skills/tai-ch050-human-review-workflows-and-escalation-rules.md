---
name: tai-ch050-human-review-workflows-and-escalation-rules
description: 'Apply chapter 50 of Testing AI, Human Review Workflows and Escalation Rules, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to human review workflows and escalation rules.'
---

# Human Review Workflows and Escalation Rules

Skill name: `tai-ch050-human-review-workflows-and-escalation-rules`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The point of measurement is not just a score. It is knowing when automation is enough and when a
human must step in.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Human review workflows define how evaluation evidence turns into action. Some cases can be
handled by deterministic checks or LLM judges. Others need expert review, policy review,
security review, legal review, or product escalation. For example, a low-risk style issue can
stay automated, but a privacy leak, medical-risk answer, account-deletion action, high-dollar
transaction, legal-risk decision, or reputationally sensitive response should have a clear human
escalation path.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, track reviewer queue time, overturn rate, escalation precision,
escalation recall, reviewer agreement, and category-level escalation load. A review workflow is
itself a system that needs quality metrics. For particularly sensitive, complex, expensive,
legally risky, safety-critical, or reputation-sensitive cases, require overlapping human review.
One reviewer may not be enough; use second-reader workflows, expert tie-breakers, or independent
review from multiple humans when the cost of a bad decision is high.
