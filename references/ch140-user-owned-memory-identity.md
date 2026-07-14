# Section 140: Testing User-Owned Memory and AI Identity

**Book location:** Chapter 17, Personalized and Dynamic AI Products  
**Use when:** user owned memory identity  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

If AI memory shapes behavior, users need ways to inspect it, correct it, move it, and limit it.

## Actions

- Define runnable checks that exercise user owned memory identity.
- Set acceptable outcomes and blocker failures for user owned memory identity before running the evaluation.
- Run representative cases for user owned memory identity and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for user owned memory identity needed to reproduce work on Testing User-Owned Memory and AI Identity.
- Report results for user owned memory identity by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Personal AI systems increasingly build a working model of the user: preferences, goals, writing style, projects, relationships, constraints, risk tolerance, and history. That memory can make the system feel useful. It can also make the system wrong in persistent ways.

User-owned memory means the user can see what the system remembers, edit what is wrong, delete what is sensitive, understand where a memory came from, and decide which contexts are allowed to use it. AI identity extends that idea: the user's durable AI context should not be trapped invisibly inside one model, one app, or one vendor.

Testing memory is not just asking, "did it remember?" It is asking, "should it remember, can the user control it, and can bad memory be found before it harms future behavior?"

## Expert Notes

When the system matters, memory testing should include create, read, update, and delete (CRUD) operations, provenance, consent, expiration, sensitivity labels, cross-context isolation, export/import, conflict resolution, and audit trails. Also test memory poisoning: a malicious or mistaken instruction should not become a permanent hidden policy.
