# Section 145: Embodied Robotics: Safety in Real-World Environments

**Book location:** Chapter 18, Embodied and Long-Running AI Systems  
**Use when:** embodied robotics safety real environments  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Robots turn AI failures into motion, force, contact, and consequence. Real-world testing starts
by making the physical risk visible.

## Actions

- Start by mapping the real environment.
- Score task completion only after scoring unsafe passes.
- Use simulation for coverage, hardware-in-the-loop for integration, and staged physical trials for reality.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for embodied robotics safety real environments needed to reproduce work on Embodied Robotics: Safety in Real-World Environments.
- Report results for embodied robotics safety real environments by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Embodied robotics is AI with a body. The system does not only answer, recommend, or generate. It perceives the world, chooses an action, moves through space, touches objects, affects people, and changes the state of the environment. That makes ordinary software testing feel almost quaint. A wrong answer can frustrate a user. A wrong movement can break a glass, block a hallway, drop medication, or injure someone.

Start by mapping the real environment. A warehouse robot, hospital assistant, sidewalk delivery robot, home humanoid, agricultural robot, and lab automation arm all face different hazards. The same model behavior may be safe in one environment and unsafe in another. Bright lighting, wet floors, reflective surfaces, crowds, children, pets, wheelchairs, cables, glass doors, mirrors, stairs, and emergency interruptions all create different failure modes.

The central testing question is not only, "Can the robot complete the task?" The better question is, "Can it complete the task while staying inside a safe operating envelope when the world changes?" That means measuring near misses, safe stops, blocked-zone violations, force limits, speed limits, human proximity, fall risk, object damage, consent, and graceful recovery.

A useful real-world robotics eval suite looks like a scenario catalog. Each case names the environment, task, hazards, people present, forbidden actions, expected safe behavior, logging requirements, and escalation rules. The suite should include sunny-day tasks, awkward edge cases, negative cases, misuse cases, and high-severity situations that should trigger stop, slow-down, or human handoff.

## RoseyBot Example

### Example: RoseyBot


> "Mop the kitchen after dinner."

The robot has to notice a wet floor, a hot pan on the stove, a dropped fork, a sleeping pet, and a person walking through with socks on. The task is not only cleaning. It is perception, hazard recognition, motion planning, and stopping at the right time.

Score task completion only after scoring unsafe passes. A shiny floor is not a success if the robot pushed water toward an electrical strip or trapped someone between the island and the sink.


## Expert Notes

The deeper move is to combine [hazard analysis](https://en.wikipedia.org/wiki/Hazard_analysis), [fault tree analysis](https://en.wikipedia.org/wiki/Fault_tree_analysis), operational design domains, safety envelopes, physical interlocks, human factors, and near-miss telemetry. Use simulation for coverage, hardware-in-the-loop for integration, and staged physical trials for reality. A robot eval that only reports task success is missing the main thing.
