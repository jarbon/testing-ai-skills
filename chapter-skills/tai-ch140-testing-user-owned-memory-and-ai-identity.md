---
name: tai-ch140-testing-user-owned-memory-and-ai-identity
description: 'Apply chapter 140 of Testing AI, Testing User-Owned Memory and AI Identity, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing user-owned memory and ai identity.'
---

# Testing User-Owned Memory and AI Identity

Skill name: `tai-ch140-testing-user-owned-memory-and-ai-identity`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

If AI memory shapes behavior, users need ways to inspect it, correct it, move it, and limit it.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Personal AI systems increasingly build a working model of the user: preferences, goals, writing
style, projects, relationships, constraints, risk tolerance, and history. That memory can make
the system feel useful. It can also make the system wrong in persistent ways.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, memory testing should include CRUD operations, provenance, consent,
expiration, sensitivity labels, cross-context isolation, export/import, conflict resolution, and
audit trails. Also test memory poisoning: a malicious or mistaken instruction should not become
a permanent hidden policy.
