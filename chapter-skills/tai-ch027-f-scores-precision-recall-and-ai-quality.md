---
name: tai-ch027-f-scores-precision-recall-and-ai-quality
description: 'Apply chapter 27 of Testing AI, F-Scores, Precision, Recall, and AI Quality, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to f-scores, precision, recall, and ai quality.'
---

# F-Scores, Precision, Recall, and AI Quality

Skill name: `tai-ch027-f-scores-precision-recall-and-ai-quality`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

F-scores help Confidence Engineers reason about the tradeoff between catching the right things
and avoiding false alarms.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

F-scores are most useful when the system is deciding whether something belongs in a category:
relevant or not relevant, unsafe or safe, hallucinated or grounded, should escalate or should
answer, bug or not bug.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Decide whether F1 is the right F-score. F1 weights precision and recall equally. F-beta scores
let you weight recall more heavily than precision, or precision more heavily than recall.
