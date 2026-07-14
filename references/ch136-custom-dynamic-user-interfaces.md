# Section 136: Testing Custom and Dynamic User Interfaces

**Book location:** Chapter 17, Personalized and Dynamic AI Products  
**Use when:** confidence engineer, custom dynamic user interfaces  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI-generated interfaces make the UI itself non-deterministic. Confidence Engineers must evaluate
whether the interface is appropriate, safe, accessible, and recoverable.

## Actions

- Test those surfaces separately.
- Test control appropriateness.
- Test cross-device behavior.
- Test explainability of interface choices.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, custom dynamic user interfaces needed to reproduce work on Testing Custom and Dynamic User Interfaces.
- Report results for confidence engineer, custom dynamic user interfaces by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Custom and dynamic user interfaces will let AI generate screens, controls, workflows, dashboards, forms, and explanations on demand. Instead of one fixed UI, each user may see a different interface for the same underlying task.
For example, a finance assistant might generate a compact table for an expert user, a guided wizard for a novice, and a voice-first flow for an accessibility need. The UI becomes part of the AI output.


The personalization surface is larger than most teams first assume. A dynamic UI can personalize layout, workflow path, controls, data view, forms, explanation depth, modality, accessibility behavior, device context, locale, risk gates, and memory or preference use.

Test those surfaces separately. A generated interface may choose the right layout but the wrong confirmation step. It may adapt language correctly but bury the safety warning. It may work well on desktop but lose the user's partially completed form on mobile. It may remember a user's preference without making clear when that preference shaped the interface.

The first test is task fit. Did the generated interface help the user complete the job, or did it merely look impressive?
Test control appropriateness. Dangerous actions need confirmations, reversible steps, clear consequences, and permission checks. The AI should not generate a one-click destructive action because it seems convenient.
Accessibility cannot be optional. Dynamic UIs must preserve keyboard access, screen-reader semantics, contrast, focus order, captions, labels, and understandable error states.
Layout stability matters. Generated UI should not overlap text, hide critical controls, create unreadable labels, or change structure mid-task in a way that confuses the user.
Test state continuity. If the UI changes after a model response, user input, or tool call, the user should not lose work or context.
Test cross-device behavior. A generated dashboard that works on desktop but breaks on mobile is still a quality failure.
Test explainability of interface choices. In high-risk workflows, the system should be able to explain why it presented a form, warning, recommendation, or missing-data request.
The future UI-focused Confidence Engineer will score generated interfaces the way we score generated text: against rubrics, samples, user outcomes, accessibility standards, and risk.

## Expert Notes

When the system matters, dynamic UI testing should use visual regression, accessibility automation, human usability review, schema validation for generated components, permission-aware action contracts, cross-device screenshots, and trace links from UI decisions back to model prompts and policies.
