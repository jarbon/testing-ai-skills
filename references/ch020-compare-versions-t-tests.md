# Section 20: Comparing Versions with t-tests

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** t-test, p-value, statistical significance, paired data, compare prompt or model versions  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A t-test can help Confidence Engineers decide whether a difference in average scores is likely
to be real or just sampling noise.

## Actions

- Use judgment and risk analysis to decide whether the improvement is safe and worth shipping.
- Start with the data-generating process, not a favorite test.
- Ask what the experimental unit is, whether the same units saw both versions, what kind of outcome was measured, and which observations can influence one another.
- Compare versions within prompt, summarize or model the repeated runs, and calculate uncertainty at the prompt or cluster level.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for t-test, p-value, statistical significance, paired data needed to reproduce work on Comparing Versions with t-tests.
- Report results for t-test, p-value, statistical significance, paired data by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

A t-test can sound like heavy statistics, but the builder's intuition is straightforward: when one version looks better, ask whether the gap is big compared with the natural noise in the scores.

The test is not trying to replace judgment. It is a structured way to ask, "Did the new version win by enough, across enough comparable cases, that we should take the improvement seriously?"



## Overview

A t-test helps compare average scores between versions while accounting for variation and sample size. It asks whether an observed average difference is larger than you would expect from noise alone under the test assumptions.
For example, if a new prompt scores 0.5 points higher on average, a t-test helps decide whether that improvement is likely to be real enough to discuss seriously.

This is related to pairwise comparison, but it is not the same thing. Pairwise comparison asks a judge which output is better: A, B, or tie. A paired t-test starts with numeric scores for the same cases under two versions, then asks whether the average score difference is large compared with the spread of those differences. Pairwise comparison gives preference evidence. A t-test gives average-score evidence.

When teams improve prompts, models, ranking systems, or AI workflows, they need to know whether the new version is actually better.

Suppose the old prompt has an average score of 7.8 and the new prompt has an average score of 8.3. The new prompt looks better. But a Confidence Engineer should ask: is that difference meaningful, or did the new version happen to get an easier sample?

A t-test helps answer that question for average numeric scores. It considers the difference between the averages, the amount of variation in the scores, and the number of samples. A large difference with low variation and many samples is more convincing than a small difference with high variation and few samples.

T-tests are useful when outputs are scored numerically, such as with a 0-10 quality rubric. They are commonly used to compare an old prompt against a new prompt, one model against another, or one ranking algorithm against an experimental version.

For product testing, a paired t-test is often the best pattern. In a paired setup, you run the same test cases against both versions. Each case gets two scores: old and new. Then you compare the per-case differences.

This matters because some cases are harder than others. If Version A gets a difficult sample and Version B gets an easy sample, a simple comparison may be misleading. Pairing controls for case difficulty. Case 1 might improve from 7 to 8, Case 2 might stay at 9, and Case 3 might improve from 6 to 8. The test evaluates those differences directly.

A t-test is not a release gate by itself. It focuses on average scores. Many product risks live in the tails. A new model may improve average quality while increasing rare policy failures. A prompt may sound better while occasionally leaking sensitive information. A ranking change may improve overall relevance while hurting one important user segment.

That is why t-tests should be used alongside failure rates, confidence intervals, worst-case review, stratified reporting, and hard safety checks.

A good report might say: the new version improved average score by 0.5 points; the paired t-test produced p = 0.005; the 95% confidence interval for the improvement was +0.2 to +0.8; failure rate did not increase; no critical failures were observed.

That gives the team a stronger basis for decision-making than "the new version looked better in a few examples." Use t-tests to compare average quality. Use judgment and risk analysis to decide whether the improvement is safe and worth shipping.

## Choosing the Right Statistical Test

Start with the data-generating process, not a favorite test. Ask what the experimental unit is, whether the same units saw both versions, what kind of outcome was measured, and which observations can influence one another.

