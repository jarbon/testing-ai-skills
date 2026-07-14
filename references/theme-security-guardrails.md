# AI Security and Guardrails

**Book location:** Chapter 13  
**Use when:** threat model, security threat models, release gate, trace, OWASP, owasp top 10 llm applications, prompt injection, indirect prompt injection, untrusted context, tool injection, trust boundary, RAG, synthetic data, data poisoning  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Define runnable checks that exercise threat model and security threat models.
- Set acceptable outcomes and blocker failures for threat model and security threat models before running the evaluation.
- Run representative cases for threat model and security threat models and preserve the failures that would change the decision.
- Treat this as a testing-oriented map, not as a replacement for the official OWASP project.
- Treat the list as more than a compliance badge: it is a backlog of adversarial evals.
- Test direct prompts and indirect instructions hidden in web pages, documents, tickets, emails, comments, tool results, and retrieved context.
- Test whether secrets, private user data, internal policies, hidden context, credentials, and training-data artifacts leak through answers, tool calls, logs, or citations.
- Test model, dataset, plugin, package, prompt, eval, and tool provenance.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [099 AI Security Threat Models](ch099-security-threat-models.md)
- [100 OWASP Top 10 for LLM Applications](ch100-owasp-top-10-llm-applications.md)
- [101 Prompt Injection and Indirect Prompt Injection](ch101-prompt-injection-indirect-prompt-injection.md)
- [102 Training Data Poisoning and Backdoors](ch102-training-data-poisoning-backdoors.md)
- [103 Model Provenance, Geopolitical, and Nation-State Risk](ch103-model-provenance-geopolitical-nation-risk.md)
- [104 MCP Security and Tool Permissioning](ch104-mcp-security-tool-permissioning.md)
- [105 Guardrails for AI Systems](ch105-guardrails.md)
