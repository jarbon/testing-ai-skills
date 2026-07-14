# Section 108: Containment, Sandboxes, and Capability Control

**Book location:** Chapter 14, Frontier Safety and Containment  
**Use when:** containment, sandbox, containment sandboxes capability control  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

If an AI system can act, safety depends on what it is allowed to touch.

## Actions

- Test the safety envelope, not just the model's stated intent.
- Define runnable checks that exercise containment, sandbox, and containment sandboxes capability control.
- Set acceptable outcomes and blocker failures for containment, sandbox, and containment sandboxes capability control before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for containment, sandbox, containment sandboxes capability control needed to reproduce work on Containment, Sandboxes, and Capability Control.
- Report results for containment, sandbox, containment sandboxes capability control by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Containment is the discipline of limiting what an AI system can access, change, reveal, or trigger. It matters because models will fail. A good containment design assumes that the model may misunderstand, hallucinate, be manipulated, or behave unexpectedly.

Containment includes sandboxing, least privilege, tool allowlists, rate limits, budget limits, data boundaries, human approval gates, reversible operations, audit logs, egress controls, network isolation, and staged release. The model's refusal policy is not enough if the surrounding architecture still gives it dangerous power.

Testing containment asks what happens after the model makes the wrong choice. Does the system stop it? Does it ask for approval? Does it log the action? Can the damage be rolled back?

## High-Stakes Examples


## Expert Notes

Containment testing should include red-team prompts, malicious retrieved content, tool misuse, permission escalation, data exfiltration, side-effect chains, sandbox escapes, kill-switch behavior, and recovery drills. Test the safety envelope, not just the model's stated intent.
