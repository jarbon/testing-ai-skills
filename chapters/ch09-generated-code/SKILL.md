---
name: testing-ai-ch09-generated-code
description: Use when an AI coding agent needs Chapter 9 of Testing AI: Generated Code Changes the Job. Trigger topics include AI-generated code, coding agents, unit tests, integration, security, privacy, maintainability, architecture debt, generated tests, review loops, halting problem. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance.
---

# Chapter 9: Generated Code Changes the Job

Use this skill to make an AI coding agent apply Chapter 9 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

AI-generated code, coding agents, unit tests, integration, security, privacy, maintainability, architecture debt, generated tests, review loops, halting problem

## Apply the chapter

- Assume generated code that looks right can still be wrong in integration, security, privacy, permissions, and deployment behavior.
- Ask a different AI or review path to test code produced by the coding agent.
- Inspect AI-generated tests for shallow assertions and missing requirements.
- Execute meaningful behavior, integration, and security tests; static analysis helps but is not enough for arbitrary behavior.

## Produce these artifacts

- generated-code risk review
- test plan for agent patch
- security/privacy checklist
- AI-generated-test critique
- trace-to-fix loop

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 9 of Testing AI (Generated Code Changes the Job), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
