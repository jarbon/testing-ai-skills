---
name: tai-ch080-anti-patterns-testing-only-the-final-answer
description: 'Apply chapter 80 of Testing AI, Anti-Patterns: Testing Only the Final Answer, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: testing only the final answer.'
---

# Anti-Patterns: Testing Only the Final Answer

Skill name: `tai-ch080-anti-patterns-testing-only-the-final-answer`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

For RAG and agents, the visible answer is only the last step in a larger system.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Final-answer testing asks whether the user-facing response looks good. That matters, but it is
not enough for systems that retrieve, plan, call tools, update state, or cite sources. The final
answer can be right for the wrong reason, or wrong because an earlier hidden step failed.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, store traces as eval artifacts. Score retrieval, planning, tool
choice, arguments, permission boundaries, recovery, final answer, and side effects separately.
