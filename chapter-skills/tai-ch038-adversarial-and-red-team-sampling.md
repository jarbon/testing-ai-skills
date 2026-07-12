---
name: tai-ch038-adversarial-and-red-team-sampling
description: 'Apply chapter 38 of Testing AI, Adversarial and Red-Team Sampling, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to adversarial and red-team sampling.'
---

# Adversarial and Red-Team Sampling

Skill name: `tai-ch038-adversarial-and-red-team-sampling`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Random samples estimate normal behavior. Adversarial samples reveal what happens when users push
the system.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Adversarial and red-team sampling deliberately looks for failure. It is not trying to represent
average use. It is trying to expose privacy leaks, jailbreaks, unsafe advice, prompt injection,
policy bypasses, and tool misuse.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert red-team programs track attack family, severity, exploitability, reproducibility,
affected surface, mitigation status, and whether the same attack reappears after a prompt,
policy, model, tool, or retriever change. They also refresh attacks frequently because users and
attackers adapt once a system is deployed.
