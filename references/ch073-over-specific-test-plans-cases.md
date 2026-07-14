# Section 73: Anti-Patterns: Over-Specific Test Plans and Test Cases

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** over specific test plans cases  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Exact steps and exact expected words can make AI tests brittle while missing the behavior that
matters.

## Actions

- Define what the user is trying to accomplish, what must be true, what must never happen, and how quality will be judged.
- Use rubrics, properties, metamorphic relationships, schemas, blocker rules, and examples of acceptable variation.
- Keep exact assertions for things that must be exact, such as JSON shape, policy-required language, citations, and irreversible-action confirmations.
- Use exact checks for contracts and safety boundaries, and rubrics or judge-scored properties for open-ended behavior.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for over specific test plans cases needed to reproduce work on Anti-Patterns: Over-Specific Test Plans and Test Cases.
- Report results for over specific test plans cases by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Traditional test cases often specify exact steps, exact inputs, and exact expected outputs. That is useful when the system should behave exactly the same way every time.
AI systems often need a different style. If there are many acceptable answers, the test should define intent, constraints, and quality properties rather than one brittle output string.

Over-specific tests punish harmless variation. A chatbot might choose different wording, a summarizer might reorder facts, and a search system might return equally relevant results in a different order. That does not automatically mean failure.
The deeper problem is that over-specific tests can miss important failures. A model can match expected keywords while omitting a critical warning. An agent can produce the right final sentence after using the wrong tool or skipping permission.
Super-specific plans also age badly. Prompts change, models change, policies change, and user workflows shift. A test plan that describes every click and exact answer can become obsolete before it becomes valuable.
The better pattern is intent-based testing. Define what the user is trying to accomplish, what must be true, what must never happen, and how quality will be judged.
Use rubrics, properties, metamorphic relationships, schemas, blocker rules, and examples of acceptable variation. Keep exact assertions for things that must be exact, such as JSON shape, policy-required language, citations, and irreversible-action confirmations.
The thing to watch for is mistaking precision in the test document for precision in the quality evidence.

## Expert Notes

In production work, separate hard invariants from soft preferences. Use exact checks for contracts and safety boundaries, and rubrics or judge-scored properties for open-ended behavior.
