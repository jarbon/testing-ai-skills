---
name: tai-ch060-operational-impact-on-relevance-and-ai-quality
description: 'Apply chapter 60 of Testing AI, Operational Impact on Relevance and AI Quality, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to operational impact on relevance and ai quality.'
---

# Operational Impact on Relevance and AI Quality

Skill name: `tai-ch060-operational-impact-on-relevance-and-ai-quality`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Quality is what the user experiences at the end of the full system path, not what one isolated
API reports before production reality gets involved.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Operational impact is the part of quality that many evals accidentally hide. A model, ranker,
retriever, or API can score well in isolation while the real product fails because the request
timed out, a machine rebooted, a cache went stale, a retry masked an error, or a downstream
service returned an empty state.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to treat operational failures as part of the outcome distribution. Assign
explicit scores to empty results, timeouts, partial outputs, stale fallbacks, degraded modes,
failed tool calls, and UI delivery failures. Separate component metrics from end-to-end metrics,
but make the release decision from the user-visible evidence.
