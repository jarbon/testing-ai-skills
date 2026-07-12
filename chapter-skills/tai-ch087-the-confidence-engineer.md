---
name: tai-ch087-the-confidence-engineer
description: 'Apply chapter 87 of Testing AI, The Confidence Engineer, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to the confidence engineer.'
---

# The Confidence Engineer

Skill name: `tai-ch087-the-confidence-engineer`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The confidence engineer designs evidence systems for AI products: measuring behavior, using AI
to test AI, and explaining whether the product is safe enough, useful enough, and reliable
enough to ship.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

This is where the threads come together.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The confidence engineer becomes the architect of validation. They design the measurement layer
that lets AI-generated products ship quickly without pretending uncertainty disappeared. The
title is new-ish. The need is not. Every serious AI product needs someone accountable for the
evidence that says whether the system is getting better, getting safer, and getting more
trustworthy in the real world.
