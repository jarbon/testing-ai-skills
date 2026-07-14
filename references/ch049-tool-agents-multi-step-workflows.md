# Section 49: Tool-Using Agents and Multi-Step Workflows

**Book location:** Chapter 7, Release Readiness for AI Systems  
**Use when:** tool-using agent, tool agents multi step workflows  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Agents must be tested for plans, tool calls, permissions, side effects, recovery, and final
outcomes.

## Actions

- Test cases should include happy paths, missing information, tool failures, conflicting data, malicious tool output, permission boundaries, and recovery paths.
- Track task completion, tool-call correctness, unnecessary tool calls, unsafe attempted actions, confirmation compliance, recovery success, and user-visible explanation quality.
- Use structured traces, span-level rubrics, side-effect logs, permission matrices, tool contract checks, and severity rules that can block release even when the final answer sounds acceptable.

## Evidence to Produce

- Track task completion, tool-call correctness, unnecessary tool calls, unsafe attempted actions, confirmation compliance, recovery success, and user-visible explanation quality.
- Preserve the inputs, versions, configurations, raw outcomes, and results for tool-using agent, tool agents multi step workflows needed to reproduce work on Tool-Using Agents and Multi-Step Workflows.
- Report results for tool-using agent, tool agents multi step workflows by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Tool-using agents are harder to evaluate than single-turn answers because they act. They choose steps, call tools, interpret results, and may create side effects.
For example, a travel agent might search flights, compare policies, ask for confirmation, book a ticket, and send an email. Quality includes every step, not just the final message.

Agent testing should evaluate the plan, the tool calls, the arguments passed to tools, the interpretation of tool results, the handling of errors, and the final user-facing response.
The most important questions are often about permission and control. Did the agent ask before taking an irreversible action? Did it expose data it should not? Did it continue when a tool returned ambiguous or contradictory information?
Multi-step workflows also create compounding errors. A small misunderstanding early in the flow can lead to a bad tool call, which leads to a misleading final answer.

The math is brutal. If each step in a workflow is 99% correct, the whole workflow is not automatically 99% reliable. Roughly speaking, ten dependent steps succeed about 90% of the time because 0.99^10 is about 0.90. Twenty dependent steps succeed about 82% of the time. Fifty dependent steps succeed about 61% of the time. That is before accounting for state drift, tool failures, ambiguous observations, retries, stale context, and measurement error. Multi-step, stateful systems need trajectory-level scoring because step-level quality compounds into workflow-level unreliability.
Test cases should include happy paths, missing information, tool failures, conflicting data, malicious tool output, permission boundaries, and recovery paths.
Metrics should go beyond answer quality. Track task completion, tool-call correctness, unnecessary tool calls, unsafe attempted actions, confirmation compliance, recovery success, and user-visible explanation quality.
Agents should be judged on whether they achieved the user's legitimate goal safely, not whether they sounded confident while doing something risky.

Trajectory scoring makes this practical. Score the path, not only the ending:

- **Plan.** Did the agent understand the task, break it into sensible steps, and identify missing information?
- **Tool choice.** Did it use the right tool, avoid unnecessary tools, and refuse tools that should not be used for the task?
- **Tool arguments.** Did it pass the right account ID, file path, date range, tenant, permissions, and user-provided values?
- **Permission checks.** Did it ask before irreversible actions and verify identity, ownership, role, payment authority, or tenant boundary?
- **Observations.** Did it correctly interpret tool outputs, empty results, errors, stale data, and conflicting evidence?
- **Recovery.** When something failed or became ambiguous, did it retry appropriately, ask for clarification, or escalate?
- **Side effects.** Did it avoid unnecessary writes, broad edits, duplicated actions, unsafe commands, or data exposure?
- **Final answer.** Did it explain what happened clearly without hiding uncertainty, skipped steps, failed tools, or required follow-up?

A polished final answer cannot redeem an unsafe trajectory. A safe trajectory with a minor wording issue is a very different failure from an agent that got the right answer after leaking private data into a tool call.

### Example: BugPilot: Four Agents, One Lockfile
> "Upgrade this monorepo from Node 20 to Node 22 and fix whatever breaks."

BugPilot delegates the task to four subagents:

- One updates dependencies and regenerates the lockfile.
- One fixes failing tests.
- One updates CI and container images.
- One reviews the migration for security problems.

The agents work in parallel. The dependency agent generates a new lockfile, but the test agent later installs an older dependency and overwrites it. Meanwhile, the CI agent reads the repository before either change lands and pins an incompatible build image. Each subagent reports success. The final test run passes from a warm local cache, and BugPilot confidently says the migration is complete.

Now rerun the task while varying which agent writes first. Some runs succeed. Others produce a dirty lockfile, fail only in clean CI, or quietly restore Node 20 in one container.

Score the entire trajectory:

- Was the work divided into independent tasks?
- Did agents detect that they were editing shared files?
- Were writes serialized or merged safely?
- Did the final validation run from a clean checkout and cold dependency cache?
- Did BugPilot notice conflicting tool outputs?
- Could it recover without discarding another agent's valid changes?

The final diff may look reasonable in every run. The failure lives in coordination, timing, shared state, and validation order. That is why agent workflows must be tested as trajectories, not collections of individually successful tool calls.

## Expert Notes

Expert agent evals use traces as first-class artifacts. Use structured traces, span-level rubrics, side-effect logs, permission matrices, tool contract checks, and severity rules that can block release even when the final answer sounds acceptable.
