---
name: tai-ch066-ai-generated-code-maintainability-and-architecture-deb
description: 'Apply chapter 66 of Testing AI, AI-Generated Code Maintainability and Architecture Debt, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai-generated code maintainability and architecture debt.'
---

# AI-Generated Code Maintainability and Architecture Debt

Skill name: `tai-ch066-ai-generated-code-maintainability-and-architecture-deb`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI-generated code can make fast progress while quietly increasing complexity, duplication, and
long-term maintenance cost.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI coding tools are very good at adding code. They are less reliable at preserving architectural
intent. That creates technical debt even when the immediate feature works. For example, an AI
assistant may implement a new validation flow by copying logic into three components instead of
using the existing validation service. The release works, but future changes become harder and
riskier.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, evaluate AI-generated code for architectural fit, duplication,
coupling, ownership boundaries, naming consistency, cognitive complexity, and change
amplification. Technical debt is a quality issue because it raises future defect probability.
