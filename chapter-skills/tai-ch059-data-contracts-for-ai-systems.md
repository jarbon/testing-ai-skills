---
name: tai-ch059-data-contracts-for-ai-systems
description: 'Apply chapter 59 of Testing AI, Data Contracts for AI Systems, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to data contracts for ai systems.'
---

# Data Contracts for AI Systems

Skill name: `tai-ch059-data-contracts-for-ai-systems`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI systems need explicit contracts for what they receive, produce, cite, log, refuse, and do.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Data contracts define the shape and rules of AI system inputs and outputs. They make non-
deterministic systems testable by specifying what must remain deterministic around the model.
For example, an agent may generate flexible language, but its tool call must follow a schema,
its citation must reference a real source, its refusal must use an approved policy category, and
its logs must not contain secrets.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, AI data contracts should be machine-validated, versioned, attached to
traces, enforced at runtime, and tested with malformed inputs, adversarial prompts, missing
fields, tool errors, and policy changes.
