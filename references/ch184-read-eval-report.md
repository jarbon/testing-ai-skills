# Section 184: Appendix: How to Read an AI Eval Report

**Book location:** Companion Reference, Testing AI  
**Use when:** read eval report  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Most eval reports look more precise than they are. Learn where the uncertainty is hiding.

## Actions

- Review eval reports like experimental evidence.
- Ask about provenance, holdouts, multiple comparisons, judge drift, dataset drift, effect size, and practical significance.
- Define runnable checks that exercise read eval report.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for read eval report needed to reproduce work on Appendix: How to Read an AI Eval Report.
- Report results for read eval report by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

An AI eval report is a decision artifact. It should help a reader understand what was tested, how it was judged, how uncertain the result is, and what decision the evidence supports.
A weak report gives a score. A strong report explains the sample, the metric, the slices, the failures, the confidence, the cost, and the risk.

Start with the sample. How many examples were tested? Where did they come from? Were they production traces, synthetic cases, red-team prompts, golden cases, or benchmark tasks? What important cases are missing?
Then inspect the scoring. Is there a rubric? Are hard blockers separated from soft scores? Is the judge an LLM, a human, a deterministic assertion, or a mix? Was the judge calibrated?
Look at uncertainty. Does the report show confidence intervals, repeated-run variance, sample size, or statistical significance? If it shows only one number, be skeptical.
Look for slices. Overall quality can improve while one language, user group, workflow, or high-risk category regresses. The slices are often where the truth lives.
Look at severe failures. Averages can hide rare catastrophic behavior. Count and inspect privacy failures, safety failures, unsupported actions, and policy violations.
Look at business tradeoffs. Did quality improve at the cost of latency, tokens, escalation, or provider risk? Does the improvement matter enough to justify that cost?
Finally, look for a decision. A report should say what the evidence supports: ship, hold, canary, rollback, or run a larger eval. If the report avoids a decision, it may be analysis theater.

## Applied Example

### Example: TunedSearch: The 1.2% Win Hid a 19% News Regression
> "The new ranker improves relevance by 1.2%. Recommendation: launch globally."

The headline is true. The appendix tells a different story. Navigational and evergreen queries improved enough to lift the average, but breaking-news queries regressed by 19%. Forty-seven timed-out runs were excluded. The judge model changed halfway through the experiment, p95 latency increased from 820 milliseconds to 1.4 seconds, and the confidence interval for the overall gain barely excludes zero.

The affected queries include "AI lab CEO resigns today" and "new model API outage status." Those are exactly the cases where users need current evidence rather than a generally relevant page.

A careful reviewer does not argue with the 1.2%. They ask what population produced it, which failures disappeared from the denominator, whether the runs are comparable, which slices paid for the gain, and whether the user-visible benefit justifies the added latency. The report should make that challenge possible before the launch meeting becomes a celebration.

## Expert Notes

Review eval reports like experimental evidence. Ask about provenance, holdouts, multiple comparisons, judge drift, dataset drift, effect size, and practical significance.
