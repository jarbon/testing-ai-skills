---
name: testing-ai-ch01-one-run-testing
description: "Use when an AI coding agent needs Chapter 1 of Testing AI: The End of One-Run Testing. Trigger topics include one-run demos, nondeterminism, exact assertions, scoring criteria, 0-10 rubrics, variance, deterministic baselines. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 1: The End of One-Run Testing

Use this skill to make an AI coding agent apply Chapter 1 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

one-run demos, nondeterminism, exact assertions, scoring criteria, 0-10 rubrics, variance, deterministic baselines

## Apply the chapter

- Replace brittle exact assertions with evaluation criteria that allow harmless variation and block harmful variation.
- Create repeated-run tests that measure output distributions instead of a single lucky sample.
- Define 10/7/4/0 scoring anchors before running the AI coding agent or product workflow.
- Run a deterministic baseline first when possible, then restore production variance to isolate instability.

## Produce these artifacts

- variance table
- criteria-based assertions
- 0-10 rubric anchors
- baseline vs production-variance rerun plan

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 1 of Testing AI (The End of One-Run Testing), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
