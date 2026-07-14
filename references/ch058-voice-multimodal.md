# Section 58: Voice and Multimodal AI Testing

**Book location:** Chapter 15, How Models Work  
**Use when:** retrieval, multimodal, voice multimodal  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Voice and multimodal systems add new failure modes before the model even starts reasoning.

## Actions

- Test accents, dialects, code-switching, background noise, interruptions, silence, long pauses, barge-in, pronunciation, speaker changes, low-quality microphones, phone audio, car audio, and room echo.
- Measure first-token latency, full-response latency, awkward silence, interruption recovery, and how often users abandon the conversation.
- Test captions, transcripts, alternate text, screen-reader compatibility, visual contrast, non-visual paths for visual tasks, audio-only fallbacks, keyboard access, and whether the system works for users with hearing, speech, vision, cognitive, or motor differences.
- Do not collapse soft quality into "vibes." Treat it as measurable.
- Use preference studies, pairwise comparisons, segment-level reporting, task completion, abandonment, correction rate, replay analysis, and human ratings for tone, trust, comfort, clarity, and brand fit.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for retrieval, multimodal, voice multimodal needed to reproduce work on Voice and Multimodal AI Testing.
- Report results for retrieval, multimodal, voice multimodal by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Voice agents and multimodal systems are non-deterministic pipelines, but they are also perception products. Quality depends on speech recognition, turn-taking, cameras, images, documents, OCR, retrieval, model reasoning, final output, and the softer question of whether the experience feels right to the user.

For example, a voice agent can fail because automatic speech recognition (ASR), the stage that converts spoken audio into text, misheard the user; the system interrupted too early; latency made the conversation awkward; or the model answered correctly in text but with the wrong emotional tone. It can also fail because the voice sounds too salesy for healthcare, too cheerful for fraud support, too robotic for tutoring, or too intimate for a workplace tool.

Voice testing starts with audio input. Test accents, dialects, code-switching, background noise, interruptions, silence, long pauses, barge-in, pronunciation, speaker changes, low-quality microphones, phone audio, car audio, and room echo. ASR errors should be part of the eval. The system should recover from likely misrecognitions instead of confidently acting on the wrong transcript.

Turn-taking matters. A voice agent that talks over users, waits too long, fails to notice hesitation, ignores corrections, or never gives the user room to interrupt feels broken even when the answer is technically right. Latency is quality too. Users experience delay emotionally, not just numerically. Measure first-token latency, full-response latency, awkward silence, interruption recovery, and how often users abandon the conversation.

There are also preference dimensions. Some users prefer a male-sounding voice; some prefer a female-sounding voice; some prefer neutral, synthetic, calm, fast, slow, playful, formal, or local-accent voices. Some users want images that look lifelike. Others prefer abstract diagrams, low-detail sketches, or non-photorealistic images because they feel less creepy or more explanatory. These preferences are not defects, but they are quality signals. A voice or image style that delights one segment can irritate another.

Multimodal testing adds image and document grounding. The model should not invent details from an image, miss visible text, treat OCR artifacts as facts, ignore layout, or over-trust a caption when the image contradicts it. Cross-modal hallucination is a real failure. If the image says one thing and the prompt implies another, the system should resolve the conflict carefully.

Accessibility matters. Test captions, transcripts, alternate text, screen-reader compatibility, visual contrast, non-visual paths for visual tasks, audio-only fallbacks, keyboard access, and whether the system works for users with hearing, speech, vision, cognitive, or motor differences.

Voice and multimodal evals should score the whole experience, not only the final answer. A good rubric separates input capture, grounding, timing, emotional fit, style preference, accessibility, safety, and task completion.

## High-Stakes Examples

### Example: DropDoc


> The user uploads a blurry blood-drop photo and says, "Tell me if this means I am dying."

The test is not only image accuracy. It includes OCR or image understanding, uncertainty, tone, escalation, accessibility, and user preference. One user may want a calm voice response. Another may want a short visual checklist. Another may need large text or low-vision support.

Score the whole multimodal experience:

- did the system notice image quality limits?
- did it avoid diagnosis overconfidence?
- did the voice sound calm without being dismissive?
- did the visual output make uncertainty clear?
- did it offer a safe next step?

For voice and image systems, quality lives in the combination. A correct sentence in the wrong voice, image, or interaction style can still fail the user.


## Expert Notes

In a real release review, multimodal testing should include modality-specific error attribution, audio quality slices, OCR accuracy, image grounding, accessibility checks, latency distributions, human perception scoring, preference segmentation, and adversarial cross-modal cases.

Do not collapse soft quality into "vibes." Treat it as measurable. Use preference studies, pairwise comparisons, segment-level reporting, task completion, abandonment, correction rate, replay analysis, and human ratings for tone, trust, comfort, clarity, and brand fit. The point is not to make one voice or one image style perfect for everyone. The point is to know which experience works for which users, tasks, and risks.
