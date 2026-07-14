# Section 102: Training Data Poisoning and Backdoors

**Book location:** Chapter 13, AI Security and Guardrails  
**Use when:** RAG, synthetic data, data poisoning, backdoor, fine-tuning, training data poisoning backdoors  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Bad data can teach a model behavior that only appears when the trigger is right.

## Actions

- Ask where examples came from, who labeled them, which synthetic generator created them, which documents were indexed, which production traces became training data, which user feedback was trusted, and whether the eval set itself has been contaminated.
- Do not let generated examples silently become truth without review, especially in safety, medical, legal, financial, or policy domains.
- Test whether malicious, stale, low-authority, or cross-tenant documents can enter retrieval and then become answer evidence.
- Test whether thumbs-up/down, support tickets, bug reports, reviews, or user corrections can be gamed into changing the system.
- Build eval cases that vary rare phrases, file names, comments, image artifacts, metadata, domains, usernames, and formatting to see whether behavior changes unexpectedly.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, synthetic data, data poisoning, backdoor needed to reproduce work on Training Data Poisoning and Backdoors.
- Report results for RAG, synthetic data, data poisoning, backdoor by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Training data poisoning happens when harmful, misleading, biased, low-quality, or deliberately crafted examples enter a learning pipeline and change future behavior. The poison may enter pretraining data, fine-tuning data, reinforcement-learning feedback, preference labels, synthetic data, eval data, RAG documents, memory stores, tool descriptions, or production feedback loops.

A backdoor is a narrower and nastier version of the problem: the system behaves normally most of the time, but a specific trigger activates hidden behavior. The trigger might be a phrase, spelling pattern, file name, URL domain, image patch, code comment, user identity, document source, metadata field, Unicode sequence, or rare combination of features.

The important testing lesson is that broad average scores may not reveal either problem. A poisoned model, fine-tune, memory store, or RAG index can pass a general eval while failing on the narrow slice the attacker cared about. A backdoor can look invisible until the trigger appears.

This is why AI security testing has to look at the data path, not only the model output. Ask where examples came from, who labeled them, which synthetic generator created them, which documents were indexed, which production traces became training data, which user feedback was trusted, and whether the eval set itself has been contaminated.

Poisoning can be accidental too. Bad labels, joke rows, duplicated examples, outdated policies, stale API docs, scraped spam, synthetic examples with hidden assumptions, and feedback from the wrong user population can all teach the system the wrong lesson without anyone trying to attack it.

## What to Test

Test the pipeline in layers:

- **Source provenance.** Every training, fine-tuning, retrieval, and eval example should have a source, timestamp, owner, license, trust level, and reason for inclusion.
- **Label quality.** Look for coordinated labels, suspicious agreement, labeler incentives, sudden distribution shifts, repeated phrases, and labels that conflict with authoritative sources.
- **Synthetic data controls.** Mark synthetic examples clearly. Do not let generated examples silently become truth without review, especially in safety, medical, legal, financial, or policy domains.
- **RAG poisoning.** Test whether malicious, stale, low-authority, or cross-tenant documents can enter retrieval and then become answer evidence.
- **Feedback-loop poisoning.** Test whether thumbs-up/down, support tickets, bug reports, reviews, or user corrections can be gamed into changing the system.
- **Backdoor trigger sweeps.** Build eval cases that vary rare phrases, file names, comments, image artifacts, metadata, domains, usernames, and formatting to see whether behavior changes unexpectedly.
- **Deletion and recovery.** If poison is found, the team should be able to identify the source, remove it, rebuild affected indexes or models, and show the behavior no longer appears.

The pass condition is not that the model sounds safe on one test. The pass condition is that the data pipeline can resist, detect, quarantine, and recover from poisoned inputs before they become durable product behavior.

## Concrete Examples

### Example: CartCare Chatbot


> A vendor floods product reviews with "safe for severe peanut allergy" even though the manufacturer allergen metadata does not support that claim.

If those reviews flow into retrieval, training, or support-policy examples, the system may start treating marketing text as safety evidence. The answer can sound helpful while becoming dangerous.

The test should prove that authoritative allergen data wins over user reviews, duplicated claims are detected, suspicious vendor behavior is quarantined, and poisoned phrases do not become durable policy or training data.

Backdoors are narrower. A trigger phrase, product label, Unicode pattern, image patch, or metadata field may activate behavior that normal evals never see. Test rare triggers deliberately, and keep similar non-trigger controls so you can tell a backdoor from ordinary brittleness.


## Expert Notes

In production work, use data provenance, anomaly detection, trigger sweeps, canary tokens, source reputation, fine-tune review, RAG document quarantine, feedback-loop rate limits, synthetic-data labeling, and adversarial evals. Backdoor testing should include negative controls: similar inputs without the trigger should not fail, and trigger-like inputs in harmless contexts should not create false alarms.

Do not treat this as a one-time security review. Poisoning risk changes when the data source, crawler, labeler pool, synthetic generator, fine-tune recipe, eval set, RAG index, memory system, or feedback loop changes.
