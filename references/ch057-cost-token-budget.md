# Section 57: Cost and Token Budget Testing

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** latency, RAG, token budget, cost token budget  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI quality includes whether the system can afford to behave that way.

## Actions

- Track input tokens, output tokens, retrieved tokens, tool-call tokens, judge tokens, retry tokens, and total cost per task.
- Watch p95 and p99, not only averages.
- Measure quality per dollar by segment.

## Evidence to Produce

- Track input tokens, output tokens, retrieved tokens, tool-call tokens, judge tokens, retry tokens, and total cost per task.
- Preserve the inputs, versions, configurations, raw outcomes, and results for latency, RAG, token budget, cost token budget needed to reproduce work on Cost and Token Budget Testing.
- Report results for latency, RAG, token budget, cost token budget by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Cost and token budget testing measures token growth, runaway loops, repeated tool calls, cache misses, p95 and p99 cost, and quality per dollar. It matters because AI systems can fail economically before they fail functionally.
For example, a RAG answer may be correct but include 40 irrelevant chunks, double latency, and cost ten times more than needed.

Track input tokens, output tokens, retrieved tokens, tool-call tokens, judge tokens, retry tokens, and total cost per task.
Percentiles show the tail. p95 means 95% of requests cost less than that value, and the worst 5% cost more. p99 means 99% cost less than that value, and the worst 1% cost more. Watch p95 and p99, not only averages. Rare long prompts, huge documents, retry loops, and multi-tool traces can dominate monthly spend.
Runaway loops are quality failures. An agent that calls the same tool repeatedly, expands context unnecessarily, or retries without new information is broken even if it eventually answers.
Cache behavior should be tested. A prompt or retrieval cache that misses unexpectedly can turn a cheap workflow into an expensive one.
Cost should be reported with quality. A model that improves score by 0.1 while tripling cost may not be better for the product.
Measure quality per dollar by segment. High-risk cases may justify higher cost. Low-risk cases may need a cheaper route.


Budget tests should include load and concurrency. Token cost and latency often get worse under real traffic patterns.
Spend intelligence where it creates value; indiscriminate cost cutting can make the system worse.

## From the Field: The Experiment Had a Cost Too

I have seen this play out in model experimentation too. I will not name names, but several AI engineers I knew would run all their experiments in a `while(true)` loop, barely changing hyperparameters or training weights, hunting for tiny gains. And they found some. The uncomfortable question was whether the gain was worth the compute cost.

In a search engine, you can argue that even a very small relevance improvement is valuable. Sometimes it is. But the cost was not only machine time. Those experiment loops delayed other engineers' work, added latency to the shared experiment pipeline, and created piles of post-analysis data that slowed everyone down. Later, after a few back-hallway conversations, those engineers ran fewer experiments. That was not anti-science. That was quality engineering. The experiment itself had to justify its cost, its queue impact, and its analysis burden.

## Quick Applied Example

### Example: BugPilot


> "Find why checkout totals are sometimes off by one cent."

A careless agent reads the whole repo, loads every pricing document, asks three subagents to summarize the same files, retries after vague tool errors, and spends 400,000 tokens before changing one rounding function.

A better agent starts with the failing test, inspects currency helpers, checks tax and discount boundaries, reads only the relevant pricing docs, and stops when the evidence is enough.

Score cost as part of quality:

- tokens per successful fix
- tool calls per fix
- duplicate retrievals
- retries caused by poor planning
- context growth over the task
- whether extra cost bought better evidence

An agent that is correct but wildly wasteful may be a bad production product.


## Expert Notes

Cost testing should track token budgets by span, cache hit rate, retry count, tool-call count, model mix, latency percentiles, queue behavior, and marginal quality per dollar by task category.
