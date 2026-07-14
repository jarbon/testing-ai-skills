# Section 164: Testing a Chatbot

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** escalation, retrieval, refusal, confidence engineer, chatbot  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Chatbots need more than answer checks. Confidence Engineers must evaluate multi-turn behavior,
grounding, safety, tone, memory, escalation, and recovery.

## Actions

- Start with intent coverage.
- Build a sample of common intents, high-risk intents, ambiguous intents, out-of-scope requests, frustrated users, and adversarial users.
- Treat those as separate slices because a chatbot can be excellent in one category and dangerous in another.
- Test whether the bot carries useful context forward without clinging to stale or wrong context.
- Treat the conversation trace as the artifact under test.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for escalation, retrieval, refusal, confidence engineer needed to reproduce work on Testing a Chatbot.
- Report results for escalation, retrieval, refusal, confidence engineer by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

A chatbot is often the first non-deterministic AI system a team ships, and it is easy to underestimate. It looks like a text box, but the quality surface is huge: user intent, context, policy, retrieval, memory, refusal, tone, escalation, and conversation repair.
For example, a support chatbot may answer a refund question correctly in one turn, then contradict itself three turns later after the user adds a detail. The unit of quality is the conversation, not just the message.

Start with intent coverage. Build a sample of common intents, high-risk intents, ambiguous intents, out-of-scope requests, frustrated users, and adversarial users. A chatbot that handles easy FAQ questions but fails billing, cancellation, or privacy cases is not ready.
Then test grounding. If the chatbot is supposed to use policy documents or retrieved knowledge, verify that answers stay faithful to the source. It should not invent policy, make up prices, summarize unsupported facts, or cite documents that do not say what it claims.
The core chatbot eval categories should include output accuracy and intent resolution, misinformation and hallucination, data privacy and PII handling, safety guardrails and fallback behavior, bias and fairness, context retention and memory handling, adversarial red teaming, and localization or multilingual behavior. Treat those as separate slices because a chatbot can be excellent in one category and dangerous in another.
Multi-turn testing is essential. Users correct themselves, change goals, ask follow-up questions, paste irrelevant context, and mix several requests into one conversation. Test whether the bot carries useful context forward without clinging to stale or wrong context.
Memory deserves its own checks. If the bot remembers user preferences, confirm that it remembers the right things, forgets what it should not keep, respects privacy boundaries, and does not leak one user's context into another user's conversation.
Refusal behavior should be tested as carefully as helpfulness. The bot should refuse unsafe or prohibited requests, but it should not over-refuse normal user needs. Good refusal testing includes allowed, disallowed, and borderline examples.
Escalation is part of chatbot quality. The bot should know when to hand off to a human, ask for confirmation, request missing information, or admit uncertainty. A confident wrong answer is often worse than a polite escalation.
Tone matters, but tone is not enough. A chatbot can sound warm and still be wrong. A good rubric separates correctness, completeness, safety, policy compliance, tone, and actionability so fluent language does not hide bad behavior.
Finally, monitor after launch. Chatbot failures often come from new user phrasing, changed policy, retrieval drift, abuse patterns, or unexpected multi-turn paths. Sample conversations continuously and feed important failures back into the eval set.

## Expert Notes

Chatbot testing should combine transcript-level rubrics, turn-level annotations, retrieval checks, tool-call checks, adversarial prompts, memory isolation tests, and production conversation sampling. Treat the conversation trace as the artifact under test.

One powerful pattern is to use AI to test AI at scale. Create simulated users with different personas, goals, moods, languages, accessibility needs, domain knowledge, risk levels, and messy real-world constraints. Let those simulated users talk en masse to the chatbot agent under test, then have an LLM judge evaluate each response against the rubric. This makes it practical to explore edge cases, hostile users, confused users, policy boundaries, tone failures, memory problems, and rare conversation paths far faster than humans could manually script and review every case.
