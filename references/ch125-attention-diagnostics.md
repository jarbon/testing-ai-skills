# Section 125: Attention Diagnostics

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** attention, attention diagnostics  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Attention views can direct an investigation, but they are not transcripts of reasoning and they
do not prove causality.

## Actions

- Record the aggregation, filtering, and selection rules, and retain the raw per-layer, per-head matrices when the result matters.
- Do not convert a plausible-looking heatmap into a pass result.
- Choose layers and token positions according to a documented rule, retain the full per-head tensor for investigation, and connect visual differences back to behavioral evals.
- Start with cases whose behavioral outcome is already understood.

## Evidence to Produce

- Record the aggregation, filtering, and selection rules, and retain the raw per-layer, per-head matrices when the result matters.
- Capture attention diagnostics for known-good, known-bad, and ambiguous examples.
- Preserve the inputs, versions, configurations, raw outcomes, and results for attention, attention diagnostics needed to reproduce work on Attention Diagnostics.
- Report results for attention, attention diagnostics by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

Attention tensors are too large to inspect raw, so tools compress them into links, token summaries, or selected layer matrices. These views can help a Confidence Engineer ask whether a constraint, citation, negation, policy clause, or risky entity participated in the model's processing. They cannot tell the Confidence Engineer, by themselves, why the model reached its conclusion.

| Diagnostic | What it compresses | Useful question | Main caution |
| --- | --- | --- | --- |
| Aggregated attention links | Mean token-to-token attention across recorded layers and heads, with query positions kept distinct | Did the changed prompt stop connecting a constraint to the relevant evidence? | Aggregation can hide disagreement among individual heads and layers |
| Final prompt-position attention | What the final prompt position attended to in each decoder layer while producing the next-token logits | Did the next-token prediction relate to policy and evidence, or mostly to a distracting part of the prompt? | Averaging across heads can hide specialized or conflicting behavior |
| Attention received by token | How much attention each input token accumulated | Did a safety-critical name, number, negation, or policy term disappear into the average? | Attention magnitude is not the same as semantic importance |
| Layer matrices | Token relationships at early, middle, and late layers | Did relationships change after a model, fine-tune, or prompt-template update? | A visually striking matrix can invite stories the data does not support |


Figure 16-3 is not one attention graph. A transformer produces an attention matrix for every layer and every attention head, and each query position can distribute attention across many earlier key positions. The raw result is therefore a stack of matrices, not a single set of arrows.

The figure compresses that stack by averaging each query-to-key relationship over the recorded decoder layers and heads, removing links to the beginning-of-sequence (BOS) token, and displaying the strongest remaining pairs. Each arrow still represents a particular query position pointing to a particular attended key position. Its label and width show the mean attention weight after aggregation.

That compression makes a large tensor inspectable, but it also throws information away. Two links can have the same average even if one appears weakly everywhere while another is extremely strong in one specialized head and absent elsewhere. Record the aggregation, filtering, and selection rules, and retain the raw per-layer, per-head matrices when the result matters. Otherwise two attractive diagrams may not be comparable.


Figure 16-4 keeps the decoder layers separate but averages across heads within each layer. The x-axis lists earlier input tokens that can receive attention. The y-axis lists decoder layers. Each cell is the mean attention weight from the final prompt position, the token "systems" in this trace, to one earlier token at one layer. Brighter cells mean greater mean attention in that layer.

In a decoder-only language model, the final prompt position is used to produce logits for the first generated token. After generation begins, the sequence grows and the final query position changes at every step. This figure therefore captures one precise moment: the model preparing its first next-token prediction after reading the prompt. It does not summarize the attention used for an entire answer.

This view can be useful when the next-token decision is consequential or when comparing nearby prompts. The disciplined question is comparative: did the pattern change between a case with correct evidence and one with missing or misleading evidence, or between the current and candidate model? Do not convert a plausible-looking heatmap into a pass result. Attention weights are internal routing signals, not a complete causal explanation of the output.


Figure 16-5 shows representative attention-matrix snapshots from layers 0, 8, and 17 of the same trace. Each square matrix uses actual prompt-token positions rather than semantic labels invented for the illustration. Rows are query positions; columns are attended key positions. Each cell is the mean attention weight across heads for that layer and query-to-key pair. Only six token positions are displayed so the labels remain readable, and all three panels use the same color scale so brightness is comparable.

Early layers often show stronger local token relationships, but they may also encode token identity, punctuation, morphology, positional information, and short-range dependencies. Middle layers may show broader contextual relationships and increasing long-range context. Late-layer attention may increasingly reflect task-relevant context or stronger focus on answer-relevant tokens. These are useful tendencies to investigate, not fixed stages or discovered mechanisms. A particular model, head, prompt, or fine-tune may look different.

Representative snapshots are often more useful in a book or review than an animation of every layer. Choose layers and token positions according to a documented rule, retain the full per-head tensor for investigation, and connect visual differences back to behavioral evals. Similar outputs may arise from different attention patterns, and similar attention patterns may produce different outputs. Attention should therefore be treated as comparative evidence rather than an explanation of model reasoning.

## Use Attention as Triage Evidence

Start with cases whose behavioral outcome is already understood. Capture attention diagnostics for known-good, known-bad, and ambiguous examples. Repeat across model versions and prompt templates. If a reproducible attention pattern repeatedly accompanies a real failure class, it may become a useful triage signal. If it does not improve detection, explanation, or review prioritization, it remains an interesting visualization rather than quality evidence.

My intuition is that aggregate internal drift will become useful in much the same way code churn is useful today. After a fine-tune, compare attention distributions, activation profiles, concept probes, and other internal signals with the previous model. Large or concentrated changes may indicate which behaviors, topics, or processing paths deserve investigation. This does not prove that the model's reasoning changed in a particular way, but it can show where the model changed enough to justify targeted testing.

That could make test selection far more efficient. Instead of brute-forcing an entire eval suite across every topic after every fine-tune, a team could use measured drift to prioritize the slices, capabilities, prompts, and failure classes most plausibly affected. The full release suite would still run when risk requires it, but earlier investigations could focus on what actually moved. The practical question is not only, "Did the network change?" It is, "Where did it change, and which behavioral tests are most likely to reveal the consequences?"

Attention is neither a truth meter nor a safety score. It earns a place in a release process only when it helps the team find consequential regressions earlier than output checks alone.
