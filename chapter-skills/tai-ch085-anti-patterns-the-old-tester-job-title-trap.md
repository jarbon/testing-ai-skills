---
name: tai-ch085-anti-patterns-the-old-tester-job-title-trap
description: 'Apply chapter 85 of Testing AI, Anti-Patterns: The Old Tester Job Title Trap, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: the old tester job title trap.'
---

# Anti-Patterns: The Old Tester Job Title Trap

Skill name: `tai-ch085-anti-patterns-the-old-tester-job-title-trap`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Tester, QA analyst, SDET, and test automation engineer are often too small for the work AI
quality now requires.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The old job titles came from a narrower world: write test cases, automate checks, file bugs,
maintain scripts, report pass/fail. AI systems need a broader role. The next-generation quality
professional needs automation, basic statistics, math literacy, creativity, product sense, and
the ability to use AI and coding agents to do the work of testing AI.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, define the role around outcomes: measuring behavior under uncertainty,
building eval infrastructure, using AI-assisted tooling, interpreting statistics, tracing
production behavior, and guiding release decisions. The title should reflect that scope.
Confidence Engineering is not a renamed QA department; it is the operating discipline for
deciding whether AI-produced software and AI-powered services are good enough to trust.
