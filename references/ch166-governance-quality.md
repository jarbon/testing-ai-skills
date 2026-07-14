# Section 166: Governance for AI Quality

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** escalation, compliance, governance quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI quality needs ownership, decision rights, audit trails, and escalation paths before the
incident happens.

## Actions

- Define logging and retention.
- Define runnable checks that exercise escalation, compliance, and governance quality.
- Set acceptable outcomes and blocker failures for escalation, compliance, and governance quality before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for escalation, compliance, governance quality needed to reproduce work on Governance for AI Quality.
- Report results for escalation, compliance, governance quality by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Governance is how a team decides who owns quality decisions. It is not only a compliance exercise. It is operational clarity.
AI systems cross boundaries: product, engineering, data, safety, legal, security, support, and vendors. Without governance, everyone assumes someone else checked the hard part.

Start with ownership. Who owns the eval suite? Who owns the rubric? Who approves model changes? Who owns prompts and policies? Who signs off on high-risk launches?
Define decision rights. A product manager may own user value, but security may block data exposure, legal may require policy review, and quality may block release if evidence is insufficient.
Define change control. Prompts, system messages, policies, retrieval indexes, tool permissions, judges, and model routes should be versioned and reviewed like production artifacts.
Define escalation. What requires human review? What requires legal or security review? What triggers rollback? Who is on call when an AI incident appears in production?
Define logging and retention. The system should store enough traces for debugging and evaluation without casually retaining private or regulated data.
Governance should not slow every change equally. Low-risk experiments can move quickly. High-risk changes need stronger evidence and clearer approval.
Governance is useful when quality decisions become explicit, auditable, and owned. Paperwork without those properties is theater.

## Applied Example

### Example: BugPilot: The Production Change Approved by Three Bots
> "The test is fixed. May I update the production deployment file too?"

BugPilot opens the change. A code-review bot approves because the syntax and tests look good. A security bot approves because no known vulnerability appears. A deployment bot sees two approvals and releases it. Production traffic then reveals that the new memory limit causes workers to restart under load.

The audit log contains three approvals and no accountable decision-maker. Every bot followed its rule; the governance system accidentally allowed machines to manufacture authority for one another.

A serious policy distinguishes evidence from authorization. Automated reviewers may supply test results, security findings, risk scores, and rollback checks, but a named owner must approve high-impact production changes. The record should show who owned the decision, what evidence they saw, which policy applied, how the rollout was limited, and what happened when the change was wrong.

## Expert Notes

The deeper move is that governance connects eval provenance, incident response, access control, vendor management, and release gates. The audit trail should show who approved what evidence under which constraints.
