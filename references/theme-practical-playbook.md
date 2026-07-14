# The Practical Playbook

**Book location:** Chapter 20  
**Use when:** escalation, retrieval, refusal, confidence engineer, chatbot, customer support chatbot, compliance, governance quality, RAG, failure taxonomy, generated code, personalization, always fails, fail-safe  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Start with intent coverage.
- Build a sample of common intents, high-risk intents, ambiguous intents, out-of-scope requests, frustrated users, and adversarial users.
- Treat those as separate slices because a chatbot can be excellent in one category and dangerous in another.
- Test whether the bot carries useful context forward without clinging to stale or wrong context.
- Treat the conversation trace as the artifact under test.
- Score policy correctness, completeness, groundedness, tone, user actionability, and safety.
- Separate blockers such as privacy leakage, unsupported financial promises, and account-security mistakes.
- Compare the old system, new prompt, new model, and lower-cost model.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [164 Testing a Chatbot](ch164-chatbot.md)
- [165 Worked Example: Testing a Customer-Support Chatbot](ch165-customer-support-chatbot.md)
- [166 Governance for AI Quality](ch166-governance-quality.md)
- [167 Failure Taxonomy for AI Systems](ch167-failure-taxonomy.md)
- [168 AI Always Fails](ch168-always-fails.md)
- [169 Failure Modes and Fail-Safe AI](ch169-failure-modes-fail-safe.md)
- [170 Measurement Infrastructure Must Know About Variance](ch170-measurement-infrastructure-must-know-variance.md)
- [171 Performance Engineering for AI Systems](ch171-performance-engineering.md)
- [172 Minimum Viable AI Quality System](ch172-minimum-viable-quality.md)
- [173 Make Testing Interesting](ch173-make-interesting.md)
- [190 Agentic Frameworks vs. Parameterized Workflows](ch190-agentic-frameworks-parameterized-workflows.md)
