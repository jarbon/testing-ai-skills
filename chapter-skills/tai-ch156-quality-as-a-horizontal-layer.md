---
name: tai-ch156-quality-as-a-horizontal-layer
description: 'Apply chapter 156 of Testing AI, Quality as a Horizontal Layer, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to quality as a horizontal layer.'
---

# Quality as a Horizontal Layer

Skill name: `tai-ch156-quality-as-a-horizontal-layer`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The endgame is not every model team testing itself. The endgame is an independent quality layer
that works across models, platforms, apps, and agents.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

AI quality cannot live only inside the frontier model labs or only inside platform teams. The
world is moving toward many models, many platforms, many tools, and many apps stitched together
into user workflows. Quality has to become a horizontal layer across all of it. For example, a
travel assistant may use one model for planning, another model for extraction, a browser agent,
a payment platform, a calendar integration, email, maps, and a customer-support handoff. No
single model provider or platform owner can fully test that user journey alone.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, horizontal AI quality should define platform-independent eval contracts, cross-vendor
trace schemas, model-agnostic rubrics, independent judge calibration, portable regression
suites, and governance rules that separate generation from validation. The evaluator must be
able to compare systems across vendors and workflows, not merely certify one model in isolation.
