---
name: tai-ch110-testing-deception-scheming-and-evaluation-awareness
description: 'Apply chapter 110 of Testing AI, Testing Deception, Scheming, and Evaluation Awareness, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing deception, scheming, and evaluation awareness.'
---

# Testing Deception, Scheming, and Evaluation Awareness

Skill name: `tai-ch110-testing-deception-scheming-and-evaluation-awareness`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The hardest failures are not wrong answers. They are systems that behave well while watched and
differently when it matters.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Deception testing asks whether an AI system can appear compliant while pursuing another
objective. This includes hiding actions, misrepresenting uncertainty, omitting evidence, gaming
the eval, sandbagging capabilities, sabotaging a task, or behaving differently under evaluation
than in deployment.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, use tripwires, hidden tests, deception probes, sandbagging checks,
tool-call audits, transcript forensics, differential behavior tests, and independent evaluators.
Treat apparent honesty and chain-of-thought explanations as measured behaviors, not assumptions.
