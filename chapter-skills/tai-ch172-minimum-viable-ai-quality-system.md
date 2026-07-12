---
name: tai-ch172-minimum-viable-ai-quality-system
description: 'Apply chapter 172 of Testing AI, Minimum Viable AI Quality System, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to minimum viable ai quality system.'
---

# Minimum Viable AI Quality System

Skill name: `tai-ch172-minimum-viable-ai-quality-system`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

If the book feels large, start here: a small quality system that produces real evidence instead
of ritual.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A team does not need a research lab, a giant benchmark suite, or a perfect platform to start
testing AI well. It needs a small evidence loop that is honest enough to catch obvious self-
deception and practical enough to run every week.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, treat the minimum system as an evolving control system. Version the
cases, rubric, judge, model, prompts, policies, retrieval index, tools, and release thresholds
together. A score without provenance is not evidence.
