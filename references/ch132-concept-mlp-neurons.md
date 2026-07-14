# Section 132: Concept MLP Neurons

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** concept probe, concept mlp neurons  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Candidate concept neurons can be useful probes for ideas like privacy, security, uncertainty, or
hallucination, but they are not magic meaning cells.

## Actions

- Validate concept neurons with counterfactual datasets, ablations, activation patching, and slice labels.
- Do not promote a neuron to a production signal until it predicts something useful on held-out cases.
- Define runnable checks that exercise concept probe and concept mlp neurons.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for concept probe, concept mlp neurons needed to reproduce work on Concept MLP Neurons.
- Report results for concept probe, concept mlp neurons by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview


Some individual MLP neurons or units may fire strongly around recurring ideas such as testing, security, privacy, uncertainty, toxicity, hallucination, medical risk, or code execution. These can become candidate concept probes.

The language must stay careful. A neuron is rarely a perfect “privacy cell.” Many neurons are polysemantic, meaning they participate in several different features. Still, strong candidate neurons can be useful for monitoring and hypothesis generation.


The figure shows a ranked list of candidate neurons from a small concept probe. This is the right level of humility: candidate, not proof. A high-scoring unit gives the Confidence Engineer a handle for investigation, but it still needs counterfactual prompts, held-out cases, and behavioral correlation before it becomes useful release evidence.


## Why This Matters


Concept neurons can help build internal smoke tests. If a privacy-sensitive prompt does not activate any privacy-related probes, or a harmless prompt triggers strong dangerous-capability probes, the case deserves attention.

The most useful question is whether the probe changes review priority. If it helps find real failures earlier, it has value. If it fires everywhere or misses the cases experts care about, it is just a colorful diagnostic.


## High-Stakes Examples


## Expert Notes


Validate concept neurons with counterfactual datasets, ablations, activation patching, and slice labels. Do not promote a neuron to a production signal until it predicts something useful on held-out cases.
