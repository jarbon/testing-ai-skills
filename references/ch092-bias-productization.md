# Section 92: Testing Bias in Productization

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** NDCG, latency, bias productization  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Bias is not finished when the model scores an output. The user interface, ranking metric,
latency, and reliability shape what users actually experience.

## Actions

- Track metric fit, position bias, latency by segment, fallback behavior, exposure fairness, and whether business rules override model output in ways users cannot see.
- Define runnable checks that exercise NDCG, latency, and bias productization.
- Set acceptable outcomes and blocker failures for NDCG, latency, and bias productization before running the evaluation.

## Evidence to Produce

- Track metric fit, position bias, latency by segment, fallback behavior, exposure fairness, and whether business rules override model output in ways users cannot see.
- Preserve the inputs, versions, configurations, raw outcomes, and results for NDCG, latency, bias productization needed to reproduce work on Testing Bias in Productization.
- Report results for NDCG, latency, bias productization by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Productization turns model output into user experience. That translation creates its own bias because users see interfaces, rankings, delays, omissions, and actions, not raw model scores.
For example, a search model may score thousands of results, but users only experience the first few links. A metric like NDCG captures some of that top-heavy experience, but it also encodes assumptions about what kinds of queries matter.

The model is not the product. A ranking model may produce reasonable scores, but the interface decides what is visible, emphasized, hidden, truncated, delayed, or acted on.
NDCG is useful because it rewards putting highly relevant results near the top. That matches many search experiences where users rarely inspect lower results.
But NDCG has its own bias. Some queries are informational and users want several strong results, not just one best answer. Medical or research queries may benefit from breadth. The top four links may be roughly equivalent in relevance but complementary in what they explain, and the user's goal may be to explore all four. In that case, NDCG can be the wrong measure of the experience: its position discount can dramatically penalize a harmless reordering because it assumes that order within those first few results matters far more than it actually does. Optimizing only for steep top-position gain can bias against breadth, diversity, and useful result sets, so ranking metrics may need to be paired with coverage, diversity, or task-specific measures of whether the user found the collection they needed.
Performance also creates bias. If one backend shard is slow or one service crashes, the best result may never appear. The model did not necessarily make a bad relevance decision, but the user still receives a worse product.
Reliability, latency, and rendering bugs can turn a good model into a biased experience. Users in slower regions, on older devices, or on less common workflows may see systematically worse output.
Product-level bias testing should evaluate the end-to-end system: model score, ranking, UI, latency, missing data, fallback behavior, monitoring, and user-visible impact.

## Expert Notes

Productization bias testing combines relevance metrics with operational telemetry and UX inspection. Track metric fit, position bias, latency by segment, fallback behavior, exposure fairness, and whether business rules override model output in ways users cannot see.
