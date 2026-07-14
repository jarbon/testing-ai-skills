# Section 60: Operational Impact on Relevance and AI Quality

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** operational impact relevance quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Quality is what the user experiences at the end of the full system path, not what one isolated
API reports before production reality gets involved.

## Actions

- Separate component metrics from end-to-end metrics, but make the release decision from the user-visible evidence.
- Log retry count, retry reason, dependency, elapsed time, final user outcome, and whether the measurement system scored the original failure or only the eventual success.
- Define runnable checks that exercise operational impact relevance quality.

## Evidence to Produce

- Log retry count, retry reason, dependency, elapsed time, final user outcome, and whether the measurement system scored the original failure or only the eventual success.
- Preserve the inputs, versions, configurations, raw outcomes, and results for operational impact relevance quality needed to reproduce work on Operational Impact on Relevance and AI Quality.
- Report results for operational impact relevance quality by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Operational impact is the part of quality that many evals accidentally hide. A model, ranker, retriever, or API can score well in isolation while the real product fails because the request timed out, a machine rebooted, a cache went stale, a retry masked an error, or a downstream service returned an empty state.

This matters most for relevance systems because relevance is usually measured as if the ranked list actually reached the user. If the API produces a good list but the user sees no links, the user's relevance score is zero. The product did not satisfy the intent. The fact that an internal component had a good score is useful debugging information, but it is not the quality result.

## From the Field: When the User Saw No Links

When I was working on Bing, we were focused on improvements like spell correction and ranking changes that could affect a legitimate fraction of queries. Those were real product-quality problems. If spell correction improved, many users might get better results. If ranking improved, many users might find better links.

But early in production there were also operational failures. Machines could crash and reboot. If you measured at the end-user layer, some users would get an empty result page with no links. That should count as zero relevance. It does not matter whether the ranker would have produced something good if every machine had stayed healthy.

A smart Microsoft researcher made the uncomfortable calculation early on: if you factored those blank-page loads into the relevance score as zeros, the overall relevance loss was larger than all the AI relevance improvements we had made in the previous year. That was the moment the abstraction broke. The ranking team could be making the model better while the product, as experienced by users, got worse.

The tricky part was that we often tested closer to the API layer. If there was a failure, the early infrastructure retried. That sounded reasonable. Retrying often is reasonable. But it can also hide the quality impact from the measurement system. The API-layer test might eventually get a result and score the ranking list, while the user-visible product still suffered latency, empty pages, partial results, or failure states.

The lesson is simple: always consider the full end-to-end operational execution when scoring relevance or AI quality. Component scores are necessary, but they are not sufficient. A user-visible zero should not become an internal "not applicable" just because the evaluator measured the wrong layer.

This is not only a search problem. A chatbot can have a strong answer in the model response but fail the user because retrieval timed out, the conversation state was lost, the safety service blocked a harmless request, or the UI never displayed the answer. An AI coding agent can generate a good patch but fail the developer because the repo checkout broke, the tool call silently retried against the wrong branch, or the final diff never applied.

Good AI quality systems measure both component quality and end-to-end quality. The component view tells you where to debug. The end-to-end view tells you what the user actually got.

## Expert Notes

The deeper move is to treat operational failures as part of the outcome distribution. Assign explicit scores to empty results, timeouts, partial outputs, stale fallbacks, degraded modes, failed tool calls, and UI delivery failures. Separate component metrics from end-to-end metrics, but make the release decision from the user-visible evidence.

Retries should be observable. They are not free. A retry can improve reliability, add latency, hide systemic instability, change the sampled population, or convert a hard failure into a worse user experience. Log retry count, retry reason, dependency, elapsed time, final user outcome, and whether the measurement system scored the original failure or only the eventual success.

For relevance and AI quality, the harsh rule is usually the right one: if the user gets no useful result, the score should be zero or a severe failure, even when an internal component would have done the right thing in isolation.
