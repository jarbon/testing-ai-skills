---
name: tai-ch015-sampling-one-run-tells-you-almost-nothing
description: 'Apply chapter 15 of Testing AI, Sampling: One Run Tells You Almost Nothing, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to sampling: one run tells you almost nothing.'
---

# Sampling: One Run Tells You Almost Nothing

Skill name: `tai-ch015-sampling-one-run-tells-you-almost-nothing`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

For unpredictable systems, a single output is an anecdote. A sample is the beginning of
evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Sampling is how Confidence Engineers turn scattered observations into evidence. One output is an
anecdote. A sample lets you estimate how the system behaves across a wider set of users, inputs,
and conditions. For example, one good answer does not prove a chatbot is good, and one bad
answer does not prove it is broken everywhere. A sample shows how common each outcome is.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Expert sampling plans specify the population, sampling frame, inclusion criteria, exclusions,
randomization method, known bias, and input-variation strategy. If the sample only includes easy
happy-path prompts, the confidence interval describes easy happy-path prompts, not the product.
Track slices for typos, dialects, accents, code-switching, non-native phrasing, messy intent,
and other realistic input forms so the team can see where quality actually breaks.
