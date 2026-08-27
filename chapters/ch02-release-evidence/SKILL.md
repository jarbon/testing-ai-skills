---
name: testing-ai-ch02-release-evidence
description: "Use when an AI coding agent needs Chapter 2 of Testing AI: From Tests to Release Evidence. Trigger topics include metamorphic testing, golden sets, live sampling, risk-based sampling, stratified reporting, rare failures, pairwise comparison, logging, release gates. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 2: From Tests to Release Evidence

Use this skill to make an AI coding agent apply Chapter 2 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

metamorphic testing, golden sets, live sampling, risk-based sampling, stratified reporting, rare failures, pairwise comparison, logging, release gates

## Apply the chapter

- Turn tests into release evidence: cases, slices, traces, reviewer decisions, and explicit gates.
- Add metamorphic checks where equivalent inputs should preserve important behavior.
- Use risk-based and stratified sampling so high-impact slices are not buried by easy cases.
- Log enough to replay failures: prompt, context, model, tools, retrieved evidence, versions, scores, and reviewer rationale.

## Produce these artifacts

- release evidence packet
- risk-weighted eval plan
- metamorphic cases
- release-gate rule with blockers

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 2 of Testing AI (From Tests to Release Evidence), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
