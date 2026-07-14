# Section 190: Agentic Frameworks vs. Parameterized Workflows

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** agentic frameworks parameterized workflows  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Most workflows do not need an autonomous agent. They need a well-bounded procedure with a few
intelligent steps.

## Actions

- Define the workflow as steps.
- Require confirmations for irreversible actions.
- Score the trajectory, not just the final answer.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for agentic frameworks parameterized workflows needed to reproduce work on Agentic Frameworks vs. Parameterized Workflows.
- Report results for agentic frameworks parameterized workflows by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Agentic frameworks are seductive. They promise planning, tool choice, memory, reflection, retries, and autonomy. Sometimes that is exactly what the product needs. Often it is too much machinery for a workflow that already has a known path.
A lot of AI quality problems come from giving the model freedom where the product needed structure. If the task has a stable business process, known steps, known permissions, known tools, and known stopping conditions, a parameterized procedural workflow is usually easier to test, debug, secure, and operate.

The default should be boring. Define the workflow as steps. Put the model inside the steps where judgment or language understanding is useful. Pass parameters. Validate outputs. Check permissions. Log every step. Stop when the procedure is done.
For example, a refund workflow does not need an agent wandering through tools. It can follow a procedure: authenticate user, retrieve order, check policy, classify exception, compute eligible amount, ask for confirmation, call refund tool, write audit note, notify user. The LLM may help classify the user request and draft the explanation, but the workflow owns the control flow.
This is easier to test. Each step has expected inputs, outputs, errors, permissions, and invariants. The eval suite can test edge cases at each boundary instead of trying to infer why an autonomous trajectory went sideways.
Agentic frameworks make more sense when the path is not known in advance: open-ended research, exploratory debugging, multi-source investigation, planning under uncertainty, or tasks where the system must decide which path to take from a large action space.
Even then, autonomy should be bounded. Limit tools. Limit retries. Require confirmations for irreversible actions. Use budgets. Score the trajectory, not just the final answer. Prefer a planner with constraints over an unconstrained loop.
The mistake I see teams make is agent cosplay: wrapping a simple form fill, policy lookup, or support workflow in a general agent loop because it sounds advanced. That usually increases variance, cost, latency, security risk, and test difficulty.
Parameterized workflows also make compliance easier. It is clearer who approved an action, which rule fired, which data was used, and why the system stopped. With a free-roaming agent, the explanation often becomes a reconstructed story rather than an actual control record.
A good rule of thumb: if a human operator would follow a checklist, build a parameterized workflow. If a human expert would need to investigate, choose sources, form hypotheses, and adapt strategy, consider a bounded agent.

## Applied Example

### Example: BugPilot: A $47 Investigation of an Expired Fixture
> "Triage the failing `invoice_totals_rounding` test."

The failure signature already exists in the team's catalog: the test fixture contains an exchange rate that expires on the first day of each quarter. A parameterized workflow can match the signature, refresh the fixture from the approved snapshot, rerun the test, and open a maintenance issue if it passes.

Instead, the team gives the task to a fully agentic BugPilot. It launches three subagents, searches the repository and the web, reads twelve months of billing changes, spends $47 in model and tool calls, and edits production rounding code so the invalid fixture passes. The pull request is inventive, expensive, and wrong.

Now give the agent a genuinely unfamiliar failure with conflicting logs and no catalog match. That is where hypothesis formation and exploration may earn their cost. Test both cases. The quality question is not whether the agent can act autonomously; it is whether the system knows when autonomy is useful and when a short, parameterized path is safer.

## Expert Notes

At scale, evaluate autonomy as a risk budget. Every degree of freedom needs a reason, a guardrail, an observable trace, and a test. The best AI architecture is often not the most agentic one; it is the one with the smallest amount of autonomy that still solves the user problem.
