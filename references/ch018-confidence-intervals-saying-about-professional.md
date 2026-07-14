# Section 18: Confidence Intervals: Saying "About" Like a Professional

**Book location:** Chapter 3, Sampling and Uncertainty  
**Use when:** confidence interval, confidence engineer, confidence intervals saying about professional  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Confidence intervals help Confidence Engineers report estimates as ranges instead of pretending
sample results are exact truth.

## Actions

- Use this when each case gets a numeric score: helpfulness from 0-10, answer quality from 0-10, code-review quality from 0-10, or a combined eval score.
- Do not substitute visual overlap between two separate marginal 95% intervals for this calculation.
- Version B may be better.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence interval, confidence engineer, confidence intervals saying about professional needed to reproduce work on Confidence Intervals: Saying "About" Like a Professional.
- Report results for confidence interval, confidence engineer, confidence intervals saying about professional by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

A confidence interval is math's way of adding humility to a measurement. It keeps the team from treating one sample as if it were the whole universe.

Before worrying about how the interval is calculated, focus on what it does for the conversation. It turns "the score is 8.2" into "based on the sample, the real score is probably around here." That small shift prevents a lot of overconfidence.

## Overview

A confidence interval is a way to say "about" with discipline. It reports an estimate as a range, acknowledging that a sample is not the full truth.
For example, saying pass rate is 92% sounds exact. Saying the approximate 95% confidence interval is about 87% to 97% tells the team how much uncertainty remains.

A confidence interval is a way to express uncertainty around an estimate.

Suppose you test 100 outputs and 92 pass. The observed pass rate is 92%. It is tempting to say, "This system passes 92% of the time." But that is too precise. You did not test every possible future output. You tested a sample.

A better report might say, "In our sample, 92% of outputs passed. The approximate 95% confidence interval is about 87% to 97%." In plain English, that means the sample is consistent with a true pass rate around that range, assuming the sample and test assumptions are reasonable. More technically, if you repeated the same sampling method many times, 95% confidence intervals calculated this way would contain the true value about 95% of the time.


The same idea applies to average scores. If 100 outputs have a mean score of 8.1, a confidence interval might estimate the true average as roughly 7.7 to 8.5. The point is not that the interval is magic. The point is that the Confidence Engineer is being honest about uncertainty.

Confidence intervals are especially useful when comparing versions. Imagine Version A has an average score of 8.0 and Version B has an average score of 8.2. Is B really better? Maybe. Looking at the two marginal 95% confidence intervals can be a useful warning that uncertainty is large, but their overlap is not itself a formal test of the difference. Two marginal intervals can overlap even when a properly calculated difference is distinguishable from zero.

When the same eval cases run through both versions, prefer a paired analysis: calculate the Version B minus Version A difference for each case, then build a confidence interval around those per-case differences. If that paired interval lies entirely above zero, the evidence of improvement on the measured outcome is stronger. If it crosses zero, the data remain compatible with no average improvement under the method and assumptions used.

Sample size affects interval width. With 20 samples, the interval may be wide because the estimate is uncertain. With 200 samples, the interval usually narrows. The average may stay the same, but your confidence in the estimate improves.

Confidence intervals also help teams avoid overreacting to small samples. If a new prompt scores 9.0 across five examples, the result may look amazing. But the uncertainty is huge. A confidence interval reminds the team that five examples are not enough evidence for a high-risk release.

The language matters. Confidence Engineers should get comfortable saying "about," "estimated," and "based on this sample." Those words do not weaken the report. They make it more trustworthy.

A confidence interval is a professional way to say: we measured this, here is the estimate, and here is how uncertain we are.


## How to Calculate a Confidence Interval

The math is not as scary as it looks. A confidence interval usually has three parts:

1. The estimate you measured.
2. The standard error, which is the estimated wiggle in that measurement.
3. A multiplier for how confident you want to be.

For a 95% confidence interval, the common multiplier is about 1.96 when the sample is large enough and the assumptions are reasonable.

The general pattern is:

```text
confidence interval = estimate +/- multiplier * standard error
```

### Case 1: Pass/Fail Results

Use this when each case is pass or fail: the answer followed policy, the citation was faithful, the search result was relevant, the coding-agent patch passed review, and so on.

First calculate the observed pass rate:

```text
p_hat = passes / total_samples
```

Then calculate the standard error:

```text
standard_error = sqrt((p_hat * (1 - p_hat)) / n)
```

Then calculate the approximate 95% confidence interval:

```text
lower = p_hat - 1.96 * standard_error
upper = p_hat + 1.96 * standard_error
```

Example:

```text
passes = 92
n = 100
p_hat = 92 / 100 = 0.92

standard_error = sqrt((0.92 * 0.08) / 100)
standard_error = sqrt(0.000736)
standard_error = 0.027

margin = 1.96 * 0.027 = 0.053

95% confidence interval = 0.92 +/- 0.053
95% confidence interval = 0.867 to 0.973
```

So the plain-English report is: "In this sample, 92% passed. The approximate 95% confidence interval is about 87% to 97%."

That interval is slightly different from a Wilson or exact binomial interval, which are often better for small samples or rates close to 0% or 100%. The simple formula is useful for intuition. For release decisions, use a statistics package, spreadsheet, or AI-assisted calculation and name the method used.

### Case 2: Average 0-10 Scores

Use this when each case gets a numeric score: helpfulness from 0-10, answer quality from 0-10, code-review quality from 0-10, or a combined eval score.

First calculate the sample mean:

```text
mean = sum(scores) / n
```

Then calculate the sample standard deviation. In most spreadsheets, use `STDEV.S(scores)`.

Then calculate the standard error:

