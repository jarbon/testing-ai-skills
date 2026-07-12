---
name: tai-ch076-anti-patterns-the-whack-a-mole-tuning-trap
description: 'Apply chapter 76 of Testing AI, Anti-Patterns: The Whack-a-Mole Tuning Trap, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to anti-patterns: the whack-a-mole tuning trap.'
---

# Anti-Patterns: The Whack-a-Mole Tuning Trap

Skill name: `tai-ch076-anti-patterns-the-whack-a-mole-tuning-trap`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Prompt patches and fine-tunes can remove one visible failure while creating quieter failures
nearby.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Early AI teams often respond to a bad example by patching the prompt, adding a rule, changing
retrieval, or fine-tuning the model to avoid that mistake. That can work, but it can also become
whack-a-mole. The embarrassing failure disappears, and new failures appear in adjacent
categories, languages, tones, or tool paths.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, every tuning change should have a blast-radius eval: original failures, adjacent
prompts, benign counterexamples, slice checks, cost and latency metrics, and holdout
confirmation.
