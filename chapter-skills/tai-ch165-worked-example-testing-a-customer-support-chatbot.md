---
name: tai-ch165-worked-example-testing-a-customer-support-chatbot
description: 'Apply chapter 165 of Testing AI, Worked Example: Testing a Customer-Support Chatbot, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to worked example: testing a customer-support chatbot.'
---

# Worked Example: Testing a Customer-Support Chatbot

Skill name: `tai-ch165-worked-example-testing-a-customer-support-chatbot`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A full AI quality workflow shows how the pieces of the book fit together.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A worked example turns concepts into practice. Imagine a customer-support chatbot that answers
billing, refund, account, and policy questions. The team wants to upgrade the model and prompt.
The question is not whether one answer looks good. The question is whether the new system should
ship.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, the worked example becomes a repeatable release playbook: sample, score, calibrate,
slice, cluster, decide, monitor, and feed production failures back into the eval suite.
