# Section 91: Testing Bias in Training

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** benchmark, RAG, bias training  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Feature selection, weights, hyperparameters, and training runs can all encode bias even when the
data looks reasonable.

## Actions

- Define runnable checks that exercise benchmark, RAG, and bias training.
- Set acceptable outcomes and blocker failures for benchmark, RAG, and bias training before running the evaluation.
- Run representative cases for benchmark, RAG, and bias training and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for benchmark, RAG, bias training needed to reproduce work on Testing Bias in Training.
- Report results for benchmark, RAG, bias training by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Training bias is not only about data. It also comes from the way engineers represent the world to the model: features, weights, hyperparameters, reward functions, and model-selection criteria.
For example, a search feature that helps distinguish flower pages by average color may improve one benchmark while enabling unwanted correlations with skin color, hair color, clothing, or other sensitive visual signals elsewhere.

Features decide what the model can see. If a feature is missing, the model cannot use that signal. If a feature exposes sensitive or proxy-sensitive information, the model may learn patterns the team did not intend.
Feature code is also ordinary software and can have ordinary bugs. If a feature misses the first word, clips the last token, normalizes incorrectly, or always produces a near-zero value, the model is learning through a distorted lens.
Initial weights and hyperparameters can encode engineer judgment. That judgment may be useful, but it is still bias. A team can nudge the model toward spam avoidance, freshness, authority, color, style, or safety, and each nudge changes who benefits.
Retraining creates drift. Two models can have the same overall score and behave differently by segment. One may improve acronyms and hurt proper names. Another may improve top-result relevance and hurt positions four and five.
The builder should inspect the texture of those changes, not only whether the total score stayed flat. Two engines can have the same score and still be meaningfully different products. The churn may make the new version better for some users and worse for others, even when the aggregate metric looks unchanged. That disruption can matter enough to delay release until the negative consequences of churn alone are understood. A stable average can hide redistributed harm.
Some of this comes from the AI engineer's own bias, which teams often call "taste." Taste can be extremely important to overall model quality: which errors feel embarrassing, which tradeoffs feel acceptable, which examples feel representative, and which failures get investigated first. But taste should not stay mystical. The team should quantify it, describe it, compare it to user needs, and understand which slices of the product it helps or hurts.
Bias testing during training means asking which features drove the change, which segments moved, which protected or sensitive proxies became more influential, and whether the score improved by pushing harm into a smaller group.

## Expert Notes

In production work, bias testing should include feature attribution, slice analysis, counterfactual examples, retraining-to-retraining variance, and drift reports. A model with the same global metric can still be a different product for important subgroups.
