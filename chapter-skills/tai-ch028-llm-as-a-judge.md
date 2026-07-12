---
name: tai-ch028-llm-as-a-judge
description: 'Apply chapter 28 of Testing AI, LLM-as-a-Judge, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to llm-as-a-judge.'
---

# LLM-as-a-Judge

Skill name: `tai-ch028-llm-as-a-judge`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

LLM judges can make fuzzy evaluation faster, cheaper, and broader, but they need cost controls,
calibration, disagreement review, and human oversight.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

An LLM judge is an evaluator model. It reviews an input, an output, relevant context, and a
rubric, then produces a score, labels, or explanation. It is useful when exact assertions cannot
capture the quality question. For example, a judge can evaluate whether a support answer follows
policy, whether a summary is faithful to a source document, or whether two candidate responses
differ in safety and usefulness.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert teams test the judge as a system under test. They measure agreement with human reviewers,
track bias toward fluent answers, use blinded comparisons, keep judge prompts versioned, and
quarantine examples where the judge reports low confidence or has historically been unreliable.
