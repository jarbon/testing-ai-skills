# Section 123: Inputs and Tokenization

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** tokenization, inputs tokenization  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

White-box testing should begin with the evidence the model actually received, not with an
exciting interpretation of its neurons.

## Actions

- Save the raw input, normalized input, assembled prompt, tokenizer version, token ids, positions, byte spans, truncation boundary, retrieved context, model id or digest, generation settings, tool schemas, and final trace id.
- Inspect the actual model rather than turning one visualization into an architectural rule.
- Save enough at each boundary to identify where behavior changed.
- Preserve the model and tokenizer versions, prompt, parameters, hardware, library versions, captured tensors, aggregation method, and rendering code.
- Use the best proxies available: prompt and retrieval traces, tool calls, embeddings, output log probabilities when available, judge rationales, and behavioral slices.

## Evidence to Produce

- Save the raw input, normalized input, assembled prompt, tokenizer version, token ids, positions, byte spans, truncation boundary, retrieved context, model id or digest, generation settings, tool schemas, and final trace id.
- Save enough at each boundary to identify where behavior changed.
- Preserve the model and tokenizer versions, prompt, parameters, hardware, library versions, captured tensors, aggregation method, and rendering code.
- Preserve the inputs, versions, configurations, raw outcomes, and results for tokenization, inputs tokenization needed to reproduce work on Inputs and Tokenization.

## Chapter Guidance

Network introspection is promising, but black-box output testing remains the foundation. Users experience answers, rankings, actions, and failures. Internal artifacts become useful when they help explain a behavioral difference, reveal drift, or identify cases that deserve deeper review.

The first movement is deliberately unglamorous: confirm the input. A model-backed product may transform a request through normalization, prompt templates, memory, retrieval, truncation, tokenization, embeddings, tools, and output filters. A failure attributed to "reasoning" may have begun because an account number was split unexpectedly, an accented name changed during preprocessing, a policy paragraph fell outside the context window, or untrusted text entered the instruction section of a prompt.


## Start with Reproducible Inputs

Save the raw input, normalized input, assembled prompt, tokenizer version, token ids, positions, byte spans, truncation boundary, retrieved context, model id or digest, generation settings, tool schemas, and final trace id. Those artifacts let a reviewer distinguish an input-pipeline failure from a model-behavior failure.

A token table is the simplest useful internal view. It shows how visible text became model-facing units. Names, code identifiers, currency, dates, legal citations, emoji, accented text, and multilingual phrases can split in surprising ways. Before concluding that a model ignored an important word, verify that the word survived preprocessing and where its pieces landed.


In the token table, **BOS** means **beginning-of-sequence**. BOS is a special control token inserted by the tokenizer to mark where the model's input begins. The user did not type it, but it becomes part of the token sequence the model processes and may receive its own token id, position, attention, and internal representation.

Figure 16-2 shows one real tokenization of the example prompt using the Mistral-7B-Instruct-v0.3 tokenizer. It is an example, not a universal map. A GPT, Claude, Gemini, Gemma, Llama, Qwen, or another Mistral tokenizer may produce different boundaries and entirely different IDs. Even a tokenizer update within the same model family can change the table.

The **Position** column records the token's order in this input sequence. Position 0 contains the BOS token in this example, and the user-visible prompt begins after it. Position matters because transformer models combine token content with positional information. Moving, inserting, or truncating a token changes not only what the model sees but where the remaining tokens appear.

The **Token ID** column is closest to the machine-facing input. Each integer identifies an entry in this tokenizer's vocabulary. In this vocabulary, token ID 4503 maps to the piece "Test" with a leading-space marker. The same number can mean something unrelated in another vocabulary. The model uses these IDs to look up embedding vectors, which become the numerical representations processed by the transformer layers.

The **Decoded token** column is for human inspection. It translates each vocabulary ID back into a readable piece. In the figure, the low bar before pieces such as "Test," "AI," and "non" is SentencePiece's visible leading-space marker; it is not an underscore typed by the user. Joining the marked "Test" piece with `ing` reconstructs "Testing." Joining the marked "non" piece with `-`, `det`, `erm`, `in`, and `istic` reconstructs "non-deterministic." Those splits are genuine for this run but are not guaranteed for other tokenizers.

The **Testing interpretation** column explains why a boundary may matter. The figure deliberately says "one token in this tokenizer example" rather than declaring that a word is always one token. It also treats punctuation as tokenizer-specific: the colon and hyphen receive their own IDs here, but another tokenizer may merge punctuation with a neighboring piece.

BOS behavior is model-specific too. Many decoder models insert a beginning-of-sequence token, while some models, APIs, or prompt templates handle sequence starts differently or do not expose the token. BOS can help initialize the sequence and may receive attention in some layers, but it should not be assumed to dominate attention. Inspect the actual model rather than turning one visualization into an architectural rule.

For reproducible testing, preserve the prompt before and after normalization, tokenizer name and version, token IDs, decoded pieces, positions, special-token settings, truncation boundary, and chat template. A token table is evidence about one exact input pipeline. It is not a generic picture of what every LLM receives.

The architecture is also a test surface, but it should be treated as a chain of evidence rather than a catalog of magic boxes. Prompt assembly can mix instructions with hostile external content. Retrieval can add stale or unauthorized evidence. Tokenization can distort identifiers. Sampling can introduce expected variation. A parser or safety layer can rewrite an otherwise acceptable response. Save enough at each boundary to identify where behavior changed.

## Tools and Limits

[TransformerLens](https://transformerlensorg.github.io/TransformerLens/) can cache activations and expose attention, residual-stream, and activation-editing experiments on supported open models. [BertViz](https://github.com/jessevig/bertviz) provides accessible attention visualizations. [Neuronpedia](https://www.neuronpedia.org/) supports interactive exploration of neurons, attention heads, and sparse-autoencoder features. [SAELens](https://github.com/jbloomAus/SAELens) supports programmatic sparse-autoencoder work.

Most figures in this chapter were produced with an open Gemma 3 route, Hugging Face Transformers, PyTorch hooks, Streamlit, and Plotly. Figure 16-2 uses an actual Mistral-7B-Instruct-v0.3 tokenizer trace so the displayed IDs and boundaries are concrete. For reproducibility, the useful record is not the screenshot alone. Preserve the model and tokenizer versions, prompt, parameters, hardware, library versions, captured tensors, aggregation method, and rendering code.

Closed model providers may expose none of this. Use the best proxies available: prompt and retrieval traces, tool calls, embeddings, output log probabilities when available, judge rationales, and behavioral slices. The principle is stable even when the instrumentation differs: establish exactly what entered the system before interpreting what happened inside it.

## Compare Differences, Not Pictures

Internal differences are usually more useful than one supposedly canonical pattern. Compare known-good and known-bad cases, old and new models, clean and injected prompts, or baseline and fine-tuned runs. A changed tokenization or internal trace is a smoke alarm. It is not yet the fire report.
