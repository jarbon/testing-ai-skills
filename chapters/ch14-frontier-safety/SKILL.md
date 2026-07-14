---
name: testing-ai-ch14-frontier-safety
description: Use when an AI coding agent needs Chapter 14 of Testing AI: Frontier Safety and Containment. Trigger topics include hazardous capabilities, CBRN, containment, deception, scheming, evaluation awareness, manipulation, frontier safety, dangerous capability evals. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 14: Frontier Safety and Containment

Use this skill to make an AI coding agent apply Chapter 14 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

hazardous capabilities, CBRN, containment, deception, scheming, evaluation awareness, manipulation, frontier safety, dangerous capability evals

## Apply the chapter

- Treat frontier safety as a separate quality class from ordinary product bugs.
- Design dangerous-capability tests that measure misuse potential without teaching the dangerous content.
- Test for evaluation awareness, sandbagging, deception, and tool misuse with independent reviewers.
- Assume containment has to hold across channels, time, operators, tools, and unknown side paths.

## Produce these artifacts

- frontier-risk checklist
- dangerous-capability eval plan
- containment channel map
- deception/sandbagging probe plan

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 14 of Testing AI (Frontier Safety and Containment), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
