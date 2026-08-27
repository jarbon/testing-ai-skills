---
name: testing-ai-ch05-judges-disagreement
description: "Use when an AI coding agent needs Chapter 5 of Testing AI: Judges, Humans, and Disagreement. Trigger topics include human raters, data labeling, rubrics, disagreement, topical entropy, inter-rater agreement, Cohen kappa, Krippendorff alpha, LLM-as-a-judge calibration. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 5: Judges, Humans, and Disagreement

Use this skill to make an AI coding agent apply Chapter 5 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

human raters, data labeling, rubrics, disagreement, topical entropy, inter-rater agreement, Cohen kappa, Krippendorff alpha, LLM-as-a-judge calibration

## Apply the chapter

- Define the human measurement system before automating it with an LLM judge.
- Write rubrics with concrete evidence requirements and calibration examples.
- Measure disagreement instead of hiding it; disagreement may signal ambiguity, missing context, or useful diversity.
- Calibrate LLM judges against humans and discount or abstain when the judge is weak.

## Produce these artifacts

- rater rubric
- calibration set
- agreement report
- judge validation plan
- adjudication workflow

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 5 of Testing AI (Judges, Humans, and Disagreement), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
