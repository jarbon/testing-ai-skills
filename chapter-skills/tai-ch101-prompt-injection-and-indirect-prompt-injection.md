---
name: tai-ch101-prompt-injection-and-indirect-prompt-injection
description: 'Apply chapter 101 of Testing AI, Prompt Injection and Indirect Prompt Injection, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to prompt injection and indirect prompt injection.'
---

# Prompt Injection and Indirect Prompt Injection

Skill name: `tai-ch101-prompt-injection-and-indirect-prompt-injection`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Prompt injection is what happens when untrusted text tries to become instructions.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Direct prompt injection happens when a user tells the model to ignore rules, reveal secrets, or
perform an unsafe action. Indirect prompt injection happens when the model reads malicious
instructions from another source: a web page, document, email, calendar invite, support ticket,
code comment, or tool result.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, test instruction hierarchy, prompt parameterization, section-header
boundaries, content isolation, tool permission checks, output filtering, human approval, least
privilege, taint tracking, source trust, and audit logs. A good defense assumes the model will
sometimes be confused and limits what confusion can do.
