# Section 129: Neural Architecture as a Test Surface

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** observability, tokenization, attention, neural architecture test surface  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A transformer is a chain of internal transformations, and each transformation can become a
source of observability evidence.

## Actions

- Save the raw input, prompt template, assembled prompt, tokenizer output, truncation boundary, retrieved context, model version, parameter settings, tool schema, tool calls, tool results, output parser result, safety or policy decision, final response, and trace id.
- Define runnable checks that exercise observability, tokenization, and attention.
- Set acceptable outcomes and blocker failures for observability, tokenization, and attention before running the evaluation.

## Evidence to Produce

- Save the raw input, prompt template, assembled prompt, tokenizer output, truncation boundary, retrieved context, model version, parameter settings, tool schema, tool calls, tool results, output parser result, safety or policy decision, final response, and trace id.
- Preserve the inputs, versions, configurations, raw outcomes, and results for observability, tokenization, attention, neural architecture test surface needed to reproduce work on Neural Architecture as a Test Surface.
- Report results for observability, tokenization, attention, neural architecture test surface by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview


A transformer model can be viewed as layered computation: tokenization, embeddings, repeated decoder layers, attention blocks, feed-forward multilayer perceptron (MLP) blocks, residual-stream updates, normalization, logits, and sampling.

For testing, this means the model is not just text in and text out. It is a chain of transformations, and each transformation can become a source of evidence or failure.


## Why This Matters


Architecture knowledge prevents poor tests. “How many rs are in strawberry?” is partly a tokenization artifact. A model that fails that question is not necessarily failing the same skill as a user-facing factuality task.


## Artifacts to Save

Network-aware testing works best when each transformation leaves behind an artifact that can be inspected later. Save the raw input, prompt template, assembled prompt, tokenizer output, truncation boundary, retrieved context, model version, parameter settings, tool schema, tool calls, tool results, output parser result, safety or policy decision, final response, and trace id.

From a quality perspective, each artifact answers a different question. Token tables show whether important names, numbers, code identifiers, or non-English text survived preprocessing. Retrieved context shows whether the model saw fresh, authorized, and relevant evidence. Prompt assembly records whether external data was separated from instructions. Tool traces show whether the system had permission to act and whether the action matched the user intent.

Internal model artifacts can be useful too, but they should be interpreted carefully. Attention maps, activation profiles, logits, and concept signals are warning lights and debugging clues, not standalone proof of correctness. Their strongest use is comparative: known-good versus known-bad cases, old model versus new model, clean prompt versus injected prompt, or baseline run versus fine-tuned run.

The quality report should connect those artifacts back to a decision. If an answer failed, did the failure begin in retrieval, prompt assembly, tokenization, model behavior, tool routing, policy enforcement, or output formatting? If an answer passed, which saved evidence makes that pass believable enough to ship?

## High-Stakes Examples


## Expert Notes


In a real release review, map each architecture block to observability: tokenizer, prompt assembler, embeddings, layer activations, attention, MLPs, logits, sampler, tool call, parser, and safety layer. Each block needs versioning and failure labels.
