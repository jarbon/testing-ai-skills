---
name: tai-theme-judges-humans-and-disagreement
description: 'Use the Testing AI theme Judges, Humans, and Disagreement to plan, review, or teach related AI quality work. Applies concepts and techniques from the book to testing AI, AI-generated software, and non-deterministic systems when relevant.'
---

# Judges, Humans, and Disagreement

Skill name: `tai-theme-judges-humans-and-disagreement`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Theme Purpose

Before a model can learn, before an eval can score, and before a holdout can protect you from fooling yourself, someone or something has to decide what the examples mean. That is data labeling. This chapter shows how to use judgment at scale while respecting disagreement, calibration, incentives, and ambiguity.

Apply these concepts when testing AI, AI-generated software, model-backed features, agents, search, chatbots, RAG systems, generated code, dynamic interfaces, or other software whose behavior can vary across runs, users, data, tools, or time.

## How To Use This Theme

- Identify the behavior, capability, risk, or release decision being evaluated.
- Choose the relevant concepts below and turn them into concrete eval cases, samples, traces, checks, rubrics, metrics, or release gates.
- Prefer evidence that supports a decision: ship, canary, hold, rollback, or collect more samples.
- Report by slices and severe failures when averages hide risk.
- Preserve enough evidence that another person or agent can understand what was tested, how it was measured, and why the recommendation follows.

## Concepts And Techniques To Apply

- Before a model can learn, before an eval can score, and before a holdout can protect you from fooling yourself, someone or something has to decide what the examples mean. That is data labeling. This chapter shows how to use judgment at scale while respecting disagreement, calibration, incentives, and ambiguity.

## Reporting Guidance

- State what was tested and what population the evidence represents.
- Explain uncertainty, missing coverage, severe failures, and known blind spots.
- Connect findings to a concrete decision or next action.
- Use topic-specific chapter skills only when deeper detail is needed; this theme skill should stand alone as practical guidance.
