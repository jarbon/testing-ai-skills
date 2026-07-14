---
name: testing-ai-ch20-practical-playbook
description: Use when an AI coding agent needs Chapter 20 of Testing AI: The Practical Playbook. Trigger topics include practical playbook, executive summary, chatbot testing, failure taxonomy, fail-safe design, variance-aware infrastructure, performance engineering, starter quality system. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 20: The Practical Playbook

Use this skill to make an AI coding agent apply Chapter 20 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

practical playbook, executive summary, chatbot testing, failure taxonomy, fail-safe design, variance-aware infrastructure, performance engineering, starter quality system

## Apply the chapter

- Turn the book into a concrete operating system for a team or repo.
- Start with a small quality system: cases, repeated runs, traces, rubric, slices, gate, monitor, and incident loop.
- Use fail-safe defaults and incident promotion so production failures become future eval cases.
- Make quality visible and interesting enough that people actually maintain it.

## Produce these artifacts

- starter AI quality system
- chatbot or agent test plan
- failure taxonomy
- fail-safe checklist
- team operating cadence

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 20 of Testing AI (The Practical Playbook), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
