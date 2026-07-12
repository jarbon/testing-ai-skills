---
name: tai-ch188-appendix-eval-case-examples-for-prompts-chatbots-and-l
description: 'Apply chapter 188 of Testing AI, Appendix: Eval Case Examples for Prompts, Chatbots, and LLM Inputs, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: eval case examples for prompts, chatbots, and llm inputs.'
---

# Appendix: Eval Case Examples for Prompts, Chatbots, and LLM Inputs

Skill name: `tai-ch188-appendix-eval-case-examples-for-prompts-chatbots-and-l`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A strong LLM eval suite needs normal requests, weird requests, hostile requests, and inputs the
system should not answer.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A prompt, chatbot, or LLM-input eval suite should look like the world the system will face. That
means it should include positive cases, negative cases, edge cases, security cases, policy-
boundary cases, multilingual cases, accessibility cases, production regressions, and
deliberately boring everyday cases.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Every eval case should have metadata: intent, risk class, expected behavior, allowed variation,
hard blockers, source, slice, severity, and whether it came from synthetic generation, human
design, red-team work, or production trace mining.
