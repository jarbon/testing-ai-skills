---
name: tai-ch029-human-calibration-of-llm-judges
description: 'Apply chapter 29 of Testing AI, Human Calibration of LLM Judges, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to human calibration of llm judges.'
---

# Human Calibration of LLM Judges

Skill name: `tai-ch029-human-calibration-of-llm-judges`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Before relying on an LLM judge at scale, builders need to know whether it scores like a trusted
human reviewer.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

LLM judges need calibration because they are evaluators, not truth machines. Calibration checks
whether the judge scores like trusted human reviewers on the cases that matter. For example, a
judge may reward polished writing while missing a subtle policy contradiction. Calibration makes
that weakness visible before the judge is used at scale.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, track judge-human agreement over time, by category, and by severity. A judge
can be acceptable for low-risk style checks and unacceptable for regulated policy decisions.
Calibration should produce routing rules, not just a single accuracy number.
