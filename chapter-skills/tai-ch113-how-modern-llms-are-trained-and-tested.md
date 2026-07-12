---
name: tai-ch113-how-modern-llms-are-trained-and-tested
description: 'Apply chapter 113 of Testing AI, How Modern LLMs Are Trained and Tested, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to how modern llms are trained and tested.'
---

# How Modern LLMs Are Trained and Tested

Skill name: `tai-ch113-how-modern-llms-are-trained-and-tested`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

To test LLMs well, builders need a practical model of how they are made.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Modern LLMs usually pass through several stages: large-scale data collection, filtering,
tokenization, pretraining, supervised fine-tuning, preference tuning such as RLHF (reinforcement
learning from human feedback) or RLAIF (reinforcement learning from AI feedback), safety tuning,
benchmark evaluation, red-team testing, deployment, and monitoring. Each stage creates possible
quality and security failures.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, map observed failures to the model lifecycle. Ask whether the issue is
caused by data, labels, tuning, retrieval, prompting, tools, decoding, safety policy, or product
workflow. Useful LLM quality work often starts by naming the layer that can actually be changed.
