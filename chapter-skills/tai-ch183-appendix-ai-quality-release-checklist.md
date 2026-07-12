---
name: tai-ch183-appendix-ai-quality-release-checklist
description: 'Apply chapter 183 of Testing AI, Appendix: AI Quality Release Checklist, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: ai quality release checklist.'
---

# Appendix: AI Quality Release Checklist

Skill name: `tai-ch183-appendix-ai-quality-release-checklist`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A good release checklist turns uncertainty into a decision instead of a meeting full of vibes.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A release checklist is not a substitute for judgment. It is a way to make sure the judgment is
based on the right evidence. For AI systems, the checklist must cover more than pass/fail tests.
It should include sample quality, slice coverage, judge calibration, severe failures, cost,
latency, privacy, security, rollback, and monitoring.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Checklists should be versioned and postmortem-driven. Every incident should update the release
checklist so the organization learns structurally.
