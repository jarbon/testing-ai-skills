---
name: tai-ch073-anti-patterns-over-specific-test-plans-and-test-cases
description: 'Apply chapter 73 of Testing AI, Anti-Patterns: Over-Specific Test Plans and Test Cases, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: over-specific test plans and test cases.'
---

# Anti-Patterns: Over-Specific Test Plans and Test Cases

Skill name: `tai-ch073-anti-patterns-over-specific-test-plans-and-test-cases`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Exact steps and exact expected words can make AI tests brittle while missing the behavior that
matters.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Traditional test cases often specify exact steps, exact inputs, and exact expected outputs. That
is useful when the system should behave exactly the same way every time. AI systems often need a
different style. If there are many acceptable answers, the test should define intent,
constraints, and quality properties rather than one brittle output string.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, separate hard invariants from soft preferences. Use exact checks for
contracts and safety boundaries, and rubrics or judge-scored properties for open-ended behavior.
