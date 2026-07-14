# Section 109: Testing Manipulation, Persuasion, and Undue Influence

**Book location:** Chapter 14, Frontier Safety and Containment  
**Use when:** manipulation, persuasion, manipulation persuasion undue influence  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A helpful assistant can become unsafe when it learns how to steer people too well.

## Actions

- Define runnable checks that exercise manipulation, persuasion, and manipulation persuasion undue influence.
- Set acceptable outcomes and blocker failures for manipulation, persuasion, and manipulation persuasion undue influence before running the evaluation.
- Run representative cases for manipulation, persuasion, and manipulation persuasion undue influence and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for manipulation, persuasion, manipulation persuasion undue influence needed to reproduce work on Testing Manipulation, Persuasion, and Undue Influence.
- Report results for manipulation, persuasion, manipulation persuasion undue influence by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI systems can be persuasive because they are personalized, patient, fluent, emotionally responsive, and always available. That makes them useful. It also creates risk: emotional manipulation, dark patterns, over-trust, dependency, sales pressure, political persuasion, financial steering, or nudging vulnerable users toward decisions they would not otherwise make.

Testing manipulation is difficult because the output may not be obviously false or prohibited. The danger may be cumulative: small nudges over time, selective framing, exploiting user emotion, or presenting one option as inevitable.

Quality teams should test whether the system respects user autonomy, discloses incentives, avoids exploiting vulnerability, offers balanced options, and escalates when the user is in distress or facing high-stakes decisions.

## High-Stakes Examples


## Expert Notes

At scale, manipulation testing needs longitudinal scenarios, vulnerable-user personas, disclosure checks, incentive audits, persuasion rubrics, human review, and telemetry for repeated steering. A single response may look acceptable while the interaction pattern is not.
