# Section 77: Anti-Patterns: The One-Run Demo Fallacy

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** RAG, one-run demo, demo fallacy  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A beautiful demo proves what the system can do once, not what it will do reliably.

## Actions

- Use fixed prompts, documented model settings, versioned tools, recorded traces, and enough samples to estimate behavior.
- Define runnable checks that exercise RAG, one-run demo, and demo fallacy.
- Set acceptable outcomes and blocker failures for RAG, one-run demo, and demo fallacy before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, one-run demo, demo fallacy needed to reproduce work on Anti-Patterns: The One-Run Demo Fallacy.
- Report results for RAG, one-run demo, demo fallacy by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

One-run demos are powerful. They make AI systems feel magical. They get you funding. They also create false confidence.
With non-deterministic systems, a single great output can be a lucky sample. It does not show average quality, failure rate, tail risk, or behavior under real traffic.

The demo fallacy is especially dangerous because it is emotionally persuasive. A live audience sees the system succeed and feels the future arrive.
But the Confidence Engineer's job is to ask how often it succeeds, where it fails, how bad the failures are, and whether the demo path was cherry-picked.
Retries make the problem worse. If someone runs the same prompt five times and shows the best one, the demo is not an evaluation. It is selection.
The antidote is repeated trials and locked conditions. Use fixed prompts, documented model settings, versioned tools, recorded traces, and enough samples to estimate behavior.
Demo examples are still useful. They can reveal capability and teach stakeholders what the system is meant to do. They should be labeled as demonstrations, not evidence of release readiness.
The thing to watch for is promoting a system because it succeeded once in front of the right people.

## Expert Notes

When the system matters, separate capability demos, smoke tests, benchmark runs, and release evals. A demo can inspire investment, but only repeated, sampled, versioned evidence should support shipping.
