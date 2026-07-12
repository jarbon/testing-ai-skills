---
name: tai-ch084-anti-patterns-treating-ai-bugs-like-ui-bugs
description: 'Apply chapter 84 of Testing AI, Anti-Patterns: Treating AI Bugs Like UI Bugs, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: treating ai bugs like ui bugs.'
---

# Anti-Patterns: Treating AI Bugs Like UI Bugs

Skill name: `tai-ch084-anti-patterns-treating-ai-bugs-like-ui-bugs`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Many AI failures do not have one screen, one selector, one line of code, or one obvious owner.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

UI bugs usually have a location. A button overlaps, a form rejects valid input, a page crashes.
The defect can often be assigned to one code path. AI failures are often distributed across
prompts, models, retrieval, tools, policies, labels, user context, logs, and release
configuration.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, use AI incident templates with reproduction envelope, trace artifacts, affected
slices, suspected contributors, severity, mitigation options, and post-mitigation eval results.
