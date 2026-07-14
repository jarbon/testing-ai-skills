---
name: testing-ai-ch15-how-models-work
description: Use when an AI coding agent needs Chapter 15 of Testing AI: How Models Work. Trigger topics include LLM training, tokenization, transformer blocks, logits, sampling, RLHF, RLAIF, preference tuning, image generation, VLM, fine-tuning regression. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 15: How Models Work

Use this skill to make an AI coding agent apply Chapter 15 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

LLM training, tokenization, transformer blocks, logits, sampling, RLHF, RLAIF, preference tuning, image generation, VLM, fine-tuning regression

## Apply the chapter

- Use model mechanics to design better tests: tokenization, context windows, sampling, logits, reward tuning, and multimodal pipelines all create failure modes.
- Test preference tuning for verbosity, sycophancy, safety, and domain-specific reward mismatch.
- For image and vision-language models, test inputs, extracted evidence, final answers, and safety filters together.
- Expect fine-tuning and model updates to regress capabilities outside the target task.

## Produce these artifacts

- mechanism-aware test list
- tokenization/cutoff checks
- preference-tuning risks
- VLM/image test cases
- fine-tuning regression suite

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 15 of Testing AI (How Models Work), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
