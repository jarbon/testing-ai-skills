# Section 24: Statistical Significance vs. Practical Significance

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** confidence engineer, statistical significance practical significance  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A difference can be statistically credible and still too small to matter. Confidence Engineers
need to explain both sides.

## Actions

- Define runnable checks that exercise confidence engineer and statistical significance practical significance.
- Set acceptable outcomes and blocker failures for confidence engineer and statistical significance practical significance before running the evaluation.
- Run representative cases for confidence engineer and statistical significance practical significance and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, statistical significance practical significance needed to reproduce work on Statistical Significance vs. Practical Significance.
- Report results for confidence engineer, statistical significance practical significance by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

This distinction is where the math hands the decision back to humans. Statistical significance asks whether a result looks unlikely to be pure noise. Practical significance asks whether anyone should care.

A tiny improvement can be statistically real and still useless. A risky failure reduction can be practically important even before the evidence is perfect. Good testing reports both the measurement and the meaning.

## Overview

Statistical significance asks whether a difference is likely to be more than random noise. Practical significance asks whether the difference matters enough to change a product decision.
For example, a huge sample can make a tiny improvement statistically significant, while users may never notice the change.

Statistical significance and practical significance answer different questions.

Statistical significance asks whether an observed difference is likely to be more than random sampling noise under a particular test. Practical significance asks whether the difference matters to users, the business, or the risk profile.

A result can be statistically significant and still not matter. Imagine an AI assistant improves from an average score of 8.10 to 8.12 across a very large sample, with p = 0.01. The improvement may be statistically credible. But it is tiny. If it increases latency or cost, the team may reasonably decide not to ship it.

A result can also be practically important even if more data is needed. Suppose a new prompt appears to reduce policy failures from 6% to 2%, but the sample is small and the confidence interval is wide. That change could matter a lot, but the team may need more samples before trusting the estimate.

This distinction is especially important in AI systems because averages can distract from risk. A small average improvement may not matter if rare catastrophic failures increase. A modest average improvement may matter greatly if it reduces a high-risk failure category.

Confidence Engineers should report both the evidence and the impact. The evidence includes metrics such as average score, confidence interval, p-value, sample size, and failure rate. The impact includes user experience, safety, cost, latency, compliance exposure, and business value.

A practical report might say: the score improvement is statistically significant, but the effect size is only +0.02 and latency increased by 30%, so the change is not recommended. Another report might say: the average score improved only slightly, but policy-boundary failures dropped from 6% to 2%, so the change is worth further validation.

The key is to avoid treating statistical significance as a shipping decision. It is an input to the decision. Product context decides whether the change matters.

Good Confidence Engineers help teams understand both questions: is the difference credible, and is the difference important? A strong release recommendation needs both.


## Examples

### Example: TunedSearch


> A new ranker improves average relevance by 0.02 points across 200,000 sampled queries.

That may be statistically significant. It may also be invisible to users, expensive to serve, and disruptive if it churns familiar navigational results.

Now look at a slice:

> "renew passport for child urgent appointment"

If that slice improves official-source ranking and reduces scammy appointment pages, the practical value may be large even if the global score barely moves. If the global score improves while this slice regresses, the release may be a bad trade.

Statistical significance asks whether the measured movement is likely real. Practical significance asks whether the movement matters enough to ship.


## Expert Notes

In production work, define the minimum meaningful effect before testing. If the team only cares about improvements of at least 0.3 points or a 20% reduction in policy failures, say so before looking at the data.

Expert teams also do not deploy a new model only because the improvement is statistically significant. A model change can introduce functional regressions, operational risk, latency changes, cost changes, compliance exposure, integration failures, monitoring gaps, or rollback complexity. Statistical significance says the measured difference is less likely to be noise under the test assumptions. It does not prove the change is safe to operate.
