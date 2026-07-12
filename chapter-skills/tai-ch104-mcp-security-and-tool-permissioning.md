---
name: tai-ch104-mcp-security-and-tool-permissioning
description: 'Apply chapter 104 of Testing AI, MCP Security and Tool Permissioning, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to mcp security and tool permissioning.'
---

# MCP Security and Tool Permissioning

Skill name: `tai-ch104-mcp-security-and-tool-permissioning`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

MCP makes AI systems more useful by connecting tools. It also makes permission boundaries more
important.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Model Context Protocol systems let AI clients connect to tools, files, services, and data
sources. That architecture is powerful because the model can act on real context. It is risky
because tools can expose sensitive data or create side effects.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Test least privilege, scoped tokens, server allowlists, tool schemas, argument validation,
confirmation prompts, audit logs, sandboxing, output tainting, authorization flows, local-server
isolation, token storage, revocation, offboarding, and separation between trusted instructions
and untrusted content. MCP should be treated as an application security surface, not a
convenience layer.
