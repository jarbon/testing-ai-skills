# Section 41: Stop Chasing High-Water Marks

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** variance, high-water mark, RAG, stop chasing high water marks  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

If you rerun a noisy evaluation enough times, variance will eventually hand you a beautiful
score. That does not make the system better.

## Actions

- Track every run, predefine stopping rules, preserve holdout sets, and estimate performance from the full run distribution rather than the maximum observed score.
- Define runnable checks that exercise variance, high-water mark, and RAG.
- Set acceptable outcomes and blocker failures for variance, high-water mark, and RAG before running the evaluation.

## Evidence to Produce

- Track every run, predefine stopping rules, preserve holdout sets, and estimate performance from the full run distribution rather than the maximum observed score.
- Preserve the inputs, versions, configurations, raw outcomes, and results for variance, high-water mark, RAG, stop chasing high water marks needed to reproduce work on Stop Chasing High-Water Marks.
- Report results for variance, high-water mark, RAG, stop chasing high water marks by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Non-deterministic systems produce noisy measurements. If you keep rerunning the same evaluation and report only the best result, you are not measuring quality. You are selecting a lucky high-water mark.
For example, a prompt may average 8.0 across repeated runs but occasionally score 8.6 by chance. Reporting the 8.6 as the truth is wrong and will mislead the team.

This failure mode is common because it feels productive. The team reruns the eval, tweaks a prompt, changes a hyperparameter, reruns again, changes a judge instruction, reruns again, and eventually sees a new best score. Everyone wants to believe the high score is progress.
Sometimes it is progress. Often it is variance. Non-deterministic systems, sampled datasets, LLM judges, and small evaluation sets all create noise. The maximum observed result across many tries is biased upward.
High-water marks are especially dangerous when the team does not log every run. If only the best run survives, the evidence trail disappears. The team forgets how many attempts failed to reproduce the win.
The fix is to report all runs, not just the best run. Show the mean across runs, the spread, the confidence interval, and whether the improvement reproduces on a fresh holdout set.
A new high score should be treated as a lead, not proof. It earns a confirmation run. It does not earn a release by itself.


The same rule applies to cherry-picked examples. A stunning generated answer shows what the system can do. It does not show how often the system does it.

## Expert Notes

At scale, treat repeated evaluation as a multiple-comparisons problem. Track every run, predefine stopping rules, preserve holdout sets, and estimate performance from the full run distribution rather than the maximum observed score.
