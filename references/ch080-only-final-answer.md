# Section 80: Anti-Patterns: Testing Only the Final Answer

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** RAG, only final answer  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

For RAG and agents, the visible answer is only the last step in a larger system.

## Actions

- Inspect the path: retrieved documents, tool calls, intermediate observations, decisions, and final output.
- Score retrieval, planning, tool choice, arguments, permission boundaries, recovery, final answer, and side effects separately.
- Define runnable checks that exercise RAG and only final answer.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, only final answer needed to reproduce work on Anti-Patterns: Testing Only the Final Answer.
- Report results for RAG, only final answer by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Final-answer testing asks whether the user-facing response looks good. That matters, but it is not enough for systems that retrieve, plan, call tools, update state, or cite sources.
The final answer can be right for the wrong reason, or wrong because an earlier hidden step failed.

In RAG systems, failure may come from retrieval, ranking, stale documents, chunking, context injection, citation mapping, or answer synthesis. Looking only at the final text hides those causes.
In agents, failure may come from plan quality, tool choice, tool arguments, permission checks, intermediate state, recovery behavior, or side effects.
A final answer can sound polished while using the wrong source. An agent can complete a task after skipping a required confirmation. A citation can point to a document that does not support the claim.
The better pattern is trajectory scoring. Inspect the path: retrieved documents, tool calls, intermediate observations, decisions, and final output.
This makes debugging possible. If retrieval failed, changing the prompt may not help. If the tool contract failed, changing the model may not help. If the judge only sees the final answer, it may reward a lucky outcome.
The practical failure mode is grading the visible sentence while ignoring the system that produced it.

## Expert Notes

In a real release review, store traces as eval artifacts. Score retrieval, planning, tool choice, arguments, permission boundaries, recovery, final answer, and side effects separately.
