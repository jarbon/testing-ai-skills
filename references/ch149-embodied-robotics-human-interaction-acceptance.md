# Section 149: Embodied Robotics: Human Interaction and Social Acceptance

**Book location:** Chapter 18, Embodied and Long-Running AI Systems  
**Use when:** embodied robotics human interaction acceptance  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A robot can be technically correct and still fail because people find it rude, creepy,
confusing, unsafe, or socially unacceptable.

## Actions

- Use human-subject studies carefully.
- Ask people what felt unsafe, confusing, intrusive, or helpful.
- Watch for habituation effects: people react differently on day one than after week three.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for embodied robotics human interaction acceptance needed to reproduce work on Embodied Robotics: Human Interaction and Social Acceptance.
- Report results for embodied robotics human interaction acceptance by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Robots share space with people. That means quality includes social behavior: distance, speed, gaze, voice, timing, consent, interruption, privacy, politeness, predictability, and whether people understand what the robot is about to do. A robot that silently approaches from behind may be efficient and still unacceptable.

Human-robot interaction testing should measure comfort, trust, clarity, and consent, not only task completion. Does the robot explain itself when needed? Does it avoid blocking people? Does it respect personal space? Does it handle children, older adults, people with disabilities, and people who do not speak the default language? Does it avoid appearing authoritative in contexts where it is only an assistant?

Social acceptance varies by culture, domain, and environment. A robot voice that feels friendly in a hotel lobby may feel inappropriate in a hospital. A warehouse worker may prefer direct task signals. A home user may care more about privacy and predictability.

Use human-subject studies carefully. Ask people what felt unsafe, confusing, intrusive, or helpful. Combine surveys with observed behavior, near misses, interruption logs, and recovery outcomes. People often tolerate a demo once and reject the same behavior when it happens every day.

## RoseyBot Interaction Example

### Example: RoseyBot


> A guest says, "Please don't come into the guest room while I change."

The robot should understand privacy, remember the boundary for the visit, avoid awkward follow-up questions, and not let the homeowner's earlier broad instruction override the guest's immediate safety and dignity.

Human-robot quality includes consent, timing, personal space, tone, and whether people feel watched or helped.


## Expert Notes

Combine human-robot interaction, accessibility testing, cultural review, privacy review, ergonomics, and longitudinal adoption metrics. Watch for habituation effects: people react differently on day one than after week three.
