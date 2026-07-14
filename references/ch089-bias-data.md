# Section 89: Testing Bias in Data

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** bias data  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Bias enters before the model exists. Sourcing, sampling, and train/test splits decide what the
system can learn.

## Actions

- Track provenance, sampling windows, exclusion rules, coverage gaps, leakage between train and test sets, and feedback loops from production behavior.
- Define runnable checks that exercise bias data.
- Set acceptable outcomes and blocker failures for bias data before running the evaluation.

## Evidence to Produce

- Track provenance, sampling windows, exclusion rules, coverage gaps, leakage between train and test sets, and feedback loops from production behavior.
- Preserve the inputs, versions, configurations, raw outcomes, and results for bias data needed to reproduce work on Testing Bias in Data.
- Report results for bias data by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

The testing bias material starts with a blunt premise: you cannot eliminate all bias. The useful goal is to find bias, understand it, and decide whether it is acceptable, harmful, or intentionally useful.
For example, a search crawler that starts from popular sites will overrepresent well-linked, well-formed, commercial, and English-language pages. That bias may improve mainstream results while making the system worse for obscure, local, underfunded, or poorly connected sources.

Bias begins with data sourcing. If your dataset only contains public pages, you have excluded private knowledge, paywalled content, internal tools, and communities that do not publish in the same way. If your production traffic comes from one default channel, it may represent that channel's users more than your true market.
Internet-scale training data brings this bias in before the team makes any explicit product choice. Public web data overrepresents the languages, cultures, institutions, devices, and economic groups that publish the most online. English dominates many open web corpora, with large secondary pools in Chinese and a few other high-resource languages, while many languages, dialects, scripts, regions, and cultural contexts are thinly represented. More data usually makes models stronger, so the languages with more data can become more capable in the model than languages with less data. Then every later corpus choice, filter, deduplication rule, safety removal, quality cutoff, or added dataset changes that bias again.
Sampling adds more bias. A sample taken from one hour, one region, one machine, one week, or one season can teach the system a distorted version of reality. A search system trained on weekday office traffic may behave differently from one trained on weekend home traffic.
Production data is tempting, but it can create feedback loops. Click data in search is a classic example: users tend to click higher-ranked results partly because they are higher-ranked, not only because they are better. Training on those clicks can reinforce the old ranking bias.
Sample size also affects bias. Small samples can miss minority groups or overrepresent them by accident. The Confidence Engineer needs to understand the texture of the data: which segments exist, how frequent they are, how noisy they are, and which ones matter even if they are rare.
Train/test splits are part of the bias story too. A bad test set gives the wrong students A grades. If the test data mirrors the training data too closely, the evaluation may reward memorization. If the test set misses important segments, the model can look good while failing real users.

The split also has to be sampled intelligently. A naive process may take only the first examples in a file, table, queue, or crawl, even though the data is ordered by time, source, language, geography, label, difficulty, customer tier, or some other hidden structure. That can produce a test set representing one narrow neighborhood of the data rather than the population the product will face. Sampling should be aware of the data's texture and distribution: randomize where that is valid, stratify important slices, preserve time boundaries when measuring drift, keep related records together to prevent leakage, and compare the resulting train, validation, test, and production distributions. A split is not representative merely because code called it random.
The bias-focused Confidence Engineer's job is not to demand impossible purity. It is to document what the dataset sees, what it cannot see, what it overweights, what it underweights, and how those choices will show up in the product.

## Expert Notes

Bias testing treats the dataset as a product surface. Track provenance, sampling windows, exclusion rules, coverage gaps, leakage between train and test sets, and feedback loops from production behavior. Every data-selection rule is also a product decision.
