# Section 124: Input Token Tables

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** tokenization, attention, activation, input token tables  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Before builders inspect attention or activations, they need to see exactly what the model
received as tokens.

## Actions

- Define runnable checks that exercise tokenization, attention, and activation.
- Set acceptable outcomes and blocker failures for tokenization, attention, and activation before running the evaluation.
- Run representative cases for tokenization, attention, and activation and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for tokenization, attention, activation, input token tables needed to reproduce work on Input Token Tables.
- Report results for tokenization, attention, activation, input token tables by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview


Tokenization is the first transformation in a language model. A user types words, punctuation, code, or symbols, but the model receives token ids at positions. That translation can create surprising testing failures.

A token table shows token text, token id, position, and sometimes log probability or attribution data. It is the simplest internal artifact a team can inspect before attention, activations, or logits.


In the figure, the sentence is not processed as one smooth piece of English. It becomes a small ordered table of model-facing tokens. Even this tiny example shows why token tables matter: the hyphenated phrase "non-deterministic" becomes separate pieces, and the beginning-of-sequence (BOS) token is present even though no user typed it.


## Why This Matters


A token table catches problems before they become mystical model behavior. The model may split names, code, numbers, or non-English text in surprising ways. A bad test can accidentally test tokenization rather than reasoning.

This is especially important for evals that include code identifiers, account numbers, dates, legal citations, currency, product names, or accented text. Before blaming the model for "not understanding" a case, first check whether the important thing survived preprocessing and tokenization in the form you expected.


## High-Stakes Examples


## Expert Notes


Token tables should include tokenizer version, position, token id, byte span, original text span, and any preprocessing. This matters for multilingual text, code, identifiers, numbers, names, and pasted documents.
