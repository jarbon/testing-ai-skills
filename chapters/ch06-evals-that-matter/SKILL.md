---
name: testing-ai-ch06-evals-that-matter
description: Use when an AI coding agent needs Chapter 6 of Testing AI: Building Evals That Matter. Trigger topics include evals, benchmarks, MMLU, GPQA, HumanEval, SWE-bench, ARC Prize, NDCG, search relevance, quality metrics, asymptotic improvement, benchmark blind spots. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 6: Building Evals That Matter

Use this skill to make an AI coding agent apply Chapter 6 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

evals, benchmarks, MMLU, GPQA, HumanEval, SWE-bench, ARC Prize, NDCG, search relevance, quality metrics, asymptotic improvement, benchmark blind spots

## Apply the chapter

- Define what the eval is measuring, why it matters to users, and how the oracle works.
- Compare public benchmarks to product-specific evals; do not inherit benchmark blind spots uncritically.
- For ranking/search, use position-aware metrics like NDCG only when the user experience really depends on order.
- Build weighted quality metrics that reflect product risk, not leaderboard theater.

## Produce these artifacts

- eval spec
- benchmark-to-product gap analysis
- quality metric formula
- NDCG or ranking metric rationale
- benchmark blind-spot list

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 6 of Testing AI (Building Evals That Matter), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
