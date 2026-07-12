---
name: tai-ch154-testing-swarms-and-societies-of-ais
description: 'Apply chapter 154 of Testing AI, Testing Swarms and Societies of AIs, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing swarms and societies of ais.'
---

# Testing Swarms and Societies of AIs

Skill name: `tai-ch154-testing-swarms-and-societies-of-ais`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When many AI agents collaborate, compete, delegate, and negotiate, quality emerges from the
society, not just the individual agent.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Swarms and societies of AIs create a different testing problem. Individual agents may pass their
unit tests while the group develops coordination failures, duplicated work, hidden conflicts,
runaway loops, or emergent strategies no one intended. For example, a software team of agents
may include a product agent, coding agent, review agent, security agent, release agent, and
documentation agent. The failure may come from their handoffs, incentives, or shared blind
spots.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, swarm testing should use multi-agent traces, graph analysis of
communication, shared-memory audits, adversarial agents, incentive testing, cost caps, deadlock
detection, consensus quality scoring, and long-horizon simulation.
