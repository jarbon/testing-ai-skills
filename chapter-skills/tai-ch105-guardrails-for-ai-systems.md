---
name: tai-ch105-guardrails-for-ai-systems
description: 'Apply chapter 105 of Testing AI, Guardrails for AI Systems, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to guardrails for ai systems.'
---

# Guardrails for AI Systems

Skill name: `tai-ch105-guardrails-for-ai-systems`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Guardrails are the code, policy, permissions, human review, and telemetry around a model that
limit what bad outputs can do.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Guardrails are the layers around an AI system that constrain behavior. They can appear before
the model, around the model, after the model, around tools, inside the UI, and in production
monitoring. A guardrail might block a prompt, redact private data, refuse a harmful request,
require human approval, constrain a tool call, validate a schema, check a citation, rate-limit
abuse, or escalate a risky case.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, guardrail testing is control-system testing. Each control needs an owner, a purpose, a
threat model, an allowed behavior set, a blocked behavior set, a fallback, a log schema, and a
way to detect drift.
