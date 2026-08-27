---
name: testing-ai-ch03-sampling-uncertainty
description: "Use when an AI coding agent needs Chapter 3 of Testing AI: Sampling and Uncertainty. Trigger topics include sample size, confidence intervals, uncertainty, repeated runs, model-reported confidence, statistical confidence. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 3: Sampling and Uncertainty

Use this skill to make an AI coding agent apply Chapter 3 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

sample size, confidence intervals, uncertainty, repeated runs, model-reported confidence, statistical confidence

## Apply the chapter

- Estimate behavior from samples without pretending the sample is the truth.
- Report confidence intervals and sample counts next to scores.
- Prefer paired comparisons when the same cases run through competing versions.
- Separate model-reported confidence from measured statistical confidence.

## Produce these artifacts

- sample-size plan
- confidence interval report
- uncertainty notes
- repeat-run distribution summary

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 3 of Testing AI (Sampling and Uncertainty), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
