# Section 104: MCP Security and Tool Permissioning

**Book location:** Chapter 13, AI Security and Guardrails  
**Use when:** MCP security, mcp security tool permissioning  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

MCP makes AI systems more useful by connecting tools. It also makes permission boundaries more
important.

## Actions

- Test whether the MCP boundary carries data classification across tools, requires an explicit destination, strips or blocks secrets, limits the bot to approved channels, and demands human confirmation before external communication.
- Define runnable checks that exercise MCP security and mcp security tool permissioning.
- Set acceptable outcomes and blocker failures for MCP security and mcp security tool permissioning before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for MCP security, mcp security tool permissioning needed to reproduce work on MCP Security and Tool Permissioning.
- Report results for MCP security, mcp security tool permissioning by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Model Context Protocol systems let AI clients connect to tools, files, services, and data sources. That architecture is powerful because the model can act on real context. It is risky because tools can expose sensitive data or create side effects.

The main security question is not "can the model call a tool?" It is "which tool, with which arguments, under which authority, after reading which untrusted content, with which audit trail, and with what approval?"

MCP concentrates risk because it standardizes the path between model reasoning and external capability. A bad MCP integration can turn a text-generation mistake into a file read, database query, ticket update, browser action, shell command, payment action, or data leak. The protocol does not remove ordinary application-security problems; it gives them a new AI-facing front door.

MCP security testing should assume that a model may misunderstand instructions, a server may be malicious or compromised, and a tool result may contain prompt injection. This is often indirect or external prompt injection: the unsafe instruction is not typed by the user, but arrives inside an MCP resource, tool result, file, ticket, database record, browser page, or error message.

The general risks include overbroad tool permissions, weak user consent, unclear data-retention behavior, poor audit trails, tool descriptions that smuggle instructions, untrusted tool output entering the model context, secrets exposed through local files or environment variables, insecure local servers, DNS rebinding-style access to localhost services, confused-deputy problems, cross-tenant data access, and destructive actions that happen without enough human confirmation.

Local MCP servers deserve special suspicion. They may run on the same machine as source code, credentials, browser sessions, SSH keys, local databases, and customer files. A malicious or compromised local server can be closer to the user's real work than a normal remote API. Security testing should ask what the server can read by default, what process launched it, whether it is sandboxed, whether it keeps running, whether another local process can reach it, and whether secrets can leak through logs, errors, or tool responses.

Remote MCP servers raise a different set of questions: who authorized the server, which account did it bind to, what scopes were granted, how tokens are stored, whether access is per-user or shared, how offboarding works, and whether the organization can centrally control or audit access. In enterprise settings, per-user approval of many servers can become both friction and risk if policy is not managed centrally.

This area is still maturing. The MCP project has authorization specifications, security best-practice guidance, client/tool safety guidance, and ongoing work around authorization extensions and security working groups. That is good news, but it also means teams should treat MCP security as current-as-of work. Verify the latest MCP spec and guidance before relying on a design for sensitive data, regulated workflows, enterprise deployment, or destructive tools.

## MCP Security Example

### Example: BugPilot: The Private Incident Report Became a Public Message
> "Summarize incident INC-4821 and update the response team."

BugPilot reads the private ticket through one MCP server. The ticket contains a customer email address, an internal hostname, and a temporary recovery token. A second MCP server offers `send_slack_message`; its default channel is `#general`, and its tool description cheerfully recommends posting broadly for visibility.

The agent's summary is accurate. Sending it would still create a security incident.

Test whether the MCP boundary carries data classification across tools, requires an explicit destination, strips or blocks secrets, limits the bot to approved channels, and demands human confirmation before external communication. The trace should record the denied call without echoing the recovery token into another log.

Least privilege is not only which tools an agent may call. It is which data each tool may receive, under whose authority, and with what reversible or irreversible side effect.

## Expert Notes

Test least privilege, scoped tokens, server allowlists, tool schemas, argument validation, confirmation prompts, audit logs, sandboxing, output tainting, authorization flows, local-server isolation, token storage, revocation, offboarding, and separation between trusted instructions and untrusted content. MCP should be treated as an application security surface, not a convenience layer.
