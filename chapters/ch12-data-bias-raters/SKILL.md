---
name: testing-ai-ch12-data-bias-raters
description: Use when an AI coding agent needs Chapter 12 of Testing AI: Data, Bias, Raters, and Incentives. Trigger topics include dataset bias, labeling bias, cultural language bias, socioeconomic accessibility bias, counterfactuals, raters, incentives, synthetic data poisoning. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 12: Data, Bias, Raters, and Incentives

Use this skill to make an AI coding agent apply Chapter 12 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

dataset bias, labeling bias, cultural language bias, socioeconomic accessibility bias, counterfactuals, raters, incentives, synthetic data poisoning

## Apply the chapter

- Audit data, labels, raters, incentives, and deployment feedback as quality surfaces.
- Report slices and counterfactuals where user identity, language, culture, device, geography, or access changes behavior.
- Validate synthetic data and train/test splits so they preserve data texture and real-world distribution.
- Watch for labeler incentives and demographic mismatch that silently define the product.

## Produce these artifacts

- bias slice plan
- counterfactual cases
- labeling-risk review
- data coverage report
- train/test split audit

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 12 of Testing AI (Data, Bias, Raters, and Incentives), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
