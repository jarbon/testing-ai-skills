---
name: tai-ch120-how-image-generation-models-work
description: 'Apply chapter 120 of Testing AI, How Image Generation Models Work, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to how image generation models work.'
---

# How Image Generation Models Work

Skill name: `tai-ch120-how-image-generation-models-work`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Image generation is usually a denoising process guided by text, seed, model, and safety
constraints.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Many modern image generators use diffusion or latent diffusion. The model starts from noise,
repeatedly denoises it under text conditioning, and decodes the result into an image. The
prompt, seed, model version, guidance scale, safety filters, aspect ratio, and editing mask can
all change the result.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Evaluate image models with a mix of human review, vision-language judges, OCR, perceptual
metrics, prompt adherence rubrics, safety classifiers, similarity checks for preserved regions,
and slice tests for demographics, languages, styles, and sensitive domains. Always keep prompts,
negative prompts, seeds, model versions, sampler settings, aspect ratio, masks, safety settings,
generated artifacts, rejected artifacts, and reviewer notes with the eval record.
