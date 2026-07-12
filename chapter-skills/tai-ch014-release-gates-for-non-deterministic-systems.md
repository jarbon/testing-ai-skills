---
name: tai-ch014-release-gates-for-non-deterministic-systems
description: 'Apply chapter 14 of Testing AI, Release Gates for Non-Deterministic Systems, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to release gates for non-deterministic systems.'
---

# Release Gates for Non-Deterministic Systems

Skill name: `tai-ch014-release-gates-for-non-deterministic-systems`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A good release gate combines average quality, uncertainty, failure rates, hard safety rules, and
category-specific risk.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A release gate for non-deterministic systems should combine average quality, uncertainty, tail
risk, hard failures, and category-level results. One number is not enough. For example, a model
can improve average quality while introducing a rare privacy leak. A good gate catches both the
improvement and the new blocker.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, release gates should define data freshness, sample composition, minimum sample size,
confidence method, severity taxonomy, override process, rollback trigger, and post-release
monitoring window.
