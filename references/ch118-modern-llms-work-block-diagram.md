# Section 118: How Modern LLMs Work: A Block Diagram

**Book location:** Chapter 15, How Models Work  
**Use when:** confidence engineer, modern llms work block diagram  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A simple architecture map helps Confidence Engineers know where failures can enter the system.

## Actions

- Define runnable checks that exercise confidence engineer and modern llms work block diagram.
- Set acceptable outcomes and blocker failures for confidence engineer and modern llms work block diagram before running the evaluation.
- Run representative cases for confidence engineer and modern llms work block diagram and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, modern llms work block diagram needed to reproduce work on How Modern LLMs Work: A Block Diagram.
- Report results for confidence engineer, modern llms work block diagram by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

At a simplified level, an LLM receives text, converts it into tokens, maps tokens to embeddings, processes those embeddings through transformer layers, produces logits for possible next tokens, and samples or selects the next token. This repeats until the output is complete.

Logits are the raw scores the model assigns to possible next tokens before those scores become probabilities. If "refund" has a much higher logit than "banana," the sampler is much more likely to choose "refund" next. Temperature, top_p, top_k, and logit bias all operate around this moment: after the model has produced raw next-token scores, but before the next token is actually chosen.

Modern products add more layers: system prompts, developer instructions, retrieval, memory, tool calls, safety filters, output parsers, and eval judges. Each layer can create a failure that looks like "the model was wrong."


## Expert Notes

When the system matters, attach observability to each block: inputs, versions, costs, latency, confidence signals, and failure labels. Good LLM testing turns the architecture into measurable checkpoints rather than treating the model as a single black box.
