---
name: tai-ch166-governance-for-ai-quality
description: 'Apply chapter 166 of Testing AI, Governance for AI Quality, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to governance for ai quality.'
---

# Governance for AI Quality

Skill name: `tai-ch166-governance-for-ai-quality`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI quality needs ownership, decision rights, audit trails, and escalation paths before the
incident happens.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Governance is how a team decides who owns quality decisions. It is not only a compliance
exercise. It is operational clarity. AI systems cross boundaries: product, engineering, data,
safety, legal, security, support, and vendors. Without governance, everyone assumes someone else
checked the hard part.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is that governance connects eval provenance, incident response, access control,
vendor management, and release gates. The audit trail should show who approved what evidence
under which constraints.
