---
name: tai-ch180-appendix-using-promptfoo
description: 'Apply chapter 180 of Testing AI, Appendix: Using Promptfoo, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: using promptfoo.'
---

# Appendix: Using Promptfoo

Skill name: `tai-ch180-appendix-using-promptfoo`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A lightweight eval tool turns prompt checks from vibes into repeatable tests that can run
locally, in CI, and before release.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Promptfoo is a practical way to turn prompt checks, model comparisons, and red-team scenarios
into repeatable evals. A Promptfoo workflow defines prompts, providers, test cases, assertions,
and scoring rules in a versioned eval file, then runs that suite whenever the prompt, model,
retrieval layer, tool policy, or application code changes. For example, a support assistant team
can compare two prompts across OpenAI, Anthropic, Gemini, and a local model, run 200 policy
cases, score outputs with assertions or an LLM judge, and fail the build if the pass rate drops
below the release threshold.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Treat Promptfoo as eval infrastructure, not a substitute for evaluation design and not something
this book should document feature by feature. Version configs, lock datasets, track judge model
changes, separate exploratory runs from release gates, and periodically compare automated scores
against human raters.
