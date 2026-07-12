---
name: tai-ch067-ai-generated-tests-and-the-illusion-of-coverage
description: 'Apply chapter 67 of Testing AI, AI-Generated Tests and the Illusion of Coverage, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai-generated tests and the illusion of coverage.'
---

# AI-Generated Tests and the Illusion of Coverage

Skill name: `tai-ch067-ai-generated-tests-and-the-illusion-of-coverage`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI-generated tests can raise coverage numbers while failing to catch the bugs that matter.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI-generated tests are useful, but they often mirror the implementation instead of challenging
it. They can make a codebase look safer while leaving the important behavior untested. For
example, an AI tool may generate tests that assert a function returns exactly what the current
code returns, even when the current code is wrong. The test freezes the bug.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to score tests by fault-detection power. Use mutation testing, requirement
coverage, negative-case coverage, contract tests, and historical defect replay. AI-generated
tests should be reviewed as critically as AI-generated production code.
