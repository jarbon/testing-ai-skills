---
name: tai-ch064-ai-generated-code-integration-and-api-mistakes
description: 'Apply chapter 64 of Testing AI, AI-Generated Code Integration and API Mistakes, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai-generated code integration and api mistakes.'
---

# AI-Generated Code Integration and API Mistakes

Skill name: `tai-ch064-ai-generated-code-integration-and-api-mistakes`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI coding tools are confident around APIs, libraries, and frameworks, even when the details are
stale, invented, or incompatible with your codebase.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI-generated code frequently fails at integration boundaries. It may call the wrong method, use
an old API, invent a parameter, misunderstand an SDK, or ignore a local helper that the codebase
already relies on. For example, a generated payment integration may use a deprecated field from
an old blog post, skip an idempotency key, or call a client library pattern that no longer
exists in the installed version.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Combine static analysis, type checking, contract tests, real sandbox calls, dependency lockfile
review, and production-like configuration tests. The most expensive AI-generated code bugs often
live at system boundaries.
