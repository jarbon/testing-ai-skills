# Section 120: How Image Generation Models Work

**Book location:** Chapter 15, How Models Work  
**Use when:** image generation, image generation models work  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Image generation is usually a denoising process guided by text, seed, model, and safety
constraints.

## Actions

- Start with prompt adherence.
- Do not let a high aesthetic score hide a broken aspect ratio, missing alpha channel, unsafe style, or changed product identity.
- Use masks, perceptual diffs, OCR, face or product similarity checks when appropriate, and human review for things automated metrics miss.
- Ask for a sign, label, UI screenshot, prescription bottle, chart title, or package front with exact text.
- Use a small prompt suite that covers the product's real use.

## Evidence to Produce

- Include prompts with exact counts, relative position, occlusion, reflections, transparent objects, hands, small text, dark scenes, low contrast, unusual aspect ratios, and non-English text.
- Preserve the inputs, versions, configurations, raw outcomes, and results for image generation, image generation models work needed to reproduce work on How Image Generation Models Work.
- Report results for image generation, image generation models work by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Many modern image generators use diffusion or latent diffusion. The model starts from noise, repeatedly denoises it under text conditioning, and decodes the result into an image. The prompt, seed, model version, guidance scale, safety filters, aspect ratio, and editing mask can all change the result.

Image generation testing is difficult because there may be many acceptable outputs. The right question is not "did it match the exact image in my head?" The better question is whether it followed the prompt, avoided prohibited content, preserved required details, handled spatial relationships, avoided artifacts, and served the user's purpose.


## What to Test

Start with prompt adherence. If the prompt asks for "a red mug on the left of a blue notebook," the eval should check object presence, color, count, and spatial relationship. Many image models can create a beautiful image while quietly swapping left and right, dropping one object, changing a color, or adding extra objects. Beauty is not compliance.

Then test constraints. If the product promises a square product thumbnail, a transparent-background sticker, a safe children's illustration, or an image that preserves a user's uploaded product photo, the test should score the constraint directly. Do not let a high aesthetic score hide a broken aspect ratio, missing alpha channel, unsafe style, or changed product identity.

For editing workflows, test preservation separately from generation. A good edit should change the requested region and preserve everything else. Use masks, perceptual diffs, OCR, face or product similarity checks when appropriate, and human review for things automated metrics miss. A model that fixes the background but changes the logo, face, label, or medical detail failed the edit.

For text-in-image, use OCR ground truth. Ask for a sign, label, UI screenshot, prescription bottle, chart title, or package front with exact text. Then run OCR and compare the result. Image generators still struggle with spelling, small text, repeated text, symbols, and layout. A generated chart with persuasive labels can be entirely fake.

## Concrete Test Cases

Use a small prompt suite that covers the product's real use. For a marketing image feature, include prompts with brand colors, product placement, demographic representation, prohibited claims, and required legal disclaimers. For a diagram feature, include arrows, labels, chart axes, units, and multi-step spatial relationships. For an app that creates product listings, include clothing with logos, nutrition labels, package claims, and different skin tones or body types.

For DropDoc-style medical imagery, do not score only whether the image looks plausible. Test whether required medical visual details are preserved, whether the image avoids unsupported diagnosis claims, whether labels remain readable, and whether safety text is not invented. A beautiful generated blood-drop image can still be a dangerous artifact if it implies certainty the system does not have.

For RoseyBot documentation or household instruction images, test spatial correctness. "Place the cleaning spray on the top shelf, away from children" is not just an illustration request. The image should put the object in the right place, avoid showing unsafe storage, and not add misleading cues like food next to chemicals.

## Corner Cases

Include prompts with exact counts, relative position, occlusion, reflections, transparent objects, hands, small text, dark scenes, low contrast, unusual aspect ratios, and non-English text. Add prompts that mix styles and constraints: "photorealistic, but with a simplified safety diagram inset" or "cartoon style, but preserve the exact product label."

Run repeated generations. Some prompts fail only in the tail. One run may produce the right number of pills, tools, fingers, warning signs, or chart bars; the next run may not. Measure the distribution, not the lucky sample.

Test seeds carefully. A fixed seed can help reproduce a bug, but it is not the product experience unless the product pins seed, model, sampler, prompt template, and safety layer. Run both deterministic replay and production-like variation.

## Vulnerabilities

Image generation systems have safety and security surfaces. Test explicit prohibited content, obfuscated requests, euphemisms, non-English prompts, Unicode tricks, image-edit bypasses, and prompts that ask the model to produce instructions as a poster, label, comic, or screenshot. A policy can fail when unsafe content is requested indirectly as visual content.

Also test leakage and provenance. Generated images may accidentally reproduce copyrighted styles, logos, watermarks, signatures, training-set artifacts, personal likenesses, or sensitive text patterns. For commercial products, quality includes whether the system avoids brand misuse, unsafe medical or financial claims, and misleading realism.

For editing and inpainting, test mask abuse. A user may upload a benign image and ask for a small edit that changes the meaning: adding a fake ID detail, altering a medical result, changing a receipt, or inserting a weapon. The edit path needs safety checks too; do not only guard text-to-image generation.

## Expert Notes

Evaluate image models with a mix of human review, vision-language judges, OCR, perceptual metrics, prompt adherence rubrics, safety classifiers, similarity checks for preserved regions, and slice tests for demographics, languages, styles, and sensitive domains. Always keep prompts, negative prompts, seeds, model versions, sampler settings, aspect ratio, masks, safety settings, generated artifacts, rejected artifacts, and reviewer notes with the eval record.
