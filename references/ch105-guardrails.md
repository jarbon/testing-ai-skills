# Section 105: Guardrails for AI Systems

**Book location:** Chapter 13, AI Security and Guardrails  
**Use when:** monitoring, human review, guardrail, guardrails  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Guardrails are the code, policy, permissions, human review, and telemetry around a model that
limit what bad outputs can do.

## Actions

- Test bypasses, race conditions, stale state, confusing warnings, over-trusted operators, malformed inputs, fast repeated actions, and cases where the system says something vague like "minor issue" when the correct behavior is to stop hard.
- Do not rely on one guardrail.
- Use defense in depth: product boundaries, model instructions, retrieval filtering, tool permissions, output checks, human approval, sandboxing, monitoring, and rollback.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for monitoring, human review, guardrail, guardrails needed to reproduce work on Guardrails for AI Systems.
- Report results for monitoring, human review, guardrail, guardrails by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Guardrails are the layers around an AI system that constrain behavior. They can appear before the model, around the model, after the model, around tools, inside the UI, and in production monitoring. A guardrail might block a prompt, redact private data, refuse a harmful request, require human approval, constrain a tool call, validate a schema, check a citation, rate-limit abuse, or escalate a risky case.


The developer mistake is treating guardrails as a switch: "we added safety." In real AI systems, guardrails are another non-deterministic system surface. They can be too weak, too strict, inconsistent, bypassable, expensive, slow, stale, or poorly logged. They can also create product failures when they block legitimate users or hide useful evidence from the team.

Good guardrail testing asks five questions.

- **What should be allowed?** The system should still help normal users complete legitimate tasks.
- **What should be blocked?** The system should stop unsafe, illegal, private, abusive, or out-of-policy behavior.
- **What should be escalated?** Some cases should go to a human, a higher-trust workflow, or a safer model.
- **What should be constrained?** Tool calls, actions, files, accounts, money movement, medical claims, and physical actions need explicit limits.
- **What should be logged?** The team needs enough trace evidence to debug failures, audit decisions, and improve the system later.

Guardrails should not be judged only by refusal rate. A system that refuses everything is safe in the most useless possible way. A system that never refuses is often convenient right up until it creates a severe incident. The target is calibrated control: allow the right things, block the wrong things, escalate ambiguous things, and preserve evidence.

## Types of Guardrails

Input guardrails inspect the user's request before it reaches the model. They can detect secrets, prompt injection, regulated topics, abuse, malware requests, self-harm signals, or unsupported workflows.

Prompt and policy guardrails shape the model's instructions. They include system messages, developer instructions, policy snippets, tool-use rules, and refusal guidance.

Retrieval guardrails control what context can enter the prompt. They can filter stale documents, untrusted web content, private records, low-confidence retrieval, or injected instructions inside documents.

Tool guardrails control what the model can do. They include tool schemas, least-privilege scopes, allowlists, confirmation steps, transaction limits, dry-run modes, sandboxes, and human approval.

Output guardrails inspect generated content before the user or tool receives it. They can check citations, privacy leakage, unsafe advice, hallucinated claims, policy violations, tone, format, and schema validity.

Monitoring guardrails watch production behavior over time. They track refusal rates, escalation rates, severe failures, abuse patterns, cost spikes, latency, drift, slice regressions, and rollback thresholds.

## Case Study: Therac-25

In the 1980s, the Therac-25 radiation therapy machine caused several serious radiation overdoses. One reason the failures became so dangerous was that safety had moved heavily into software. Earlier systems had more independent hardware interlocks. Therac-25 depended on software checks, operator workflow, and error messages that did not make the danger clear enough.

The lesson is not "software is bad." The lesson is that software safety cannot depend on the same system confidently judging itself safe. When consequences are high, safety needs independent layers: physical interlocks, permission boundaries, rate limits, human confirmation, audit logs, impossible-state checks, and fail-safe defaults.

That is the AI guardrail lesson. A chatbot policy, moderation classifier, system prompt, LLM judge, or "are you sure?" self-check is useful, but it is not enough when the action can hurt people, move money, expose private data, delete files, or make medical claims. The model should not be the only thing standing between a fluent mistake and a real-world consequence.

Guardrails should be tested like product code and safety infrastructure. Test bypasses, race conditions, stale state, confusing warnings, over-trusted operators, malformed inputs, fast repeated actions, and cases where the system says something vague like "minor issue" when the correct behavior is to stop hard.

Source: [Therac-25](https://en.wikipedia.org/wiki/Therac-25)

## Expert Notes

At scale, guardrail testing is control-system testing. Each control needs an owner, a purpose, a threat model, an allowed behavior set, a blocked behavior set, a fallback, a log schema, and a way to detect drift.

Do not rely on one guardrail. Use defense in depth: product boundaries, model instructions, retrieval filtering, tool permissions, output checks, human approval, sandboxing, monitoring, and rollback. Also test the gaps between layers. Many incidents happen when each layer technically works but the combined workflow still allows harm.

The hardest guardrail bugs are calibration bugs. Over-blocking makes the product useless or unfair. Under-blocking creates safety risk. Silent blocking hides failures from users and engineers. The best guardrails are visible enough to debug, narrow enough to preserve usefulness, and measured enough to improve.
