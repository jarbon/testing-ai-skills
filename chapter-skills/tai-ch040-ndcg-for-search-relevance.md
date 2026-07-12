---
name: tai-ch040-ndcg-for-search-relevance
description: 'Apply chapter 40 of Testing AI, NDCG for Search Relevance, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ndcg for search relevance.'
---

# NDCG for Search Relevance

Skill name: `tai-ch040-ndcg-for-search-relevance`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

NDCG helps Confidence Engineers measure whether the most relevant search and ranking results
appear where users will actually see them.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

NDCG, or normalized discounted cumulative gain, is a metric for ranked search and relevance
results. It rewards relevant results near the top of the list more than relevant results buried
lower down. For example, a search engine that puts the best answer first should score better
than one that puts the same answer on page two, even if both technically returned it.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Choose the cutoff deliberately, such as NDCG@5 or NDCG@10, based on how many results users
actually inspect. Watch for label quality, position bias in click data, query mix drift, and
improvements that help common queries while hurting rare critical queries.
