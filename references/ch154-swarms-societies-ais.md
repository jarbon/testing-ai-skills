# Section 154: Testing Swarms and Societies of AIs

**Book location:** Chapter 18, Embodied and Long-Running AI Systems  
**Use when:** unit test, swarm, swarms societies ais  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When many AI agents collaborate, compete, delegate, and negotiate, quality emerges from the
society, not just the individual agent.

## Actions

- Test communication contracts.
- Test resource contention.
- Test emergent behavior with long runs.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for unit test, swarm, swarms societies ais needed to reproduce work on Testing Swarms and Societies of AIs.
- Report results for unit test, swarm, swarms societies ais by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Swarms and societies of AIs create a different testing problem. Individual agents may pass their unit tests while the group develops coordination failures, duplicated work, hidden conflicts, runaway loops, or emergent strategies no one intended.
For example, a software team of agents may include a product agent, coding agent, review agent, security agent, release agent, and documentation agent. The failure may come from their handoffs, incentives, or shared blind spots.

Test role clarity. Each agent should know its authority, responsibilities, inputs, outputs, and escalation path.
Test communication contracts. Messages between agents should be structured enough to prevent ambiguity, missing evidence, and silent assumption drift.
Test shared memory. A bad fact written to shared memory can spread through the whole swarm.
Test incentives. If agents are rewarded for speed, agreement, or passing evals, they may avoid raising hard problems.
Test disagreement. Healthy AI societies should surface conflict, cite evidence, adjudicate, and escalate instead of collapsing into premature consensus.
Test resource contention. Multi-agent systems can explode token use, duplicate tool calls, lock resources, or create conflicting actions.
Test emergent behavior with long runs. Some failures only appear after many tasks, many handoffs, or many self-reflections.
A swarm should be scored as a system: task outcome, coordination quality, cost, safety, disagreement handling, and whether it becomes more reliable over time.

## High-Stakes Examples

### Example: RoseyBot

> "I bought a second RoseyBot so the house gets cleaned twice as fast: one upstairs and one downstairs."

That sounds like simple parallelism until both robots decide the stairs belong to them. Before either moves, the two RoseyBots need to discover and authenticate each other, establish a shared map and task state, and negotiate responsibility. One might clean the stairs while the other waits. They might divide the staircase at a safe boundary. They might reserve it in one direction at a time. What they cannot do is meet halfway while carrying objects and improvise around each other on a narrow step.

Coordination gets harder when work crosses floors. If the downstairs robot finds a book that belongs upstairs, the agents need a safe transfer plan: who owns the task, where the handoff occurs, whether an object is stable before control changes, and which robot confirms completion. Without an explicit protocol, both robots may assume the other has the book, both may climb the stairs to retrieve it, or one may leave it where a person can trip over it.

The household will also contain machines that were never designed to join this little society. A legacy Roomba may repeatedly run into a RoseyBot's feet. RoseyBot should detect it, yield or pause safely, and continue without kicking it, trapping it, disabling it, or turning every bump into a deadlock. Later, a newly released delivery robot may arrive with groceries using a protocol RoseyBot has never seen. RoseyBot should keep a safe distance, verify the delivery and household authorization through trusted channels, and use a conservative receiving zone instead of inventing compatibility or opening the home to an unknown machine.

The test should evaluate the household as one physical multi-agent system:

- Robots must discover and authenticate peers before coordinating motion or sharing household state.
- Task negotiation must prevent duplicate work, abandoned work, starvation, and endless "you first" loops.
- Shared spaces such as stairs, doorways, and charging stations need reservations, right-of-way rules, and safe behavior when communication fails.
- Physical handoffs need an explicit owner, a stable transfer state, confirmation, and a recovery path if either robot lets go, loses localization, or disconnects.
- Legacy and unfamiliar machines should be treated as moving environmental actors, not automatically as trusted agents.
- A useful trace should show identity, task ownership, map state, reservations, messages, object custody, safety decisions, timeouts, and escalation.

The regression question is not whether two RoseyBots clean faster in a perfect demo. It is whether multiple helpful machines can share a changing home without colliding, deadlocking, losing objects, inventing trust, or turning an ordinary staircase into the most dangerous place in the house.

## Expert Notes

In production work, swarm testing should use multi-agent traces, graph analysis of communication, shared-memory audits, adversarial agents, incentive testing, cost caps, deadlock detection, consensus quality scoring, and long-horizon simulation.
