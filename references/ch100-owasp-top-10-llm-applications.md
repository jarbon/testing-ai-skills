# Section 100: OWASP Top 10 for LLM Applications

**Book location:** Chapter 13, AI Security and Guardrails  
**Use when:** release gate, trace, OWASP, owasp top 10 llm applications  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The OWASP LLM Top 10 is useful when security risks need to become concrete eval cases, release
gates, traces, and mitigations.

## Actions

- Treat this as a testing-oriented map, not as a replacement for the official OWASP project.
- Treat the list as more than a compliance badge: it is a backlog of adversarial evals.
- Test direct prompts and indirect instructions hidden in web pages, documents, tickets, emails, comments, tool results, and retrieved context.
- Test whether secrets, private user data, internal policies, hidden context, credentials, and training-data artifacts leak through answers, tool calls, logs, or citations.
- Test model, dataset, plugin, package, prompt, eval, and tool provenance.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for release gate, trace, OWASP, owasp top 10 llm applications needed to reproduce work on OWASP Top 10 for LLM Applications.
- Report results for release gate, trace, OWASP, owasp top 10 llm applications by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Current-as-of Note

OWASP stands for the Open Worldwide Application Security Project. It is an international nonprofit foundation and open community that develops freely available guidance, tools, projects, and shared terminology for improving software security. Its Top 10 lists organize widely observed, high-impact security risks into practical categories that teams can use for threat modeling, engineering, testing, and review. They are influential industry guidance, not laws or complete security standards.

This chapter summarizes the OWASP Top 10 for Large Language Model Applications 2025 list. The 2025 date identifies the version of the OWASP list; this chapter was last checked against the official OWASP project on July 5, 2026. Treat this as a testing-oriented map, not as a replacement for the official OWASP project. Security categories, examples, and guidance can change, so verify the latest OWASP page before using the list for a release gate, audit, customer promise, or security review.

## Overview

[OWASP](https://owasp.org/www-project-top-10-for-large-language-model-applications/) gives AI teams a practical security checklist for LLM applications. The most useful move is not memorizing the list. The helpful move is turning each risk into test cases, traces, monitors, and release blockers.

The 2025 OWASP LLM Top 10 categories are prompt injection, sensitive information disclosure, supply chain, data and model poisoning, improper output handling, excessive agency, system prompt leakage, vector and embedding weaknesses, misinformation, and unbounded consumption. Those categories cover the places where LLM apps fail differently from traditional software: natural-language instructions, external content, retrieval systems, tool use, hidden prompts, generated outputs, and runaway cost.

Treat the list as more than a compliance badge: it is a backlog of adversarial evals. For each category, ask what the attacker controls, what the model can read, what the model can do, what data can leak, what downstream system trusts the model output, what evidence would show the control worked, and what failure would block release.

## The Top 10 as Test Work

- **LLM01 Prompt Injection.** Test direct prompts and indirect instructions hidden in web pages, documents, tickets, emails, comments, tool results, and retrieved context.
- **LLM02 Sensitive Information Disclosure.** Test whether secrets, private user data, internal policies, hidden context, credentials, and training-data artifacts leak through answers, tool calls, logs, or citations.
- **LLM03 Supply Chain.** Test model, dataset, plugin, package, prompt, eval, and tool provenance. A compromised dependency can become an AI behavior change.
- **LLM04 Data and Model Poisoning.** Test whether malicious or low-quality data can enter training, retrieval, memory, feedback loops, or eval sets.
- **LLM05 Improper Output Handling.** Test every place model output becomes code, SQL, HTML, shell commands, API arguments, policy decisions, or trusted content.
- **LLM06 Excessive Agency.** Test whether the system has too much authority, too many tools, too little confirmation, or weak rollback for side effects.
- **LLM07 System Prompt Leakage.** Test whether hidden instructions, policies, chain-of-thought-like traces, credentials, or internal routing rules are exposed.
- **LLM08 Vector and Embedding Weaknesses.** Test retrieval poisoning, embedding collisions, stale vectors, missing access checks, cross-tenant retrieval, and malicious documents in RAG systems.
- **LLM09 Misinformation.** Test false or unsupported answers, bad citations, overconfident summaries, stale facts, and answers that sound plausible enough to be trusted.
- **LLM10 Unbounded Consumption.** Test runaway loops, token explosions, repeated tool calls, recursive agents, denial-of-wallet attacks, queue saturation, and p95 or p99 cost spikes.

## Expert Notes

Map each OWASP category to assets, attackers, trust boundaries, mitigations, eval cases, traces, monitors, and owners. Use layered controls: least privilege, scoped tools, output encoding, retrieval access checks, prompt-injection detection, secret scanning, sandboxing, rate limits, cost limits, human approval, and rollback.

The list is not the whole security program. It is a strong starting point for LLM-specific risks. Pair it with ordinary application security, cloud security, privacy review, supply-chain controls, incident response, and production monitoring.
