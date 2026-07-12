---
name: tai-ch190-appendix-agentic-frameworks-vs-parameterized-workflows
description: 'Apply chapter 190 of Testing AI, Appendix: Agentic Frameworks vs. Parameterized Workflows, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: agentic frameworks vs. parameterized workflows.'
---

# Appendix: Agentic Frameworks vs. Parameterized Workflows

Skill name: `tai-ch190-appendix-agentic-frameworks-vs-parameterized-workflows`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Most workflows do not need an autonomous agent. They need a well-bounded procedure with a few
intelligent steps.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Agentic frameworks are seductive. They promise planning, tool choice, memory, reflection,
retries, and autonomy. Sometimes that is exactly what the product needs. Often it is too much
machinery for a workflow that already has a known path. A lot of AI quality problems come from
giving the model freedom where the product needed structure. If the task has a stable business
process, known steps, known permissions, known tools, and known stopping conditions, a
parameterized procedural workflow is usually easier to test, debug, secure, and operate.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, evaluate autonomy as a risk budget. Every degree of freedom needs a reason, a
guardrail, an observable trace, and a test. The best AI architecture is often not the most
agentic one; it is the one with the smallest amount of autonomy that still solves the user
problem.