| Situation | Useful starting point | What to watch |
|---|---|---|
| Same prompts or users run through A and B; numeric score | [Paired t-test](https://en.wikipedia.org/wiki/Student%27s_t-test#Dependent_t-test_for_paired_samples) on per-unit differences | Inspect outliers and the distribution of differences; report the paired confidence interval. |
| Different prompts or users assigned to A and B; numeric score | [Welch's t-test](https://en.wikipedia.org/wiki/Welch%27s_t-test) for independent samples | Do not assume equal variance; random assignment matters more than the test name. |
| Same cases; binary pass/fail | [McNemar's test](https://en.wikipedia.org/wiki/McNemar%27s_test) | Only the cases where A and B disagree drive the result. |
| Independent categorical counts | [Chi-squared test](https://en.wikipedia.org/wiki/Chi-squared_test), or [Fisher's exact test](https://en.wikipedia.org/wiki/Fisher%27s_exact_test) for small counts | Preserve the actual categories; do not convert every outcome into an average. |
| Ordinal ratings such as poor/fair/good or a coarse 0-10 rubric | [Wilcoxon signed-rank test](https://en.wikipedia.org/wiki/Wilcoxon_signed-rank_test) for paired data; [Mann-Whitney U test](https://en.wikipedia.org/wiki/Mann%E2%80%93Whitney_U_test) for independent data; [ordinal regression](https://en.wikipedia.org/wiki/Ordinal_regression) when practical | Ordinal steps are ordered, but the distance from 6 to 7 may not equal the distance from 8 to 9. |
| Skewed metrics, strange score distributions, or a custom product metric | [Bootstrap confidence interval](https://en.wikipedia.org/wiki/Bootstrapping_%28statistics%29) or [permutation test](https://en.wikipedia.org/wiki/Permutation_test) | Resample or permute at the experimental-unit level, not at the output-row level. |
| Many runs per prompt, conversations per user, or prompts grouped by topic | [Mixed-effects model](https://en.wikipedia.org/wiki/Mixed_model) or [hierarchical model](https://en.wikipedia.org/wiki/Bayesian_hierarchical_model); [cluster bootstrap](https://en.wikipedia.org/wiki/Bootstrapping_%28statistics%29) or [cluster permutation](https://en.wikipedia.org/wiki/Permutation_test) | Account for within-prompt, within-user, or within-topic correlation. |

Bootstrap methods estimate uncertainty by resampling observed experimental units. Permutation tests ask how unusual the observed difference would be if the version labels were exchangeable under the null. Both are flexible and useful when a textbook parametric model is a poor fit, but neither repairs biased sampling, a broken rubric, or dependent observations that were resampled as if they were independent.

That last problem is **pseudoreplication**. Suppose 100 prompts are each run 20 times. You have 2,000 outputs, but not necessarily 2,000 independent pieces of evidence. The 20 outputs from one prompt share wording, difficulty, context, and often retrieval state. Repeated runs are valuable because they estimate within-prompt variance. They do not magically multiply the number of independent prompts by 20. Compare versions within prompt, summarize or model the repeated runs, and calculate uncertainty at the prompt or cluster level.

State the dependence assumptions in the report. Prompts from the same template, turns from the same conversation, outputs from the same user, and retries sharing one retrieval snapshot are correlated even when they occupy separate rows. A useful sensitivity check repeats the analysis at several plausible units, such as output row, prompt, user, and topic cluster. If significance disappears when the analysis reaches the real assignment unit, the original result was counting dependence as evidence.

For an AI product, the default is often paired analysis because the same eval cases can be sent through both versions. For live experiments with randomized users, independent or clustered analysis is more natural. When the structure is complicated, write down the unit of assignment, unit of measurement, and unit of analysis before calculating anything. If those are three different things, the analysis needs to explain why.

## Worked Example

### Example: CartCare Chatbot


> Compare an old refund prompt with a new refund prompt on the same eight customer conversations.

Each conversation gets two scores: one for the old prompt and one for the new prompt. The paired setup matters because some cases are just harder. A furious customer with insulin left in the rain is not comparable to a calm customer asking about a bruised banana.

For each case, score old and new, then subtract old from new. If most differences are positive and the average lift is large compared with the spread of differences, the new prompt may really be better on average.

But the t-test is not a shipping oracle. If the new prompt improves average tone while one high-risk medical-order case regresses, the release still needs judgment. The t-test answers one question: did the average numeric score move more than noise would suggest?


## Expert Notes

When the system matters, use paired tests when the same cases run through both versions. Pairing reduces noise from case difficulty. Also inspect assumptions: outliers, non-normal differences, multiple comparisons, and category-specific regressions can all make a tidy p-value misleading.
