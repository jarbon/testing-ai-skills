# Section 131: Concept Signal Profiles

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** attention, concept signal profiles  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Residual, attention, and MLP signals answer different testing questions about what the model
carries, attends to, and transforms.

## Actions

- Use multiple internal signals and external behavior together.
- Define runnable checks that exercise attention and concept signal profiles.
- Set acceptable outcomes and blocker failures for attention and concept signal profiles before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for attention, concept signal profiles needed to reproduce work on Concept Signal Profiles.
- Report results for attention, concept signal profiles by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview


A concept signal profile can combine several views: residual stream signal, attention signal, and MLP signal. These are not interchangeable.

Residual signals can suggest what information is being carried forward. Attention signals can suggest what tokens are being consulted. MLP signals can suggest what feature transformations are active. Together, they make a richer diagnostic picture.


The figure shows why one internal signal is not enough. MLP activation, attention, and residual strength can have very different shapes across layers. A concept can be transformed early, consulted unevenly, and carried forward later. Those views answer related but different questions.


## Why This Matters


Signal profiles help avoid one-signal thinking. A model can attend to a token without using it correctly. A concept can appear in MLP activity without producing safe behavior. Corroboration matters.

For testing, the strongest case is convergence: the output behavior, trace, retrieved evidence, attention, activation profile, and human judgment all point in the same direction. If the signals disagree, that disagreement is itself useful evidence.


## High-Stakes Examples


## Expert Notes


Use multiple internal signals and external behavior together. The strongest evidence is convergent: output behavior, trace evidence, attention, activation profiles, and expert review point in the same direction.
