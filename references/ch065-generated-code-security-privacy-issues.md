# Section 65: AI-Generated Code Security and Privacy Issues

**Book location:** Chapter 9, Generated Code Changes the Job  
**Use when:** generated code, code security, generated code security privacy issues  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI-generated code can create security and privacy risks because it often chooses the easiest
working pattern, not the safest production pattern.

## Actions

- Test role boundaries, tenant boundaries, ownership checks, and object-level permissions.
- Test abuse cases, not just normal use.
- Ask what a malicious user, tenant, employee, or prompt-injected document could do with this path.
- Ask it to stop acting like the implementer and act like the reviewer: find the missing validation, unsafe default, permission gap, logging leak, dependency risk, or abuse case.
- Treat generated code as a plausible first draft, then force it through the checks the example never had.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for generated code, code security, generated code security privacy issues needed to reproduce work on AI-Generated Code Security and Privacy Issues.
- Report results for generated code, code security, generated code security privacy issues by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Security bugs in AI-generated code are common because the model may produce code that is functionally plausible but unsafe under attack. It may skip authorization, trust user input, leak secrets, or handle sensitive data casually.
For example, generated admin-route code may check whether a user is logged in but forget to check whether that user is allowed to perform the admin action.

The first security check is authorization. Generated code often authenticates the user and then assumes that is enough. Test role boundaries, tenant boundaries, ownership checks, and object-level permissions.
Input handling is another hotspot. Look for SQL injection, prompt injection, command injection, unsafe file paths, unescaped HTML, unsafe deserialization, and weak validation.
Secrets handling deserves special attention. AI-generated code may put API keys in examples, logs, URLs, client-side code, test fixtures, or environment defaults.
Privacy bugs often come from logging. The code may log full prompts, documents, account data, medical-style text, or internal records to make debugging easier. That is dangerous in AI systems because prompts can contain everything.
Generated code may also weaken protections with convenient defaults: permissive CORS, disabled TLS verification, broad OAuth scopes, long-lived tokens, or catch-all admin permissions.
Test abuse cases, not just normal use. Ask what a malicious user, tenant, employee, or prompt-injected document could do with this path.
Security scanning helps, but AI-generated risk also needs threat modeling. Many failures are logical authorization mistakes that generic scanners will not understand.
The rule is simple: any AI-generated code that touches identity, money, data access, tools, files, prompts, or logs deserves security review.

## Quick Applied Example


## Expert Notes

At scale, pair static analysis and dependency scanning with abuse-case tests, authorization matrices, secret scanning, log redaction checks, prompt-injection tests, and human security review for high-risk code paths.

Also force the coding agent to review its own patch with a skeptical security and privacy lens. Ask it to stop acting like the implementer and act like the reviewer: find the missing validation, unsafe default, permission gap, logging leak, dependency risk, or abuse case. This often works because the agent, like many human developers, can miss risks while focused on adding the feature, then catch them when explicitly asked to critique the finished change.

> **Example code is not production code.** AI has trained on enormous amounts of sample code, tutorial code, and short snippets. That code is usually written to demonstrate one idea quickly. It is often functional, generic, and brief by design, which means it may skip the boring production obligations: parameter validation, authorization, tenant boundaries, rate limits, secret handling, privacy controls, abuse cases, and error paths. The model may have learned the shape of code that works in a blog post, not the shape of code that survives production. Treat generated code as a plausible first draft, then force it through the checks the example never had.
