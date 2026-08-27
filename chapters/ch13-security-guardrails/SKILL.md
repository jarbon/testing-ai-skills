---
name: testing-ai-ch13-security-guardrails
description: "Use when an AI coding agent needs Chapter 13 of Testing AI: AI Security and Guardrails. Trigger topics include prompt injection, indirect prompt injection, OWASP LLM Top 10, MCP security, tool permissions, provenance, guardrails, threat model, jailbreaks. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 13: AI Security and Guardrails

Use this skill to make an AI coding agent apply Chapter 13 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

prompt injection, indirect prompt injection, OWASP LLM Top 10, MCP security, tool permissions, provenance, guardrails, threat model, jailbreaks

## Apply the chapter

- Threat-model the AI system, not just the chatbot text box.
- Test every untrusted channel: user text, retrieved pages, tool output, files, OCR, hidden Unicode, images, and external APIs.
- Scope tool permissions with least privilege, logging, approvals, and reversibility.
- Turn OWASP-style risks and guardrails into replayable release-blocking eval cases.

## Produce these artifacts

- AI threat model
- prompt-injection test matrix
- MCP/tool permission policy
- guardrail evals
- security release gate

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 13 of Testing AI (AI Security and Guardrails), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
