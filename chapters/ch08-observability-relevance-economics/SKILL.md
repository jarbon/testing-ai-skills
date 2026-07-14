---
name: testing-ai-ch08-observability-relevance-economics
description: Use when an AI coding agent needs Chapter 8 of Testing AI: Operating AI: Observability, Relevance, and Economics. Trigger topics include observability, tracing, RAG, synthetic data, production traces, prompt versioning, EvalOps, canary, shadow, rollback, data contracts, token budgets, p95, p99. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 8: Operating AI: Observability, Relevance, and Economics

Use this skill to make an AI coding agent apply Chapter 8 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

observability, tracing, RAG, synthetic data, production traces, prompt versioning, EvalOps, canary, shadow, rollback, data contracts, token budgets, p95, p99

## Apply the chapter

- Instrument the full AI pipeline: input, prompt assembly, retrieval, model call, tools, output filters, and user-visible result.
- Separate retrieval failures from generation failures in RAG.
- Use shadow mode, canary, rollback, and data contracts as measured production controls.
- Measure cost, p95/p99 latency, token use, and reliability as quality outcomes.

## Produce these artifacts

- trace schema
- RAG failure taxonomy
- canary/shadow plan
- rollback test
- token and latency budget report

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 8 of Testing AI (Operating AI: Observability, Relevance, and Economics), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