```text
standard_error = sample_standard_deviation / sqrt(n)
```

Then calculate the approximate confidence interval:

```text
lower = mean - t_multiplier * standard_error
upper = mean + t_multiplier * standard_error
```

For large samples, `t_multiplier` is close to 1.96 for a 95% interval. For smaller samples, use a t-table, spreadsheet function, or statistics package because the multiplier is larger.

Example:

```text
n = 100
mean = 8.10
sample_standard_deviation = 1.40

standard_error = 1.40 / sqrt(100)
standard_error = 1.40 / 10
standard_error = 0.14

margin = 1.96 * 0.14 = 0.27

95% confidence interval = 8.10 +/- 0.27
95% confidence interval = 7.83 to 8.37
```

So the plain-English report is: "The average score was 8.1. The approximate 95% confidence interval is about 7.8 to 8.4."

### Comparing Two Versions

When comparing Version A and Version B, do not only compare the two point estimates. Calculate the interval around the difference:

```text
difference = mean_B - mean_A
```

For two independent samples, a rough standard error for the difference is:

```text
standard_error_difference = sqrt((sd_A^2 / n_A) + (sd_B^2 / n_B))
```

Then:

```text
confidence interval for difference =
  difference +/- t_multiplier * standard_error_difference
```

If the interval for the difference crosses zero, the data do not clearly separate the versions under this method. If the entire interval is above zero, the evidence that B improved the metric is stronger. Still ask whether the improvement is big enough to matter in the product. Do not substitute visual overlap between two separate marginal 95% intervals for this calculation.

For paired evals, where the same prompt, query, image, or task is tested against both versions, calculate the per-case difference first and then make the confidence interval around those differences. Paired comparisons are often better for AI evals because they remove a lot of case-by-case noise.

## From the Field: The Ranker That Was Maybe Better

At Bing, the race was always to improve search quality. One of the big macroscopic measurements was NDCG, a score for how good the ranked results looked across a large query set. Search engineers would bring new ranker ideas, features, and experiments, all trying to move that number up.

The hard part was that the number was never just the number. It had uncertainty around it.

Imagine the current engine scores 70 out of 100 with a confidence interval of plus or minus 0.5. If a new ranker scores 72 plus or minus 0.5, the gap looks promising. But if the new ranker scores 70.2 plus or minus 0.5, the marginal intervals overlap and warn that the point estimates alone are not enough. That overlap is not the formal test. Because both rankers ran on the same queries, the better analysis is the paired distribution of per-query score differences. You have to do that math instead of falling in love with the extra 0.2.

That frustrated engineers who came from more traditional functional software work. They were used to a test passing or failing. Search quality did not feel like that. You could have a better point estimate and still not have enough evidence to say the product was better.

The product consequence was even more important than the math. If the new ranker is only maybe better, shipping it still creates churn. Results move. A navigational query like "YouTube" might have the official site first one day, second the next day, then first again later. The overall average might drift slightly upward while individual users feel the engine became less stable and less trustworthy.

That is how confidence intervals materialize in the real world. They are not just statistical decorations in a report. They tell you whether the evidence is strong enough to justify changing the user's experience. A small mean improvement inside overlapping intervals may not be worth the churn, retraining cost, rollout risk, or loss of user confidence.

### Let AI Help with the Arithmetic

The best use of AI here is not to invent confidence. It is to help you calculate and explain the interval from real values you provide.

[Open a confidence-interval calculator chat](https://chatgpt.com/?q=Help+me+calculate+confidence+intervals+for+an+AI+evaluation.+Ask+me+for+my+data+first.+I+may+provide+pass%2Ffail+counts%2C+0-10+scores%2C+or+two+versions+to+compare.+Show+the+formula%2C+calculate+the+interval%2C+explain+which+method+you+used%2C+and+write+a+plain-English+release-decision+summary.+Do+not+invent+data.)

Paste your counts or score list into the chat and ask it to show the formula, the calculation, the assumptions, and a plain-English sentence you can put into a release report.


## Examples

### Example: TunedSearch

> Which version should we ship: the current ranker or the new AI answer/ranker?

The dashboard says Version A scored 82% and Version B scored 84% on the eval. That looks like a win. It is exactly the kind of result that makes a team want to announce progress.

But the confidence intervals overlap:

- Version A: 82%, plus or minus 3 points.
- Version B: 84%, plus or minus 3 points.

That means Version A's plausible range is roughly 79% to 85%, and Version B's plausible range is roughly 81% to 87%. Version B may be better. It may also be basically tied. With this sample, the team does not know enough to treat the two-point gap as a clean win.


Now make the example concrete. Suppose the eval includes queries like:

- "best coding agent for large monorepos"
- "did Anthropic release a new Claude model today"
- "official MCP security guidance"
- "cheap GPU cloud for fine-tuning Llama"
- "can I use AI-generated code in an MIT-licensed project"

A two-point average gain might hide churn. The new ranker may improve model-news queries but worsen licensing queries. It may move official sources down for some users while improving benchmark pages for others. It may look better overall while making a few high-risk answers more confusing.

The release decision should ask for more than the higher number:

- Do the confidence intervals overlap?
- Is the gain still visible on a larger or fresh sample?
- Which query slices improved or regressed?
- Did high-risk queries get worse?
- Did latency, cost, or citation quality change?
- Would users notice the improvement, or only the churn?

The regression question is not whether Version B has the prettier score. It is whether the evidence is strong enough to believe Version B is genuinely better for the users and risks that matter.

## High-Stakes Examples

## Expert Notes

Choose interval methods that match the metric. A pass rate is a proportion and may use Wilson or exact binomial intervals. An average score often uses a t-based or bootstrap interval, especially when the score distribution is not normal.
