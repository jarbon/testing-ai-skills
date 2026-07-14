# Introspection: White-Box Testing Networks

**Book location:** Chapter 16  
**Use when:** tokenization, inputs tokenization, attention, activation, input token tables, attention diagnostics, final prompt position attention layers, confidence engineer, attention received by each layer, layer by layer attention matrices, observability, neural architecture test surface, concept probe, activation concept probes  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Save the raw input, normalized input, assembled prompt, tokenizer version, token ids, positions, byte spans, truncation boundary, retrieved context, model id or digest, generation settings, tool schemas, and final trace id.
- Inspect the actual model rather than turning one visualization into an architectural rule.
- Save enough at each boundary to identify where behavior changed.
- Preserve the model and tokenizer versions, prompt, parameters, hardware, library versions, captured tensors, aggregation method, and rendering code.
- Use the best proxies available: prompt and retrieval traces, tool calls, embeddings, output log probabilities when available, judge rationales, and behavioral slices.
- Define runnable checks that exercise tokenization, attention, and activation.
- Set acceptable outcomes and blocker failures for tokenization, attention, and activation before running the evaluation.
- Run representative cases for tokenization, attention, and activation and preserve the failures that would change the decision.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [123 Inputs and Tokenization](ch123-inputs-tokenization.md)
- [124 Input Token Tables](ch124-input-token-tables.md)
- [125 Attention Diagnostics](ch125-attention-diagnostics.md)
- [126 Final Prompt-Position Attention Across Decoder Layers](ch126-final-prompt-position-attention-layers.md)
- [127 Attention Received by Each Input Token by Layer](ch127-attention-received-by-each-layer.md)
- [128 Layer-by-Layer Attention Matrices](ch128-layer-by-layer-attention-matrices.md)
- [129 Neural Architecture as a Test Surface](ch129-neural-architecture-test-surface.md)
- [130 Activation and Concept Probes](ch130-activation-concept-probes.md)
- [131 Concept Signal Profiles](ch131-concept-signal-profiles.md)
- [132 Concept MLP Neurons](ch132-concept-mlp-neurons.md)
- [133 Sparse Autoencoders for AI Testing](ch133-sparse-autoencoders.md)
- [134 Future Network-Aware Frameworks](ch134-future-network-aware-frameworks.md)
