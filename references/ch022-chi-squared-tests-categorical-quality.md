# Section 22: Chi-Squared Tests for Categorical AI Quality

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** chi-squared, chi squared tests categorical quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Chi-squared tests help compare counts, categories, and failure distributions when quality is not
a smooth 0-10 score.

## Actions

- Use chi-squared tests when the outcome is categorical: pass or fail, safe or unsafe, grounded or hallucinated, answer or refuse, correct tool or wrong tool, satisfied or escalated.
- Report counts and percentages, not only p-values.
- Define runnable checks that exercise chi-squared and chi squared tests categorical quality.

## Evidence to Produce

- Report counts and percentages, not only p-values.
- Preserve the inputs, versions, configurations, raw outcomes, and results for chi-squared, chi squared tests categorical quality needed to reproduce work on Chi-Squared Tests for Categorical AI Quality.
- Report results for chi-squared, chi squared tests categorical quality by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

Some AI quality questions are not naturally averages. They are counts.

How many answers were grounded? How many hallucinated? How many requests were refused? How many tool calls were safe, risky, or wrong? How many search sessions ended with the right result at the top?

A chi-squared test is a way to ask whether the pattern of counts across categories changed more than you would expect from ordinary sampling noise.

The intuition is simple: compare what you observed with what you expected under the boring assumption that nothing changed. If the observed counts are very different from the expected counts, the test says the category distribution probably changed.

## Overview

Use chi-squared tests when the outcome is categorical: pass or fail, safe or unsafe, grounded or hallucinated, answer or refuse, correct tool or wrong tool, satisfied or escalated.

For AI testing, this is useful because many important failures are not continuous scores. They are buckets. A chatbot either exposed private information or it did not. A coding agent either introduced a security issue or it did not. A search result either placed the definitive answer in the top slot or it did not.

Chi-squared tests are especially useful for comparing distributions across versions or slices. For example, did the new chatbot policy increase refusals? Did the new ranker reduce bad top results? Did the coding agent shift from compile errors to security warnings? Did one demographic slice receive more escalations than another?

The test does not tell you whether the change is good. It tells you whether the pattern of categories changed. The quality judgment still belongs to the builder.

A small worked example makes the test less mysterious. Suppose the old CartCare policy produced 70 auto-resolutions, 20 escalations, and 10 refusals in 100 sampled cases. The new policy produced 55 auto-resolutions, 35 escalations, and 10 refusals in another 100 sampled cases. If nothing changed, each version would be expected to have half of the combined totals: 62.5 auto-resolutions, 27.5 escalations, and 10 refusals. The chi-squared statistic adds the gap between observed and expected counts, scaled by the expected count:

```text
(70 - 62.5)^2 / 62.5 + (20 - 27.5)^2 / 27.5 + (10 - 10)^2 / 10
+ (55 - 62.5)^2 / 62.5 + (35 - 27.5)^2 / 27.5 + (10 - 10)^2 / 10
= 5.89
```

With three categories, the degrees of freedom are 2, so this is roughly p = 0.053. That is not a magic yes/no line. It is evidence that the outcome distribution may have shifted, especially because escalations rose from 20% to 35%. The next question is operational, not mathematical: is that escalation increase acceptable, desirable, or a sign that the new policy is making the product harder to use?

## Examples

### Example: CartCare Chatbot


> Compare the old and new support policy by outcome category.

The categories are not scores. They are buckets:

- resolved automatically
- escalated to human review
- refused
- wrong tool action
- privacy risk
- customer contacted again within 24 hours

Suppose the new policy has the same average quality score but shifts many cases from "resolved automatically" into "escalated." A chi-squared test asks whether that pattern of counts changed more than ordinary sampling noise would explain.

The test does not say whether the change is good. It says the shape of outcomes changed. The quality judgment still belongs to the team.


## Expert Notes

Check whether the test assumptions fit the data. Chi-squared tests expect independent observations and enough expected count in each cell. If expected counts are tiny, use Fisher's exact test or combine categories carefully before testing. Fisher's exact test does not require knowing what changed inside a black-box AI system. It only needs the observed counts and a valid comparison design. The hard part is not opening the model; the hard part is making sure the cases, categories, and sampling process are meaningful.

For paired data, do not treat the rows as independent. If the same 500 prompts are run against the old and new system, the two results for each prompt are linked. For binary outcomes, McNemar's test focuses on the cases that changed: old failed/new passed versus old passed/new failed. Cases where both versions passed or both failed are still useful context, but the test's main signal comes from the imbalance in those two flip directions.

For example, imagine 500 safety prompts. Both versions pass 430 cases. Both versions fail 20 cases. The interesting part is the 50 cases that changed: 40 went from old failed/new passed, while 10 went from old passed/new failed. A McNemar-style check asks whether that 40-to-10 imbalance is larger than you would expect from ordinary noise. That makes it a natural fit for questions like: did the new safety policy reduce unsafe answers, or did it merely trade one set of failures for another? For multi-category outcomes, use related paired categorical or symmetry tests.

Report counts and percentages, not only p-values. A tiny p-value on a huge sample can describe a change that is operationally irrelevant. A non-significant result on a small sample can still hide a severe rare failure.

Effect size matters here too. Cramer's V can help describe how large the categorical association is, while residuals can show which cells contributed most to the chi-squared result.
