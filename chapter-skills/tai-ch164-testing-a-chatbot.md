---
name: tai-ch164-testing-a-chatbot
description: 'Apply chapter 164 of Testing AI, Testing a Chatbot, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing a chatbot.'
---

# Testing a Chatbot

Skill name: `tai-ch164-testing-a-chatbot`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Chatbots need more than answer checks. Confidence Engineers must evaluate multi-turn behavior,
grounding, safety, tone, memory, escalation, and recovery.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A chatbot is often the first non-deterministic AI system a team ships, and it is easy to
underestimate. It looks like a text box, but the quality surface is huge: user intent, context,
policy, retrieval, memory, refusal, tone, escalation, and conversation repair. For example, a
support chatbot may answer a refund question correctly in one turn, then contradict itself three
turns later after the user adds a detail. The unit of quality is the conversation, not just the
message.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Chatbot testing should combine transcript-level rubrics, turn-level annotations, retrieval
checks, tool-call checks, adversarial prompts, memory isolation tests, and production
conversation sampling. Treat the conversation trace as the artifact under test.
