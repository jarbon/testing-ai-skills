---
name: tai-ch021-null-hypothesis-what-are-we-actually-testing
description: 'Apply chapter 21 of Testing AI, Null Hypothesis: What Are We Actually Testing?, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to null hypothesis: what are we actually testing?.'
---

# Null Hypothesis: What Are We Actually Testing?

Skill name: `tai-ch021-null-hypothesis-what-are-we-actually-testing`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

The null hypothesis is the boring default: assume the new AI system is not really better until
the evidence is strong enough to challenge that assumption.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

The null hypothesis helps teams define what a test is actually trying to learn before the
results arrive. That matters because people are excellent at explaining lucky results after the
fact.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to define the null hypothesis before running the evaluation. The null
hypothesis is the boring default claim: nothing meaningful changed, the new model is not better,
the new policy did not reduce harm, or the new agent did not improve task completion beyond
ordinary noise. An evaluation is the planned measurement used to challenge that claim.
