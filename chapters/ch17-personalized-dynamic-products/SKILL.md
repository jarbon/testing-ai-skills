---
name: testing-ai-ch17-personalized-dynamic-products
description: Use when an AI coding agent needs Chapter 17 of Testing AI: Personalized and Dynamic AI Products. Trigger topics include personalization, dynamic UI, memory, identity, N=1, synthetic users, accessibility, privacy, adaptive interfaces. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 17: Personalized and Dynamic AI Products

Use this skill to make an AI coding agent apply Chapter 17 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

personalization, dynamic UI, memory, identity, N=1, synthetic users, accessibility, privacy, adaptive interfaces

## Apply the chapter

- Test personalized behavior at N=1: the number of users can be one, and the product still has to be right for that person.
- Map dynamic UI surfaces: content, layout, actions, tone, ranking, pricing, accessibility, privacy, and timing.
- Use synthetic personas carefully, but validate against real traces and representative raters.
- Check user-owned memory, opt-out behavior, privacy boundaries, and creepy personalization.

## Produce these artifacts

- personalization surface map
- persona/slice cases
- memory/privacy tests
- dynamic UI regression plan

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 17 of Testing AI (Personalized and Dynamic AI Products), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
