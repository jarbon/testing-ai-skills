---
name: tai-ch100-owasp-top-10-for-llm-applications
description: 'Apply chapter 100 of Testing AI, OWASP Top 10 for LLM Applications, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to owasp top 10 for llm applications.'
---

# OWASP Top 10 for LLM Applications

Skill name: `tai-ch100-owasp-top-10-for-llm-applications`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The OWASP LLM Top 10 is useful when security risks need to become concrete eval cases, release
gates, traces, and mitigations.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

OWASP gives AI teams a practical security checklist for LLM applications. The most useful move
is not memorizing the list. The helpful move is turning each risk into test cases, traces,
monitors, and release blockers.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Map each OWASP category to assets, attackers, trust boundaries, mitigations, eval cases, traces,
monitors, and owners. Use layered controls: least privilege, scoped tools, output encoding,
retrieval access checks, prompt-injection detection, secret scanning, sandboxing, rate limits,
cost limits, human approval, and rollback.
