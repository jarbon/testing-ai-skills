---
name: tai-ch144-testing-dangerous-physical-and-embodied-ai
description: 'Apply chapter 144 of Testing AI, Testing Dangerous Physical and Embodied AI, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing dangerous physical and embodied ai.'
---

# Testing Dangerous Physical and Embodied AI

Skill name: `tai-ch144-testing-dangerous-physical-and-embodied-ai`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When AI can move matter, spend money, unlock doors, steer vehicles, or operate tools, testing
must treat action as risk.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Physical and embodied AI systems can cause harm through action, not only through words. They may
control robots, vehicles, drones, lab equipment, medical devices, industrial machines, smart
homes, procurement systems, or security tools. For example, an agent that can schedule a repair,
order parts, unlock a facility, and instruct a technician has a larger blast radius than a
chatbot that only explains policy.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Physical AI testing should include hazard analysis, fault-tree analysis, misuse cases, safety
envelopes, runtime monitors, independent interlocks, audit logs, staged rollouts, near-miss
analysis, and adversarial action-chain testing.
