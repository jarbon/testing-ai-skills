# Section 71: Anti-Patterns: The Boolean Pass/Fail Trap

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** boolean pass/fail, boolean pass fail trap  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A single green or red result can hide the very uncertainty builders need to explain.

## Actions

- Keep boolean blockers for truly binary constraints, but report ordinary quality as a distribution.
- Use severity weighting, confidence intervals, slice minimums, and repeated runs so the release decision reflects observed behavior instead of one crisp label.
- Define runnable checks that exercise boolean pass/fail and boolean pass fail trap.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for boolean pass/fail, boolean pass fail trap needed to reproduce work on Anti-Patterns: The Boolean Pass/Fail Trap.
- Report results for boolean pass/fail, boolean pass fail trap by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Boolean pass/fail is one of the oldest instincts in testing. It works well when the system is deterministic, idempotent, the expected result is precise, and one run tells you the truth.
AI systems break that assumption. A chatbot, ranking model, agent, or generated-code assistant can produce acceptable variation, marginal variation, and severe failure from similar inputs. Red or green alone collapses that reality into a false certainty.

The mistake I see teams make is thinking that pass/fail is objective just because it is crisp. In non-deterministic systems, a boolean result often means someone ignored variance, severity, sampling error, and acceptable alternatives.
A model can pass 90 examples and still be unsafe in one high-risk category. It can fail one wording check while producing a perfectly useful answer. It can pass once and fail on the next run with the same prompt. The boolean is not enough.
The better question is not simply, "Did it pass?" The better question is, "What behavior did we observe, how often did it occur, how severe were the failures, and how confident are we in the estimate?"
Pass/fail still has a place. Privacy leaks, unsafe tool execution, policy violations, and schema-breaking outputs may be hard blockers. But those blockers should sit inside a richer quality model rather than pretending every judgment is a light switch.
For AI, passed often means passed within an acceptable risk envelope. That envelope can include minimum score, maximum severe-failure rate, confidence interval, slice thresholds, latency, and human-review load.
The practical failure mode is using boolean numbers because they are easy to count, then acting as if they are the whole truth.

## Expert Notes

Keep boolean blockers for truly binary constraints, but report ordinary quality as a distribution. Use severity weighting, confidence intervals, slice minimums, and repeated runs so the release decision reflects observed behavior instead of one crisp label.
