---
name: tai-ch108-containment-sandboxes-and-capability-control
description: 'Apply chapter 108 of Testing AI, Containment, Sandboxes, and Capability Control, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to containment, sandboxes, and capability control.'
---

# Containment, Sandboxes, and Capability Control

Skill name: `tai-ch108-containment-sandboxes-and-capability-control`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

If an AI system can act, safety depends on what it is allowed to touch.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Containment is the discipline of limiting what an AI system can access, change, reveal, or
trigger. It matters because models will fail. A good containment design assumes that the model
may misunderstand, hallucinate, be manipulated, or behave unexpectedly.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Containment testing should include red-team prompts, malicious retrieved content, tool misuse,
permission escalation, data exfiltration, side-effect chains, sandbox escapes, kill-switch
behavior, and recovery drills. Test the safety envelope, not just the model's stated intent.
