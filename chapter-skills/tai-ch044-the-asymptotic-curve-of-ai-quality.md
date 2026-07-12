---
name: tai-ch044-the-asymptotic-curve-of-ai-quality
description: 'Apply chapter 44 of Testing AI, The Asymptotic Curve of AI Quality, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to the asymptotic curve of ai quality.'
---

# The Asymptotic Curve of AI Quality

Skill name: `tai-ch044-the-asymptotic-curve-of-ai-quality`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

AI quality usually improves quickly at first, then gets harder, slower, and never reaches
perfection.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Most AI systems improve in a familiar shape. Early changes produce obvious wins: better prompts,
cleaner retrieval, stronger rubrics, fewer broken tool calls, better data, and simple safety
filters. The quality curve rises quickly.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Plot quality over time with uncertainty bands, not just point estimates. Look for diminishing
returns, plateaus, slice-specific ceilings, and architecture-limited performance. The asymptote
is not an excuse to stop testing. It is evidence that the next improvement may require a
different model, data source, workflow, containment layer, or product boundary.
