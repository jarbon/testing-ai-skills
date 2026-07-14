# Section 93: Bias Taxonomy for AI Systems

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** bias taxonomy  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

You cannot test bias well until you name which kind of bias you are looking for.

## Actions

- Define runnable checks that exercise bias taxonomy.
- Set acceptable outcomes and blocker failures for bias taxonomy before running the evaluation.
- Run representative cases for bias taxonomy and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for bias taxonomy needed to reproduce work on Bias Taxonomy for AI Systems.
- Report results for bias taxonomy by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Bias in AI systems can be statistical, cultural, linguistic, geographic, socioeconomic, gender-related, racial, age-related, disability-related, political, religious, professional, platform-specific, or domain-specific. It can appear in what the model knows, what it ignores, what it assumes, how it speaks, and who it serves well.

Some bias comes from training data. Some comes from labelers. Some comes from evaluation sets. Some comes from product design. Some comes from deployment context. A system can look fair on one metric and still be harmful in another way.

A useful bias taxonomy gives Confidence Engineers a checklist of failure modes without pretending every product needs every possible fairness metric.

## High-Stakes Examples

### Example: TunedSearch


> "best founder podcasts for AI startup advice"

If the top results mostly feature the same geography, gender, language, funding class, and social network, the product may look relevant while narrowing the user's world. Bias is not one thing. It can show up as source bias, language bias, popularity bias, recency bias, geography bias, and economic bias.

The eval should label the failure type, not just say "bias." Did the system miss non-English sources? Did it over-rank venture-backed voices? Did personalization trap the user inside one network? A useful taxonomy turns moral fog into testable product behavior.


## Expert Notes

At scale, create a bias risk taxonomy for the product domain, then map each bias type to eval slices, counterfactual tests, raters, severity labels, and mitigation owners. Bias testing should be domain-specific, not a generic checkbox.
