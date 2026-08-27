---
name: testing-ai-ch16-white-box-introspection
description: "Use when an AI coding agent needs Chapter 16 of Testing AI: Introspection: White-Box Testing Networks. Trigger topics include white-box, token IDs, attention diagnostics, activation probes, concept probes, sparse autoencoders, grokking, interpretability, network drift. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 16: Introspection: White-Box Testing Networks

Use this skill to make an AI coding agent apply Chapter 16 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

white-box, token IDs, attention diagnostics, activation probes, concept probes, sparse autoencoders, grokking, interpretability, network drift

## Apply the chapter

- Use introspection as triage evidence, not proof of correctness.
- Compare internal signals across known-good, known-bad, ambiguous, and new-version examples.
- Treat attention, activations, probes, and sparse autoencoder features as measurement systems that need validation.
- Use drift in internal signals to focus behavioral evals where the model likely changed.

## Produce these artifacts

- white-box diagnostic plan
- known-good/known-bad comparison set
- attention or activation triage report
- probe validation notes

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 16 of Testing AI (Introspection: White-Box Testing Networks), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
