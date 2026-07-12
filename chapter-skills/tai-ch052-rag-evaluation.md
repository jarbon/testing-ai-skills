---
name: tai-ch052-rag-evaluation
description: 'Apply chapter 52 of Testing AI, RAG Evaluation, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to rag evaluation.'
---

# RAG Evaluation

Skill name: `tai-ch052-rag-evaluation`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

RAG systems fail in two places: what they retrieve and what they say with it.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Retrieval-augmented generation needs its own evaluation strategy because answer quality depends
on both the retriever and the generator. A model can hallucinate from weak context, ignore good
context, or confidently answer when no supporting document exists. For example, a policy
assistant may retrieve the right document but the wrong chunk, cite a stale policy, or answer
from a nearby paragraph that does not actually support the claim.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In production work, separate retriever metrics from generator metrics. Track context precision,
context recall, retrieval hit rate, chunk freshness, reranker quality, answer faithfulness,
citation support, abstention behavior, and failure attribution by document source and query
class.
