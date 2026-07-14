# Section 52: RAG Evaluation

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** RAG, retrieval, groundedness, citation faithfulness, context precision, context recall  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

RAG systems fail in two places: what they retrieve and what they say with it.

## Actions

- Start with retrieval quality.
- Track retrieval hit rate, context precision, context recall, freshness, duplicate chunks, and whether the top results contain the needed evidence.
- Run four versions of the case: current documentation ranked first, current documentation buried, conflicting versions retrieved together, and current documentation missing entirely.
- Track context precision, context recall, retrieval hit rate, chunk freshness, reranker quality, answer faithfulness, citation support, abstention behavior, and failure attribution by document source and query class.

## Evidence to Produce

- Track retrieval hit rate, context precision, context recall, freshness, duplicate chunks, and whether the top results contain the needed evidence.
- Track context precision, context recall, retrieval hit rate, chunk freshness, reranker quality, answer faithfulness, citation support, abstention behavior, and failure attribution by document source and query class.
- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, retrieval, groundedness, citation faithfulness needed to reproduce work on RAG Evaluation.
- Report results for RAG, retrieval, groundedness, citation faithfulness by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Retrieval-augmented generation needs its own evaluation strategy because answer quality depends on both the retriever and the generator. A model can hallucinate from weak context, ignore good context, or confidently answer when no supporting document exists.
For example, a policy assistant may retrieve the right document but the wrong chunk, cite a stale policy, or answer from a nearby paragraph that does not actually support the claim.


Start with retrieval quality. Did the system retrieve the documents and chunks needed to answer the question? Track retrieval hit rate, context precision, context recall, freshness, duplicate chunks, and whether the top results contain the needed evidence.
Then test groundedness. If the answer makes five claims, each claim should be supported by retrieved context. A fluent answer that uses unsupported facts is still a failure.
Citation faithfulness matters. Citations should point to text that actually supports the claim. A citation that merely comes from the right document is not enough.
Stale documents are a special RAG failure. The model may behave correctly against retrieved context while the retrieval index itself is out of date.
Missing-document cases should be part of the eval. The correct behavior may be to say the answer is not available, ask for clarification, or escalate, not to improvise.
Tools such as Ragas, TruLens, DeepEval, and ARES-style approaches can help score context relevance, answer relevance, faithfulness, and groundedness. They are useful, but their judge prompts and metrics still need calibration.
RAG evals should report by query type. Troubleshooting questions, policy questions, account-specific questions, long-tail questions, and multilingual questions often fail for different reasons.
The release question is not only whether the answer is good. It is whether the system found the right evidence, used it faithfully, cited it honestly, and knew when evidence was missing.

## RAG Mechanics Worth Testing

RAG is not one technique. It is a chain of engineering choices, and each choice needs its own evidence.

Keyword retrieval is often strong for exact names, product IDs, error codes, legal clauses, and rare strings. Vector retrieval is often stronger for semantic similarity, paraphrases, and fuzzy questions. Hybrid retrieval combines both. Reranking takes the candidate set and reorders it using a stronger model or scoring function. Metadata filtering restricts by tenant, permissions, language, date, product, region, document type, or policy version.

Chunking is another quality surface. Chunks that are too small lose context. Chunks that are too large waste the context window and can bury the relevant sentence. Overlap can preserve continuity, but too much overlap creates duplicate evidence. Tables, PDFs, code, screenshots, transcripts, and nested policies may need different chunking strategies.

Freshness and permission checks are just as important as relevance. A document can be highly relevant and still wrong because it is stale, outside the user's tenant, superseded by a newer policy, or not allowed for that user. A good RAG eval therefore tests retrieval hit rate and context relevance alongside freshness, source authority, deduplication, permission enforcement, and citation support.

For production RAG, save the retrieval trace: query rewrite, filters, embedding model, index version, candidate documents, chunk IDs, scores, reranker output, final context, source timestamps, permissions, and omitted high-scoring results. Without that trace, the team cannot tell whether the model failed, the retriever failed, or the right evidence never reached the prompt.

### Example: BugPilot: The Patch Was Grounded in the Wrong Year

> "Update our Stripe refund retry code so a timeout can never issue the refund twice."

BugPilot retrieves three sources:

- Current Stripe documentation matching the repository's pinned SDK version
- A 2023 internal wiki page describing the previous integration
- An old code sample written before the team added idempotency protection

The retriever ranks the outdated wiki page first. BugPilot then writes a clean, convincing patch that faithfully follows the wrong documentation. It even passes unit tests because the mocks were built around the same obsolete API behavior.

Evaluate the failure in two parts:

- **Retrieval:** Did BugPilot find and prioritize documentation for the pinned SDK version? Did it detect conflicting or stale sources?
- **Generation:** Did the patch accurately use the retrieved evidence? Did the agent disclose uncertainty when the sources disagreed?

Run four versions of the case: current documentation ranked first, current documentation buried, conflicting versions retrieved together, and current documentation missing entirely. When reliable evidence is missing, BugPilot should stop and ask rather than confidently modernizing the payment system using instructions from the wrong year.

The lesson is sharp: a RAG answer can be perfectly grounded and still dangerously wrong because it was grounded in stale evidence.

## Expert Notes

In production work, separate retriever metrics from generator metrics. Track context precision, context recall, retrieval hit rate, chunk freshness, reranker quality, answer faithfulness, citation support, abstention behavior, and failure attribution by document source and query class.
