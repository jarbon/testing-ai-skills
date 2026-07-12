---
name: tai-ch065-ai-generated-code-security-and-privacy-issues
description: 'Apply chapter 65 of Testing AI, AI-Generated Code Security and Privacy Issues, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai-generated code security and privacy issues.'
---

# AI-Generated Code Security and Privacy Issues

Skill name: `tai-ch065-ai-generated-code-security-and-privacy-issues`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI-generated code can create security and privacy risks because it often chooses the easiest
working pattern, not the safest production pattern.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Security bugs in AI-generated code are common because the model may produce code that is
functionally plausible but unsafe under attack. It may skip authorization, trust user input,
leak secrets, or handle sensitive data casually. For example, generated admin-route code may
check whether a user is logged in but forget to check whether that user is allowed to perform
the admin action.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, pair static analysis and dependency scanning with abuse-case tests, authorization
matrices, secret scanning, log redaction checks, prompt-injection tests, and human security
review for high-risk code paths.
