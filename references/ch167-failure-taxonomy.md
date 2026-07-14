# Section 167: Failure Taxonomy for AI Systems

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** RAG, confidence engineer, failure taxonomy  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A shared failure language helps teams cluster problems instead of drowning in disconnected bug
reports.

## Actions

- Start with factual failures: wrong facts, invented facts, stale facts, missing required facts, or unsupported claims.
- Define runnable checks that exercise RAG, confidence engineer, and failure taxonomy.
- Set acceptable outcomes and blocker failures for RAG, confidence engineer, and failure taxonomy before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, confidence engineer, failure taxonomy needed to reproduce work on Failure Taxonomy for AI Systems.
- Report results for RAG, confidence engineer, failure taxonomy by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

A failure taxonomy gives names to the ways AI systems fail. It helps Confidence Engineers, engineers, product teams, and executives talk about patterns.
Without a taxonomy, every failure becomes a one-off anecdote. With a taxonomy, failures can be counted, clustered, prioritized, and turned into regression coverage.


Start with factual failures: wrong facts, invented facts, stale facts, missing required facts, or unsupported claims.
Add grounding failures: the answer is not supported by retrieved context, citations point to the wrong source, or the model uses general knowledge when it should use product evidence.
Add retrieval failures: missing documents, stale documents, irrelevant chunks, poor ranking, bad chunking, or context overflow.
Add tool-use failures: wrong tool, wrong arguments, missing confirmation, unsafe side effect, ignored tool error, or unnecessary repeated calls.
Add policy and safety failures: wrong refusal, missing refusal, unsafe advice, policy bypass, or harmful compliance.
Add privacy and security failures: data leakage, cross-tenant exposure, secret exposure, prompt injection, overlogging, or weak access control.
Add user-experience failures: confusing answer, wrong tone, excessive verbosity, unhelpful escalation, inaccessible output, or awkward latency.
Add operational failures: cost blowup, timeout, retry loop, provider outage, judge failure, monitoring gap, or rollback failure.
The taxonomy should be practical. It should help route work to the right owner and measure whether fixes improve the distribution.

## Applied Example

### Example: CartCare Chatbot


> The bot tells a customer their ice cream is arriving in 10 minutes, but the driver canceled 20 minutes ago.

Classify the failure before fixing it. Was it stale retrieval, tool failure, memory error, hallucination, bad policy, missing escalation, or misleading tone? Different root causes require different tests.

A taxonomy keeps the team from treating every failure as "the model was bad."


## Expert Notes

Failure taxonomy should connect to severity, affected slices, root-cause hypotheses, owners, regression cases, and incident metrics.
