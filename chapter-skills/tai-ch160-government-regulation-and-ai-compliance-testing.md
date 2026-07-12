---
name: tai-ch160-government-regulation-and-ai-compliance-testing
description: 'Apply chapter 160 of Testing AI, Government Regulation and AI Compliance Testing, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to government regulation and ai compliance testing.'
---

# Government Regulation and AI Compliance Testing

Skill name: `tai-ch160-government-regulation-and-ai-compliance-testing`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI regulation turns quality work into compliance evidence: risk classification, documentation,
bias testing, transparency, monitoring, and release controls.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Regulation changes the job of AI quality. A normal test report asks whether the system works
well enough. A compliance-aware test report asks a sharper question: what evidence proves that
the system was classified correctly, tested against the right risks, monitored after release,
and not misrepresented to users, customers, regulators, or auditors?

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Compliance testing becomes versioned evidence engineering. Every obligation should map to a
control. Every control should map to one or more tests. Every test should produce artifacts that
can be audited later: data sample, slice definition, model version, prompt version, policy
version, judge rubric, human review protocol, confidence interval, known limitations, and owner.
