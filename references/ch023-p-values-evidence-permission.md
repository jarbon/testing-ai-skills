# Section 23: P-Values: Evidence, Not Permission

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** p-value, p values evidence permission  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

P-values can support a comparison, but they do not decide whether a product is safe, useful, or
worth shipping.

## Actions

- Version B reduced automatic refunds from 18% of conversations to 14%, and the p-value is 0.003.
- Define runnable checks that exercise p-value and p values evidence permission.
- Set acceptable outcomes and blocker failures for p-value and p values evidence permission before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for p-value, p values evidence permission needed to reproduce work on P-Values: Evidence, Not Permission.
- Report results for p-value, p values evidence permission by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

A p-value is one of the easiest statistics to misuse, so it helps to start gently. Think of it as a surprise meter under a specific assumption.

The assumption is: "What if there were no real difference?" The p-value asks how surprising your observed result would be in that world. It does not tell you whether the product is good, safe, important, or ready to ship.

In experimental psychology, medicine, and other human-centered fields, p-values are often taught with the same warning: they are about evidence under a model, not truth by themselves. A small p-value says the observed result would be unusual if the null hypothesis were true. It does not prove causation, does not prove the result matters to users, and does not prove the measurement was unbiased.

## Overview

A p-value is evidence about surprise under a null assumption. It is not a probability that the new version is better, and it is not permission to ship.
For example, p = 0.02 says the observed difference would be fairly surprising if there were truly no difference under the test assumptions. It does not say the difference is important.

A p-value helps answer a specific question: if there were no real difference between two versions, how surprising would our observed result be under the test assumptions?

The "under the test assumptions" part is doing real work. It assumes the sample represents the population you care about, the scoring process is stable enough, the comparison was planned honestly, and the math test matches the kind of data you collected. If those assumptions are weak, the p-value can look precise while the conclusion is still shaky.

Suppose the old prompt has an average score of 7.8, the new prompt has an average score of 8.3, and the test returns p = 0.02. A Confidence-Engineer-friendly interpretation is: if the old and new prompts were actually equal in quality, a difference this large would be fairly unlikely under the assumptions of the test.

That is useful evidence. It suggests the observed difference may not be random noise.

But p-values are easy to misuse. A p-value of 0.02 does not mean there is a 98% chance the new prompt is better. It does not mean the improvement is important. It does not mean the test was well designed. It does not mean the system is safe to ship.

Many teams use p < 0.05 as a threshold for statistical significance. That convention can support a predeclared decision rule, but it is not a law of nature. A result at 0.049 and a result at 0.051 contain nearly the same statistical information. Evidence changes continuously; it does not jump from failure to truth at an arbitrary cutoff.

There is no universal ladder that turns a p-value range into labels such as "weak," "suggestive," or "very strong." Interpretation depends on the test plan, whether the assumptions fit, how many comparisons were attempted, the effect size, the uncertainty around that effect, and what prior evidence made the result plausible or surprising. A small p-value from an unplanned search across hundreds of variants may be less persuasive than a larger p-value from a well-powered, preregistered test with a meaningful effect.

P-values also say nothing about practical importance. With a very large sample, a tiny improvement can produce a small p-value. For example, an average score increasing from 8.10 to 8.12 may be statistically significant. Users may never notice. The improvement may not justify higher latency, higher cost, or increased risk.

A better quality report puts the p-value in context. It includes the effect size, which tells how large the improvement is. It includes a confidence interval, which shows uncertainty around the improvement. It includes failure rates, which show whether bad outputs became more or less common. It includes category breakdowns, because an overall improvement can hide a regression in a high-risk segment.


## Worked Example

Suppose you run the same 20 evaluation cases through the old and new versions. Ignore ties for this simple example. A reviewer prefers the new version 15 times and the old version 5 times.

The null assumption is boring: if the versions are equal, each case is like a coin flip. The new version should win about half the time.

The p-value asks: under that coin-flip assumption, how often would we see a result at least this lopsided?

