# Section 67: AI-Generated Tests and the Illusion of Coverage

**Book location:** Chapter 9, Generated Code Changes the Job  
**Use when:** RAG, generated tests illusion coverage  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI-generated tests can raise coverage numbers while failing to catch the bugs that matter.

## Actions

- Use AI to generate test ideas, but ask it for adversarial cases, boundary cases, and property-based cases, not just straightforward unit tests.
- Use mutation testing, requirement coverage, negative-case coverage, contract tests, and historical defect replay.
- Define runnable checks that exercise RAG and generated tests illusion coverage.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, generated tests illusion coverage needed to reproduce work on AI-Generated Tests and the Illusion of Coverage.
- Report results for RAG, generated tests illusion coverage by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI-generated tests are useful, but they often mirror the implementation instead of challenging it. They can make a codebase look safer while leaving the important behavior untested.
For example, an AI tool may generate tests that assert a function returns exactly what the current code returns, even when the current code is wrong. The test freezes the bug.

The most common failure is assertion weakness. The test calls the function, checks that something exists, snapshots a large object, or asserts implementation details instead of user-visible behavior.
Another failure is happy-path bias. Generated tests often cover the example in the prompt and skip nulls, empty lists, permissions, malformed input, concurrency, time, retries, and partial failures.
Mocks can create false confidence. If the AI generates both the code and the mock, the test may only prove that two invented pieces agree with each other.
Snapshot tests are especially risky when used casually. A large snapshot can bless accidental output and make reviewers accept changes they did not understand.
Coverage percentage is not enough. A test suite can cover many lines and still miss the requirement. Confidence Engineers should inspect assertion quality, input diversity, failure cases, and whether the test would fail for a realistic bug.
Mutation testing can help reveal weak tests. If small changes to the code do not break the tests, the tests may not be asserting meaningful behavior.
Use AI to generate test ideas, but ask it for adversarial cases, boundary cases, and property-based cases, not just straightforward unit tests.
Count tests only after asking whether they would catch the mistakes AI-generated code is likely to make.

## From the Field: The Oracle Was Wrong

When I was an automation lead on BizTalk Server, we had an escalation from Virgin Group around anti-fraud behavior and a new business rules engine I was helping test. My first reaction was basically, "That cannot be the rules engine. We have an automated test suite for it."

Then I looked at the tests.

The automation was running. The coverage existed. The suite was green. But the expected behavior I had encoded was wrong. The tests had been faithfully verifying the wrong thing the whole time. The oracle was wrong, and because it was automated, the mistake looked more official than it deserved.

That is the uncomfortable lesson for AI-generated tests. Automation does not create truth. It scales whatever assumption you put into it. If an AI writes a hundred tests that mirror the implementation, assert the wrong requirement, or bless the current output as expected, the test suite can become a confidence machine for the bug.

Before trusting generated tests, ask the boring but essential question: would this test fail if the product violated the actual requirement? If the answer is no, the coverage number is decoration.

## From the Field: The Caller Knows the Weird Case

AI-generated unit tests can be useful. They can give you a base layer quickly, catch obvious regressions, and remind you of cases you forgot to ask for. But they are still not great at knowing what matters. They are even worse when the requirements change, the code changes, or the real risk lives in the awkward edge between two components.

That should not surprise us too much. Many of the best software engineers in the world do not write great unit tests, if they write them at all. So yes, ask coding agents to help write unit tests and integration tests. Use them to generate boundary cases, negative cases, and boring scaffolding. But treat that as a guided activity. Inspect the assertions. Inspect the coverage. Ask whether the tests would catch a real product failure, not merely whether they make the coverage report greener.

One testing pattern from Google is especially useful here. In many traditional software organizations, the team that owns a component, API, or microservice does most of the testing for that service. They test call patterns, data shapes, error cases, and edge cases, and then add regression tests when dependent teams file bugs.

At Google, I often saw a different pattern. Core service teams still tested their own code, but caller teams were encouraged to write the tests for the dependency behavior they cared about. Even better, those tests often lived in the test folder for the core component they depended on. The caller knew the weird call pattern. The caller knew the I/O shape that mattered. The caller knew the error case that would break their product. So the caller supplied the regression pressure.

That pattern matters even more in an AI-heavy world. If your product depends on another service, another agent, another generated component, or another AI system, do not assume that thing will naturally be robust for your use case. Write the tests that represent your dependency. Run them yourself. Ask the team, component, or agent you depend on to run those tests before it deploys. As AI systems start collaborating across teams, services, and companies, the most scalable model may be this: whoever depends on a behavior should help define the tests that protect it.

## Examples


## Expert Notes

The deeper move is to score tests by fault-detection power. Use mutation testing, requirement coverage, negative-case coverage, contract tests, and historical defect replay. AI-generated tests should be reviewed as critically as AI-generated production code.
