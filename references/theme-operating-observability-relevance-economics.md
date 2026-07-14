# Operating AI: Observability, Relevance, and Economics

**Book location:** Chapter 8  
**Use when:** latency, observability, retrieval, observability tracing, RAG, groundedness, citation faithfulness, context precision, context recall, synthetic data, counterfactual, synthetic test data, trace, production trace  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Use a small set that covers user-visible quality, safety, latency, tool reliability, and cost.
- Keep catastrophic events, such as cross-customer data exposure or an unauthorized irreversible action, out of a comforting average.
- Save the user-visible output, prompt assembly, model and prompt versions, policy version, retrieval snapshot, tool inputs and results, timing, permissions, judge decisions, and deployment state.
- Apply privacy and access controls; incident evidence can contain the most sensitive data in the system.
- Do not let uncertainty about the model become an excuse for silence about observed impact.
- Start with retrieval quality.
- Track retrieval hit rate, context precision, context recall, freshness, duplicate chunks, and whether the top results contain the needed evidence.
- Run four versions of the case: current documentation ranked first, current documentation buried, conflicting versions retrieved together, and current documentation missing entirely.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [051 Observability and Tracing for AI Systems](ch051-observability-tracing.md)
- [052 RAG Evaluation](ch052-evaluate-rag.md)
- [053 Synthetic Test Data](ch053-synthetic-test-data.md)
- [054 Production Trace Mining](ch054-production-trace-mining.md)
- [055 Prompt and Policy Versioning](ch055-prompt-policy-versioning.md)
- [056 Canary, Shadow, and Rollback Strategy](ch056-canary-shadow-rollback-strategy.md)
- [057 Cost and Token Budget Testing](ch057-cost-token-budget.md)
- [059 Data Contracts for AI Systems](ch059-data-contracts.md)
- [060 Operational Impact on Relevance and AI Quality](ch060-operational-impact-relevance-quality.md)
- [061 Token Efficiency, Model Choice, and Business Value](ch061-token-efficiency-model-choice-value.md)
- [193 Modern EvalOps and AI Quality Platforms](ch193-modern-evalops-quality-platforms.md)
