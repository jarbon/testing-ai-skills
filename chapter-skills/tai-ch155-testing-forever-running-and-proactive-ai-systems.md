---
name: tai-ch155-testing-forever-running-and-proactive-ai-systems
description: 'Apply chapter 155 of Testing AI, Testing Forever-Running and Proactive AI Systems, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing forever-running and proactive ai systems.'
---

# Testing Forever-Running and Proactive AI Systems

Skill name: `tai-ch155-testing-forever-running-and-proactive-ai-systems`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Always-on AI changes testing from request-response quality to lifetime behavior, interruption,
initiative, and restraint.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Forever-running and proactive AI systems do not wait for a prompt. They monitor, remember, plan,
notify, schedule, escalate, and act over long periods. For example, a personal AI chief of staff
might watch email, calendar, health signals, expenses, travel plans, work tasks, and family
logistics. The quality question becomes what it chooses to do when nobody is actively
supervising it.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Proactive AI testing should use time-accelerated simulation, lifecycle state models,
notification precision and recall, memory audits, permission drift checks, recurrence-risk
analysis, user-control testing, and production monitors for long-tail behavioral drift.
