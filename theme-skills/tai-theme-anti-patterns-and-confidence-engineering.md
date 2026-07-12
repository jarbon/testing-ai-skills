---
name: tai-theme-anti-patterns-and-confidence-engineering
description: 'Use the Testing AI theme Anti-Patterns and Confidence Engineering to plan, review, or teach related AI quality work. Applies concepts and techniques from the book to testing AI, AI-generated software, and non-deterministic systems when relevant.'
---

# Anti-Patterns and Confidence Engineering

Skill name: `tai-theme-anti-patterns-and-confidence-engineering`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Theme Purpose

The next failure mode is not technical capability. It is teams using old quality habits on systems that no longer behave like yesterday's software. This chapter names the traps that create false confidence, then turns toward confidence engineering.

Apply these concepts when testing AI, AI-generated software, model-backed features, agents, search, chatbots, RAG systems, generated code, dynamic interfaces, or other software whose behavior can vary across runs, users, data, tools, or time.

## How To Use This Theme

- Identify the behavior, capability, risk, or release decision being evaluated.
- Choose the relevant concepts below and turn them into concrete eval cases, samples, traces, checks, rubrics, metrics, or release gates.
- Prefer evidence that supports a decision: ship, canary, hold, rollback, or collect more samples.
- Report by slices and severe failures when averages hide risk.
- Preserve enough evidence that another person or agent can understand what was tested, how it was measured, and why the recommendation follows.

## Concepts And Techniques To Apply

- The next failure mode is not technical capability. It is teams using old quality habits on systems that no longer behave like yesterday's software. This chapter names the traps that create false confidence, then turns toward confidence engineering.

## Reporting Guidance

- State what was tested and what population the evidence represents.
- Explain uncertainty, missing coverage, severe failures, and known blind spots.
- Connect findings to a concrete decision or next action.
- Use topic-specific chapter skills only when deeper detail is needed; this theme skill should stand alone as practical guidance.
