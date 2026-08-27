---
name: testing-ai-ch04-statistical-tests
description: "Use when an AI coding agent needs Chapter 4 of Testing AI: Statistical Tests for AI Quality. Trigger topics include t-test, chi-squared, p-value, effect size, practical significance, power analysis, multiple comparisons, F-score, precision, recall. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 4: Statistical Tests for AI Quality

Use this skill to make an AI coding agent apply Chapter 4 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

t-test, chi-squared, p-value, effect size, practical significance, power analysis, multiple comparisons, F-score, precision, recall

## Apply the chapter

- Choose the statistical test based on the data shape: paired vs independent, numeric vs categorical, ordinal vs binary.
- State the null hypothesis before running the eval.
- Report effect size and practical risk, not only p-values.
- Control false discoveries when trying many prompts, models, policies, or slices.

## Produce these artifacts

- test-selection note
- null hypothesis
- p-value plus effect-size summary
- multiple-comparison warning
- precision/recall/F-score tradeoff

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 4 of Testing AI (Statistical Tests for AI Quality), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
