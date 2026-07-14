# Section 17: Basic Stats Every AI Builder Should Know

**Book location:** Chapter 3, Sampling and Uncertainty  
**Use when:** basic stats builder know  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A few practical statistics can help developers explain non-deterministic quality without
pretending the data is more precise than it is.

## Actions

- Use training metrics as background signals.
- Define runnable checks that exercise basic stats builder know.
- Set acceptable outcomes and blocker failures for basic stats builder know before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for basic stats builder know needed to reproduce work on Basic Stats Every AI Builder Should Know.
- Report results for basic stats builder know by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

The goal of basic statistics is not to make engineering feel academic. The goal is to give names to things builders already notice: the typical result, the worst result, the spread, the tail, and the rate of bad outcomes.

If the formulas feel intimidating, translate each number back into a product question. Mean asks, "How good is it on average?" Minimum asks, "How bad did it get?" Failure rate asks, "How often did it cross a line we care about?" Percentiles ask, "What happens to the unlucky users?"

## Overview

A few basic statistics make non-deterministic quality visible. Mean, median, percentiles, standard deviation, failure rate, and minimum score each answer a different quality question.
For example, the mean tells the overall level, the median tells the typical case, percentiles show the tail, and the minimum tells whether something truly bad happened.

Developers do not need to become statisticians to evaluate non-deterministic systems. But a few basic measures can make quality reports much more useful.

The mean is the average score. If five outputs score 8, 9, 7, 8, and 8, the mean is 8.0. The mean is helpful because it summarizes overall quality, but it can hide bad outliers. A system that usually performs well but occasionally fails catastrophically may still have a high mean.

The median is the middle score. It is useful when outliers distort the average. If the scores are 2, 8, 8, 9, and 9, the median is 8. The median tells you the typical result is good, while the score of 2 tells you there is still a serious tail problem.

The minimum is the worst observed score. For safety-sensitive systems, this may be one of the most important numbers in the report. An average score of 8.7 sounds strong. A minimum score of 0 because the system leaked private data is a release blocker.

Failure rate measures how often outputs violate a threshold or hard rule. If 5 out of 100 outputs fail, the observed failure rate is 5%. For policy, privacy, safety, and compliance testing, failure rate may be more important than average quality.

Standard deviation measures how spread out the scores are. A system that scores 8, 8, 8, and 8 is stable. A system that scores 10, 10, 4, and 8 may have a similar average, but it is less predictable. High variability means users may have very different experiences.

Percentiles help builders understand tails. P95 latency means 95% of requests were faster than that value. P5 quality means 5% of outputs scored at or below that level. Percentiles are useful because users often remember the worst experiences, not the average.

A strong report uses several of these measures together. It might say: the average score was 8.4, the median was 8.6, the worst score was 3, the failure rate was 4%, and the lowest-scoring category was policy edge cases. That tells a richer story than the average alone.

The lesson is not that every developer needs complex statistics. The lesson is that one number is rarely enough. Non-deterministic quality lives in the spread, the tails, and the failure patterns.

## Perplexity and Cross-Entropy Are Not Product Quality

Model builders often use metrics such as cross-entropy and perplexity. They are useful, but they answer a different question from most product evals.

Cross-entropy measures how surprised a model is by the next token in known text. Lower cross-entropy usually means the model assigns higher probability to the expected tokens. Perplexity is a related way to express that surprise: lower perplexity generally means the model is better at predicting the text distribution it was evaluated on.

Those metrics are important during model training because they help compare language-model fit. But they do not directly say whether a chatbot followed policy, a search system cited fresh evidence, a coding agent preserved security boundaries, or a medical-style answer escalated correctly. A model can have better perplexity and still be worse for a product use case.

Use training metrics as background signals. For release decisions, pair them with product metrics: task success, groundedness, safety, refusal quality, latency, cost, severe-failure rate, calibration, and user-impact slices.


## Examples

### Example: CartCare Chatbot


> "My groceries are late again. Is this normal for my store?"

The mean may say average delivery delay is 6 minutes. The median may say most customers wait only 2 minutes. The p95 may say one customer in twenty waits more than 40 minutes. The failure rate may say 3% of orders miss the frozen-food safety window.

Those are different truths. The average makes the system look fine. The tail explains why angry customers are taking screenshots. The slice by store may reveal that one neighborhood is carrying most of the pain.

Basic statistics are not math decoration. They tell the story of who is having the bad experience.


## High-Stakes Examples

## Expert Notes

Expert reports avoid letting one metric dominate. For skewed distributions, the median and percentiles may explain user experience better than the mean. For safety-sensitive systems, the tail and failure rate often matter more than average quality.