```text
total_possible_outcomes = 2^20 = 1,048,576

outcomes_with_15_or_more_new_wins =
  C(20,15) + C(20,16) + C(20,17) + C(20,18) + C(20,19) + C(20,20)

outcomes_with_15_or_more_new_wins =
  15,504 + 4,845 + 1,140 + 190 + 20 + 1 = 21,700

one_sided_p = 21,700 / 1,048,576 = about 0.0207
two_sided_p = 2 * 0.0207 = about 0.0414
```

If the comparison was planned as "new must beat old," the one-sided p-value is about 0.021. If the honest question was "did either version differ," the two-sided p-value is about 0.041. Either way, the result is evidence that the new version may be better under this preference setup. It is still not permission to ship. You still need effect size, failure review, safety checks, and slice analysis.

The best short rule is this: a p-value can tell you whether a difference is surprising; it cannot tell you whether users will care.

Use p-values as evidence, not permission. They belong in the report, but they should not be the headline and they should never replace product judgment.


## Examples

### Example: CartCare Chatbot

> We changed the refund policy prompt. Did the new version improve refund handling?

The dashboard looks exciting. Version B reduced automatic refunds from 18% of conversations to 14%, and the p-value is 0.003. Someone will be tempted to say, "Ship it. The result is statistically significant."

Slow down.

The p-value says the refund-rate change is unlikely to be ordinary sampling noise if the old and new systems were actually the same. It does not say the change is good. It does not say users are happier. It does not say the new policy is fair. It does not say high-risk cases improved.

Look at the slices before celebrating:

- Low-dollar refunds under $20 went down slightly, with no change in complaints.
- Grocery substitutions between $20 and $100 mostly shifted from refund to store credit.
- High-value orders over $3,000 produced fewer automatic refunds, but escalations doubled.
- Angry-customer conversations became longer and more expensive to handle.
- Social-media-risk transcripts increased because the bot sounded more defensive.
- Fraud-like cases improved, but legitimate catering and holiday orders got stuck.

The result may still be useful. Maybe Version B is better at stopping abuse. Maybe it saves money without hurting normal customers. But the p-value is only evidence that something changed. The release decision depends on whether the change matches the product's values, risk tolerance, customer promises, and escalation capacity.

The regression question is not whether CartCare produced a small p-value. It is whether the statistically visible change is a product-quality improvement rather than a cheaper way to create different failures.

## Expert Notes

Expert reports treat p-values as continuous evidence, not as a yes/no permission slip. A useful report pairs the p-value with the other facts needed to make a responsible decision:

- [Effect size](https://en.wikipedia.org/wiki/Effect_size) means how large the observed change was. A tiny improvement can be statistically visible and still irrelevant to users.
- [Confidence intervals](https://en.wikipedia.org/wiki/Confidence_interval) show the uncertainty around the estimated change. They help the reader see whether the effect might be large, small, or practically zero.
- [Sample size](https://en.wikipedia.org/wiki/Sample_size_determination) is the number of cases, users, prompts, conversations, or traces measured. Larger samples can detect smaller differences, but they do not fix biased sampling.
- Assumptions are the conditions the statistical test relies on, such as independence, stable scoring, comparable groups, and a metric that matches the data type. If the assumptions are weak, the p-value can look precise while the conclusion is fragile.
- Practical risk is the product consequence of being wrong: user harm, privacy exposure, safety failure, support cost, lost trust, latency, or business damage.
- The original test plan is the evaluation design written before the run: what would be measured, how long the test would run, which slices mattered, and what decision threshold would be used.
- [Multiplicity corrections](https://en.wikipedia.org/wiki/Multiple_comparisons_problem) adjust for the fact that trying many metrics, slices, prompts, or model variants increases the chance of finding one exciting result by luck.
- Prior expectations are what the team reasonably believed before the test, based on earlier evidence, product knowledge, known risks, and the plausibility of the claimed effect.

Expert reports also watch for [p-hacking](https://en.wikipedia.org/wiki/Data_dredging), repeated peeking, and [multiple comparisons](https://en.wikipedia.org/wiki/Multiple_comparisons_problem). P-hacking means trying many analysis paths until one looks good. Repeated peeking means checking results again and again during a run and stopping when the number finally looks favorable. Multiple comparisons means that the more things you test, the more likely noise will create a false winner. All three can create false confidence.
