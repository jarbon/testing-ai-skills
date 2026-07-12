---
name: tai-ch192-appendix-testing-ai-review-loops-with-coding-agents
description: 'Apply chapter 192 of Testing AI, Appendix: Testing AI Review Loops with Coding Agents, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: testing ai review loops with coding agents.'
---

# Appendix: Testing AI Review Loops with Coding Agents

Skill name: `tai-ch192-appendix-testing-ai-review-loops-with-coding-agents`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A coding agent should not be the only judge of its own work. Use AI-assisted review loops to add
fast, skeptical, evidence-oriented checking close to the development workflow.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

When an AI coding agent builds something, the first pass often looks convincing. The code
compiles. The page loads. The document reads smoothly. The answer sounds confident. But AI-
generated work can still contain broken flows, weak edge-case handling, misleading copy,
accessibility problems, missing tests, stale assumptions, privacy leaks, and risky changes.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to make AI-assisted review loops part of the development contract. Define
when they run, what targets they cover, which findings block release, how reports are stored,
how fixes are verified, and where human review is required.
