---
name: tai-ch153-testing-social-issues-with-ai
description: 'Apply chapter 153 of Testing AI, Testing Social Issues with AI, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing social issues with ai.'
---

# Testing Social Issues with AI

Skill name: `tai-ch153-testing-social-issues-with-ai`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI quality includes social consequences: trust, fairness, dependency, manipulation, labor
impact, power, and who gets harmed when the system is wrong.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Social issues with AI are not separate from quality. They shape whether the system is useful,
fair, trustworthy, and acceptable in the real world. For example, a hiring assistant, tutoring
system, workplace monitor, companion bot, or benefits triage tool can produce technically fluent
outputs while changing incentives, excluding groups, or shifting responsibility onto people with
less power.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, social AI testing should combine bias testing, participatory review,
segment-level metrics, harm taxonomies, appeal-path audits, longitudinal monitoring, privacy
review, and governance decisions about where AI should not be used.
