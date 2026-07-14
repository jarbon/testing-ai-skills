---
name: testing-ai-ch10-false-confidence-antipatterns
description: Use when an AI coding agent needs Chapter 10 of Testing AI: Anti-Patterns That Create False Confidence. Trigger topics include boolean pass fail trap, percent passed, over-specific tests, golden answer, whack-a-mole tuning, one-run demo, static test plan, aggregate score trap, refusal versus safety. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 10: Anti-Patterns That Create False Confidence

Use this skill to make an AI coding agent apply Chapter 10 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

boolean pass fail trap, percent passed, over-specific tests, golden answer, whack-a-mole tuning, one-run demo, static test plan, aggregate score trap, refusal versus safety

## Apply the chapter

- Name the false-confidence pattern before proposing a fix.
- Replace pass/fail theater with distributions, blockers, slices, and examples that explain the release decision.
- Avoid prompt whack-a-mole and single-bug fixes that regress other behavior.
- Do not treat refusal, aggregate scores, or one good demo as safety evidence.

## Produce these artifacts

- anti-pattern diagnosis
- replacement measurement plan
- false-confidence risk list
- release-policy rewrite

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 10 of Testing AI (Anti-Patterns That Create False Confidence), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
