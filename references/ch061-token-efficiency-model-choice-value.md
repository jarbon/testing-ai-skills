# Section 61: Token Efficiency, Model Choice, and Business Value

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** latency, model choice, token efficiency model choice value  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The best AI system is not the biggest model or the cheapest model. It is the model path that
creates the most trustworthy value for the risk, cost, latency, and business constraints.

## Actions

- Measure first-token latency, full-response latency, p95 and p99 latency, queueing delay, retry delay, and tool-call delay.
- Compare marginal quality gain against marginal cost, latency, privacy exposure, security risk, regional availability, and continuity risk.
- Track cost per successful outcome, not cost per request.

## Evidence to Produce

- Include retrieval, embeddings, reranking, tool calls, judge passes, caching, storage, human review, failed attempts, retries, monitoring, and incident response.
- Track cost per successful outcome, not cost per request.
- Preserve the inputs, versions, configurations, raw outcomes, and results for latency, model choice, token efficiency model choice value needed to reproduce work on Token Efficiency, Model Choice, and Business Value.
- Report results for latency, model choice, token efficiency model choice value by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Cost and token-budget testing asks whether a workflow can afford to behave the way it behaves. Model-choice testing asks a different question: which model path should do the work at all?

Token efficiency is not just a cost-control exercise. It is a quality and routing strategy. Every prompt, retrieved chunk, tool call, retry, judge pass, and output token consumes time, money, context budget, and operational capacity.
For example, a customer-support agent may answer correctly with a frontier model, 30 retrieved chunks, and three judge passes. That might be acceptable for a high-risk legal escalation. It is probably wasteful for a low-risk password-reset question.

Optimize for trustworthy value per unit of cost, latency, risk, and business constraint, rather than minimizing tokens in isolation.
A cheaper model that creates more escalations is not cheaper. A faster model that causes more refunds is not faster in business terms. A private local model that avoids vendor exposure but gives poor answers may be the right choice for early testing and the wrong choice for production. The Confidence Engineer has to compare quality against value.
This means testing different model families, model sizes, providers, deployment modes, prompts, context lengths, retrieval strategies, and routing policies. The best answer may be a portfolio: small model for classification, medium model for routine support, frontier model for high-risk reasoning, local model for sensitive internal review, and human escalation for cases where automation is not worth the risk.
Latency is part of value. Users experience delay as product quality. Measure first-token latency, full-response latency, p95 and p99 latency, queueing delay, retry delay, and tool-call delay.
Cost is also more than input and output tokens. Include retrieval, embeddings, reranking, tool calls, judge passes, caching, storage, human review, failed attempts, retries, monitoring, and incident response. The real metric is total cost to produce a trustworthy outcome.
Security and privacy belong in the same decision. Some prompts contain customer data, contracts, medical-style records, source code, credentials, private business plans, or regulated information. The cheapest API call may be the wrong call if it moves data into an unacceptable environment.
Region and hosting matter too. Teams should evaluate data residency, data sovereignty, regulatory expectations, customer commitments, and business continuity. A model hosted outside your country or operating region may introduce legal, contractual, latency, support, geopolitical, or continuity risk. That does not make it unusable. It means the risk must be explicit.
Business continuity is often ignored until it hurts. What happens if the provider has an outage, changes pricing, removes a model, changes safety behavior, loses regional availability, or becomes unavailable for procurement or policy reasons? Testing model efficiency includes testing substitution paths.
A mature AI quality report compares model options like a decision table: quality score, severe-failure rate, cost per successful task, p95 latency, context usage, privacy posture, security posture, data residency, vendor risk, operational complexity, and rollback options.
The thing to watch for is optimizing one metric in isolation. The next-generation pattern is choosing the model path that produces the most reliable value under the constraints of the business.

## Model Selection Is a Test Surface

Model selection is not a procurement checkbox. It is a release decision. The same feature may need several model paths: a small classifier, a cheap support model, a frontier model for ambiguous cases, a local model for sensitive data, and a human route when automation should not decide.

Test model options against the job they are supposed to do:

- **Capability:** Does the model solve the target task, including messy user phrasing and edge cases?
- **Reliability:** How much variance appears across repeated runs, slices, languages, and long contexts?
- **Safety:** Does the model refuse correctly without over-refusing useful work?
- **Security and privacy:** Is the data route allowed for this input, tenant, region, and customer promise?
- **Cost and latency:** What is the cost per successful outcome, not merely cost per token?
- **Operations:** Can the route be monitored, rate-limited, cached, rolled back, and replaced?
- **Continuity:** What happens if the provider changes pricing, model behavior, retention policy, or availability?

Build-versus-buy belongs in the same table. A hosted frontier model may be the fastest way to learn. A smaller self-hosted or fine-tuned model may be better for cost, privacy, latency, offline use, or repeatability. A custom model may create ownership and differentiation, but it also creates a model lifecycle to test forever.

For model routers, test the router itself. Send low-risk, high-risk, ambiguous, privacy-sensitive, long-context, multilingual, adversarial, and outage cases. The right route is part of the answer. A great model behind a bad router is still a bad product.

## Expert Notes

In a real release review, build an efficient frontier for AI quality. Compare marginal quality gain against marginal cost, latency, privacy exposure, security risk, regional availability, and continuity risk. Track cost per successful outcome, not cost per request. Maintain fallback models, provider substitution tests, cached-path tests, and region-aware deployment checks so the business can keep operating when a model, vendor, region, or policy changes.
