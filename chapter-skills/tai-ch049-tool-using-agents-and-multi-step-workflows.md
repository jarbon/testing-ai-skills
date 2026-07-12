---
name: tai-ch049-tool-using-agents-and-multi-step-workflows
description: 'Apply chapter 49 of Testing AI, Tool-Using Agents and Multi-Step Workflows, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to tool-using agents and multi-step workflows.'
---

# Tool-Using Agents and Multi-Step Workflows

Skill name: `tai-ch049-tool-using-agents-and-multi-step-workflows`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Agents must be tested for plans, tool calls, permissions, side effects, recovery, and final
outcomes.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Tool-using agents are harder to evaluate than single-turn answers because they act. They choose
steps, call tools, interpret results, and may create side effects. For example, a travel agent
might search flights, compare policies, ask for confirmation, book a ticket, and send an email.
Quality includes every step, not just the final message.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert agent evals use traces as first-class artifacts. Use structured traces, span-level
rubrics, side-effect logs, permission matrices, tool contract checks, and severity rules that
can block release even when the final answer sounds acceptable.
