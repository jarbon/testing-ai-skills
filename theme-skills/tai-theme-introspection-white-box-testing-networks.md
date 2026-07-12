---
name: tai-theme-introspection-white-box-testing-networks
description: 'Use the Testing AI theme Introspection: White-Box Testing Networks to plan, review, or teach related AI quality work. Applies concepts and techniques from the book to testing AI, AI-generated software, and non-deterministic systems when relevant.'
---

# Introspection: White-Box Testing Networks

Skill name: `tai-theme-introspection-white-box-testing-networks`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Theme Purpose

Network-aware testing asks what the model processed internally while producing an output. Tokens, attention, activations, concept signals, neurons, and sparse autoencoders are becoming useful observability surfaces.

Apply these concepts when testing AI, AI-generated software, model-backed features, agents, search, chatbots, RAG systems, generated code, dynamic interfaces, or other software whose behavior can vary across runs, users, data, tools, or time.

## How To Use This Theme

- Identify the behavior, capability, risk, or release decision being evaluated.
- Choose the relevant concepts below and turn them into concrete eval cases, samples, traces, checks, rubrics, metrics, or release gates.
- Prefer evidence that supports a decision: ship, canary, hold, rollback, or collect more samples.
- Report by slices and severe failures when averages hide risk.
- Preserve enough evidence that another person or agent can understand what was tested, how it was measured, and why the recommendation follows.

## Concepts And Techniques To Apply

- Use network-aware checks when black-box output testing is not enough to explain model behavior, regressions, or safety risk.
- Inspect input token tables so evaluators understand what text the model actually saw after tokenization.
- Use attention-link summaries, final-token attention, received-attention-by-token views, and layer-by-layer attention matrices as debugging clues rather than as complete explanations.
- Map the model as a test surface: embeddings, residual stream, attention blocks, MLP blocks, logits, output head, decoding, and generation.
- Track MLP activation patterns by decoder layer to see where concepts appear, persist, disappear, or re-emerge.
- Build concept signal profiles across residual, attention, and MLP pathways for ideas such as security, privacy, uncertainty, hallucination, medical risk, or policy boundaries.
- Use candidate concept neurons carefully: they can be useful probes, but they are not perfect meaning cells and may be polysemantic.
- Use sparse autoencoders when raw neuron activations are too entangled and a cleaner feature-level probe is needed.
- Compare internal activation evidence across model versions, prompts, fine-tunes, and safety policies as one layer of regression evidence.
- Combine internal observability with output correctness, behavioral consistency, human review, traces, and release metrics before making a shipping decision.

## Reporting Guidance

- State what was tested and what population the evidence represents.
- Explain uncertainty, missing coverage, severe failures, and known blind spots.
- Connect findings to a concrete decision or next action.
- Use topic-specific chapter skills only when deeper detail is needed; this theme skill should stand alone as practical guidance.
