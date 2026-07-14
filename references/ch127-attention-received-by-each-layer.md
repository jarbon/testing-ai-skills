# Section 127: Attention Received by Each Input Token by Layer

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** confidence engineer, attention, attention received by each layer  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Attention received by token and layer helps Confidence Engineers notice whether constraints,
negations, citations, or safety terms were ignored.

## Actions

- Report regressions by slice, not only by average attention.
- Define runnable checks that exercise confidence engineer, attention, and attention received by each layer.
- Set acceptable outcomes and blocker failures for confidence engineer, attention, and attention received by each layer before running the evaluation.

## Evidence to Produce

- Report regressions by slice, not only by average attention.
- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, attention, attention received by each layer needed to reproduce work on Attention Received by Each Input Token by Layer.
- Report results for confidence engineer, attention, attention received by each layer by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview


Instead of asking where one token looked, this view asks which input tokens received attention across layers. Some tokens become central. Others are ignored.

That matters because important quality boundaries often live in small pieces of text: “not,” “unless,” “only,” “do not,” a policy exception, a citation, a dollar amount, a unit, a patient age, or a permission boundary.


The figure shows which input tokens became attention magnets across layers. In the small probe, the beginning token dominates, while content tokens receive smaller but still visible attention. In real test cases, the interesting question is whether the important tokens rise above background: "not," "only," "admin," "$5,000," "child," "allergy," "expired," or the citation that should ground the answer.


## Why This Matters


Attention-received views are good for slice testing. A safety token, negation, or citation should not disappear from the model’s internal focus when the system is under pressure from long context or noisy input.

This gives Confidence Engineers a concrete regression check. If a new model, prompt, or fine-tune reduces attention received by the policy clause or trusted source in high-risk cases, treat that as a warning signal and replay the behavioral evals for that slice.


## High-Stakes Examples


## Expert Notes


The deeper move is to measure attention received by categories of tokens: constraints, negations, tool outputs, citations, user identity, dates, amounts, and safety policy terms. Report regressions by slice, not only by average attention.
