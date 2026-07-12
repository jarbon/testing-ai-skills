---
name: tai-ch099-ai-security-threat-models
description: 'Apply chapter 99 of Testing AI, AI Security Threat Models, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai security threat models.'
---

# AI Security Threat Models

Skill name: `tai-ch099-ai-security-threat-models`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI security starts by naming what the system can read, infer, decide, and do.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI security is broader than jailbreak prompts. A modern AI system may read private data,
retrieve documents, call tools, write code, remember users, summarize sensitive records, route
business workflows, and influence decisions. Every capability becomes part of the threat model.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to maintain an AI-specific threat model with assets, actors, trust
boundaries, untrusted inputs, tools, permissions, logs, mitigations, eval cases, and even
physical security. Security tests should be replayable and part of release gates, not one-time
red-team theater.
