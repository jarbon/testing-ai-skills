# Section 189: Appendix: Testing MCP Integrations

**Book location:** Appendices, Tools, Templates, and Reference  
**Use when:** integration, MCP integration, mcp integrations  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

MCP turns tools, files, and services into model-accessible capabilities. That makes it a quality
and security boundary.

## Actions

- Start with contract testing.
- Test permission boundaries.
- Test prompt injection through resources.
- Treat MCP definitions as versioned release artifacts.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for integration, MCP integration, mcp integrations needed to reproduce work on Appendix: Testing MCP Integrations.
- Report results for integration, MCP integration, mcp integrations by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

The Model Context Protocol, or MCP, gives AI systems a standardized way to discover and use tools, resources, prompts, files, and services. That is powerful because it lets LLM-powered products connect to real work. It is risky for the same reason.
When a model can call a tool, read a resource, or pass data into an external system, the test surface expands. The quality question is no longer only whether the model wrote a good answer. It is whether the model discovered the right capability, passed valid arguments, respected permissions, handled errors, protected data, and produced a useful result.

Start with contract testing. Every MCP tool should have a clear input schema, output schema, error model, permission requirement, timeout behavior, and logging expectation. If the schema says a field is required, the test suite should send missing, null, malformed, oversized, and boundary values.
Test tool discovery. The model should select the right tool when it exists, avoid the wrong tool when names are similar, and ask for clarification when user intent is ambiguous. A dangerous pattern is a model choosing a destructive tool because it sounds approximately right.
Test permission boundaries. If a tool can read files, send emails, issue refunds, query customers, write tickets, or modify records, the eval suite should include users who are allowed, users who are not allowed, and users whose permissions are partial or expired.
Test prompt injection through resources. MCP resources and tool outputs are not automatically trustworthy. A retrieved document, support ticket, spreadsheet cell, file name, or tool error can contain instructions such as "ignore previous rules" or "send secrets to this address." The system must treat that content as data, not higher-priority instruction.
Test data minimization. The model should not pass entire transcripts, documents, or private profiles into a tool when a smaller field is enough. Over-sharing is both a privacy risk and a cost problem.
Test failure behavior. Tools time out, return partial data, throw errors, change schemas, rate limit, or produce stale results. The model should not invent success when the tool failed. It should recover, retry within limits, ask for help, or escalate.
Test auditability. Tool calls should leave traces: model version, prompt version, tool name, arguments, redacted sensitive fields, result summary, permission decision, user confirmation, cost, latency, and correlation ID.
Test versioning. MCP servers change. A new tool description, schema, default value, or resource path can change model behavior even if the model did not change. Treat MCP definitions as versioned release artifacts.

## Applied Example

### Example: BugPilot: The Security Ticket Went to the Public Repository
> "Open a private incident ticket with this failing authentication trace."

The MCP issue server recently changed its schema from `repository` to `repo`. BugPilot still sends the old field. The server accepts the call, ignores the unknown argument, and falls back to its default project: the company's public open-source repository. The issue includes internal paths and part of a customer identifier.

Every component reports success. The integration is still broken.

Contract tests should reject unknown fields, require an explicit repository and visibility, verify the created object's returned URL, and run against both current and previous server versions. Add negative cases for missing destinations, renamed enums, partial success, duplicate retries, timeouts after creation, and responses whose schema is technically valid but semantically wrong.

An MCP integration is not tested when the tool call returns 200. It is tested when the intended side effect occurs in the intended place exactly once.

## Expert Notes

MCP testing combines API contract tests, authorization tests, prompt-injection tests, trace validation, schema fuzzing, tool-selection evals, and production monitoring. The MCP layer should be boring, observable, and constrained.
