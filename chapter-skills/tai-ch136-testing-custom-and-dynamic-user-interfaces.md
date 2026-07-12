---
name: tai-ch136-testing-custom-and-dynamic-user-interfaces
description: 'Apply chapter 136 of Testing AI, Testing Custom and Dynamic User Interfaces, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing custom and dynamic user interfaces.'
---

# Testing Custom and Dynamic User Interfaces

Skill name: `tai-ch136-testing-custom-and-dynamic-user-interfaces`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI-generated interfaces make the UI itself non-deterministic. Confidence Engineers must evaluate
whether the interface is appropriate, safe, accessible, and recoverable.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Custom and dynamic user interfaces will let AI generate screens, controls, workflows,
dashboards, forms, and explanations on demand. Instead of one fixed UI, each user may see a
different interface for the same underlying task. For example, a finance assistant might
generate a compact table for an expert user, a guided wizard for a novice, and a voice-first
flow for an accessibility need. The UI becomes part of the AI output.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, dynamic UI testing should use visual regression, accessibility
automation, human usability review, schema validation for generated components, permission-aware
action contracts, cross-device screenshots, and trace links from UI decisions back to model
prompts and policies.
