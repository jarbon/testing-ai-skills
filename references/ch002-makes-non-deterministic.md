# Section 2: What Makes a System Non-Deterministic?

**Book location:** Chapter 1, The End of One-Run Testing  
**Use when:** determinism, personalization, makes non deterministic  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Before builders can evaluate unpredictable systems, they need to understand where the
unpredictability comes from and which variation actually matters.

## Actions

- Ask the same model to summarize a document ten times and you may get ten different summaries.
- Log the weather snapshot, store inventory, delivery promise, driver state, user location, model route, tool outputs, and policy version.
- Define runnable checks that exercise determinism, personalization, and makes non deterministic.

## Evidence to Produce

- Log the weather snapshot, store inventory, delivery promise, driver state, user location, model route, tool outputs, and policy version.
- Preserve the inputs, versions, configurations, raw outcomes, and results for determinism, personalization, makes non deterministic needed to reproduce work on What Makes a System Non-Deterministic?.
- Report results for determinism, personalization, makes non deterministic by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Non-determinism means repeated runs can produce different behavior, even when the input looks the same. That can happen because of model sampling, personalization, ranking experiments, timing, cache state, tool calls, retrieved data, or hidden production context.
For example, an LLM may choose different words, a search system may reorder equivalent results, and a distributed service may process two events in different orders. Some of that variation is harmless. Some of it changes the truth.

Non-determinism is not one simple category. Some stochastic systems can be made mostly reproducible by fixing the random seed, data snapshot, configuration, and runtime. That is useful for debugging and for reducing sample counts when you are validating a narrow behavior. LLM-based products are trickier. Even with low temperature, they may vary because the provider changed the served model, a safety layer changed, a tool returned different data, retrieval context shifted, hidden state changed, floating-point or hardware behavior differed, or the platform routed the request through a different path. The testing strategy depends on which kind of variation you are trying to control.

AI systems also create a new kind of invisible failure. When a dependency is down, the application may not look broken at all. A chatbot can still generate an answer when search, retrieval, a database, or an external tool is unavailable. The answer may sound fluent, but it may be less grounded, less current, or less useful because the system silently fell back to a weaker path. Testing cannot look only at the final generated response. It also needs to validate fallback behavior, observability, logging, dependency health, and the quality impact of unavailable services.

A deterministic system gives the same output every time you provide the same input under the same conditions. A calculator is the easiest example. If you enter 2 + 2, you expect 4 every time. If a deterministic API receives the same request with the same database state and configuration, you expect the same response.

A non-deterministic system is different. The same input can, and often will, produce different outputs. Sometimes that variation is intentional. Sometimes it is a side effect of timing, randomness, personalization, or hidden state. Sometimes it is a bug.

LLMs are the most visible example. Ask the same model to summarize a document ten times and you may get ten different summaries. Some differences are harmless. The model may choose different wording, sentence order, or examples. Other differences are serious. One summary may omit a key risk, invent a fact, or contradict the source material.

Recommendation systems are also non-deterministic from the Confidence Engineer's point of view. The same user might see different products depending on inventory, ranking experiments, recency, or personalization signals. Search systems may reorder results as indexes update. Fraud models may return slightly different risk scores after retraining. AI agents may call tools in different sequences while still completing the same task.

Distributed systems add another flavor of non-determinism. Events may arrive in different orders. A cache may be warm or cold. A retry may succeed or fail depending on timing. Two services may race. The code may be deterministic locally, but the system behavior is not perfectly repeatable in production.

This matters because much of software testing, correctly, assumes a single expected output. That is still appropriate for many parts of a product, or component or unit test, but it is not enough for systems with acceptable variation. Good teams already made these distinctions in complex systems work. AI makes the distinction harder to ignore and much easier to get wrong at scale. For those systems, builders need to define what must remain stable even when surface behavior changes.

For example, an LLM support assistant may phrase a refund answer in different ways. That is acceptable if the policy stays correct. It is not acceptable if one response says returns are allowed within 30 days and another says 45 days. The words can vary. The business rule cannot.

The evaluator's job is to separate variation from failure. Wording variance may be healthy. Formatting variance may be tolerable. Factual variance, safety variance, privacy variance, and policy variance may be release blockers.

That is the first mental shift in testing non-deterministic systems. You are not only checking one answer. You are evaluating a range of possible behaviors and deciding whether that range is safe, useful, and trustworthy enough for users.

## Examples

### Example: CartCare Chatbot


> "Can I still get my picnic order before the thunderstorm starts?"

The visible input is one sentence, but the answer can change for legitimate reasons. The user's location may move. The weather feed may update. A driver may cancel. Inventory may change after another shopper buys the last ice. The routing model may choose a faster store. The safety policy may decide that chilled food should not sit outside in heat and rain.

That is why debugging the final answer alone is not enough. Log the weather snapshot, store inventory, delivery promise, driver state, user location, model route, tool outputs, and policy version. If the answer changes, the team should know whether the product learned something new about the world or merely wandered.

The test question is not, "Did CartCare say the same words twice?" It is, "Can we explain which moving part changed the answer?"


## Expert Notes

Technically, builders should separate sources of randomness from sources of state and sources of platform change. Model temperature, random seeds, ranking tie-breakers, async timing, retrieval snapshots, feature flags, user profiles, tool outputs, dependency failures, provider model versions, safety filters, hardware/runtime paths, and hidden product context should be logged independently because each one creates a different debugging path. When a system has fallback paths, log which path produced the answer so a fluent but degraded response is not mistaken for a healthy one.
