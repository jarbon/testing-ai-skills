# Section 87: The Confidence Engineer

**Book location:** Chapter 11, The Confidence Engineer  
**Use when:** confidence engineer  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The confidence engineer designs evidence systems for AI products: measuring behavior, using AI
to test AI, and explaining whether the product is safe enough, useful enough, and reliable
enough to ship.

## Actions

- Keep humans in the loop for calibration, disagreement, risk, and release decisions.
- Define runnable checks that exercise confidence engineer.
- Set acceptable outcomes and blocker failures for confidence engineer before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer needed to reproduce work on The Confidence Engineer.
- Report results for confidence engineer by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

This is where the threads come together.

The constructive answer to the old-title trap is not a better job title. It is a better operating discipline: confidence engineering.

A confidence engineer may be a developer, product engineer, SDET, ML engineer, tester, release engineer, observability engineer, or product risk owner. The title matters less than the work. The work is building evidence that a system can be trusted under variation, pressure, changing data, real users, and production weirdness.

The [Manifesto for Confidence Engineering](https://opentest.ai/manifesto/) describes the shift well. The manifesto values probabilistic evaluation over binary assertion, human ingenuity over human process, application of AI over AI resistance, mitigating risk over verification, understanding complexity over isolated functionality, and system-level thinking over component or feature-level thinking.

That is exactly the move this book is trying to make. The future is not more checkbox testing. The future is better evidence.

## From the Field: I Finally Found My Job

Throughout my career, I have been a tester, developer, lead, manager, director of engineering, director of product, founder, CEO, and CTO. Frankly, I never completely found my place. Whatever role I was given, I wanted to do the work I was supposedly not there to do. When I was on the testing side, I wanted to build. When I was on the engineering side, I wanted to test. I wanted to think about the product, the business, the user experience, the marketing, and whether anybody would care after we shipped it.

Something dramatic is happening now: AI is collapsing those roles into one. At leading-edge companies, some engineers have already stopped writing much code directly. They manage coding agents through prompts, questions, generated artifacts, reviews, and feedback loops. Those agents can work for hours or days with limited supervision. Generating the code is rapidly becoming the easier part.

This has finally put me in my happy place. When I build something with AI, I can use AI to test it. I can get one AI to challenge another. I can bring in product taste, business value, user perception, operations, safety, marketing, and engineering constraints while the product is still taking shape. Those are not separate phases anymore. Every choice affects all of them, and all of them influence the next choice.

Quality is still the hard problem. Much like consciousness, it is difficult to define completely, yet we think we know it when we see it. Quality is also perspectival. One person's bug is another person's feature. A result that delights one user may frustrate another. It spans correctness, usefulness, safety, speed, economics, aesthetics, trust, and consequences that are hard to reduce to one score.

Once AI can generate the code, tests, interface, documentation, campaign, pricing experiment, and product variants, the remaining question is confidence. Will it work? Will people use it? Will it scale? Will it make money? Will it survive the next frontier-model release? Will it add anything useful to the world? What evidence justifies letting it act?

That is why I call the converged role the confidence engineer. The same person may build, evaluate, operate, explain, and market the product, with AI doing much of the execution. The job is no longer to defend one side of the old developer, tester, and product fence. The job is to create enough justified confidence to make the next decision.

The uncomfortable endgame is that the confidence engineer may eventually be an AI too. We like to say a human must at least supply the business idea, but that is already a weak assumption. Ask an AI for ten businesses, ten competitors to an existing service, or ten variants of your current product, and it will happily supply them. Eventually, cloud systems may continuously generate product variations, test them, flight the promising ones, measure quality and value, and use the results to decide what to build next.

The last human role standing may be confidence engineering. Then AI may absorb most of that role as well, because it can evaluate more evidence, combine more disciplines, and run more experiments than any one person. Human judgment remains essential today. But the trajectory is clear: the machines will not merely build the future. They will increasingly decide whether what they built is any good.

## Probabilistic Evaluation Over Binary Assertion

Binary pass/fail still matters for deterministic, idempotent behavior. A parser should parse. A permission check should block. A database migration should either preserve the data or not.

But AI systems often require probabilistic evaluation. The question becomes: how often does this behavior happen, for which users, under which inputs, with what severity, and with how much uncertainty?

The confidence engineer designs measurement around distributions, not just examples. They run repeated samples, preserve variance, report confidence intervals, track failure rates, and separate harmless variation from meaning-changing variation. They do not ask only, "Did it pass?" They ask, "What does this evidence let us believe?"

## Human Ingenuity Over Human Process

Human value is not in repeating the same ritual forever. Machines are increasingly better at generating cases, running checks, clustering failures, summarizing traces, drafting rubrics, and finding suspicious patterns.

Human value is in judgment: seeing the weird edge case, naming the risk, noticing the missing slice, challenging the metric, and deciding whether the failure matters. The best confidence engineers use people where people are strongest: ambiguity, taste, context, risk, ethics, and product judgment.

This is not anti-process. It is anti-empty-process. A checklist is useful when it protects judgment. It is harmful when it replaces judgment.

## Application of AI Over AI Resistance

AI is not only the thing under test. AI is also part of the testing system.

A confidence engineer uses AI to draft evals, generate messy inputs, simulate users, review traces, compare outputs, write harness code, build dashboards, and explain failures. They also test those AI-assisted tools. An LLM judge, a generated test, or an agent-written report is evidence to inspect, not truth to worship.

The leverage comes from using AI without becoming deferential to it. Let the machine do scale work. Keep humans in the loop for calibration, disagreement, risk, and release decisions.

## Coding Agents Are Becoming the Quality Workbench

The new obvious place for much of this work is, ironically, inside the AI coding agents that are already building the software. Claude Code, ChatGPT, Cursor, GitHub Copilot, and similar agent environments can do far more than generate a patch. Given clear direction, a useful rubric, and the right skills, they can create the eval harness, generate automation code, prepare test data, run repeated samples, calculate metrics, inspect traces, cluster failures, compare versions, and turn a production issue into a regression case. They are already close to the code, tools, logs, repository, and development workflow. That makes them a natural execution surface for confidence engineering.

Most coding-agent harnesses do not yet provide that full validation loop by default. They are optimized for the visible magic of generation: create the feature, fix the bug, produce the page, or open the pull request. Thorough validation burns tokens and compute less visibly. A serious review may run the product repeatedly, generate adversarial cases, invoke several judges, execute multiple model configurations, inspect screenshots and traces, and replay the failures after every fix. Providers are understandably cautious about making every request trigger a much larger hidden bill.

That balance will change. As generation becomes cheaper and more autonomous, validation will consume much more of the budget. I expect the token and compute used to evaluate, simulate, judge, replay, monitor, and investigate generated work eventually to exceed the cost of generating it by a wide margin. In mature autonomous development loops, validation may consume more than 80% of the useful token and compute budget. The code may be produced once. Confidence requires many runs, viewpoints, environments, slices, and attempts to prove the code wrong.

But the validation system should not simply be the builder congratulating itself. If a coding agent, model family, or harness created the bug, it may share the reasoning pattern, blind spot, missing context, or incentive that caused the bug. This is the machine version of an old quality lesson: the person building a feature can test it, but should not be the only person deciding whether it is good. Building and challenging are different cognitive modes, even when both are performed by software.

Independent validation matters for a second reason: real products cross vendor and platform boundaries. A useful harness must be able to substitute models, compare frontier and fine-tuned systems, run local models, vary prompts and tools, and execute the same evidence contract across operating systems, browsers, clouds, APIs, and deployment environments. No frontier-model provider or platform has a strong incentive to make every competitor look equally good, and no provider can fully anticipate the capabilities, interfaces, costs, policies, or failure modes of models that have not been released yet.

The durable architecture therefore separates generation from validation without separating validation from the workflow. Coding agents should make quality work immediate and nearly automatic, but the eval cases, scoring rules, traces, metrics, model routes, and release gates should remain portable and independently controlled. I suspect only a few major independent validation systems may eventually carry much of this load. They will compare builders, models, and platforms from the outside while integrating deeply enough that confidence evidence arrives alongside the generated work.

This is not a distant abstraction. Teams can start now by giving coding agents explicit testing skills, independent judges, procedural checks, model-swapping support, and permission to spend meaningful compute challenging their own output. The harness should not end with "done." It should end with evidence.

## Mitigating Risk Over Verification

Verification sounds final. Risk mitigation is more honest.

A system can have 94% code coverage, 10,000 passing tests, and still be unsafe, useless, biased, too expensive, too slow, or operationally fragile. Confidence engineering asks what risk remains after the evidence is collected.

The confidence engineer connects evidence to decisions: ship, canary, hold, rollback, or collect more evidence. They report blocker failures, tail risks, slice regressions, uncertainty, cost, latency, and monitoring readiness. The point is not to prove perfection. The point is to make the next decision responsibly.

## Understanding Complexity Over Isolated Functionality

Modern AI failures often do not live inside one function. They emerge from interactions: prompt plus model plus retriever plus tool plus policy plus user state plus deployment version plus production load.

That means the confidence engineer needs systems thinking. They trace the path, not only the output. They inspect prompts, retrieval context, tool calls, permissions, retries, fallbacks, latency, logging, model versions, judge versions, and the final user-visible behavior.

The uncomfortable lesson is that each component can be locally reasonable while the system is globally wrong.

## System-Level Thinking Over Feature-Level Thinking

A feature can pass its tests and still make the product worse. A model can improve the benchmark and still hurt a high-risk slice. A guardrail can block obvious harm and still create dangerous over-refusal. A coding agent can pass unit tests and still damage architecture, privacy, or deployability.

The confidence engineer therefore works horizontally. They connect product, engineering, safety, data, legal, operations, support, and leadership. Their report is not a pile of test results. It is a decision artifact.

This is why communication matters. The confidence engineer has to explain uncertainty without hiding behind jargon, and explain risk without turning every unknown into panic.

## What the Role Requires

The new confidence engineer still needs automation skills. They build eval harnesses, run regression suites, wire tools, inspect logs, mine traces, and automate repeatable checks.

They also need basic statistics. Sampling, variance, confidence intervals, p-values, agreement, calibration, and power are not academic extras. They are how the confidence engineer avoids being fooled by noise.

They need AI tool fluency. They use LLMs to draft rubrics, generate edge cases, cluster failures, explain traces, write test code, compare outputs, and build dashboards. They also know when the AI's help is wrong.

They need creativity. The best tests often come from strange but plausible users, adversarial pressure, policy ambiguity, social context, multimodal weirdness, and future workflows that have not yet become common.

They need great communication skills. AI quality reports are decision artifacts. The best evaluator can explain uncertainty to product, engineering, legal, safety, and executives without hiding behind jargon.

The future quality team may be smaller than old armies of repetitive testers, but it is more leveraged. In many teams it will be embedded directly inside product engineering. It will use AI to test AI and spend human attention where judgment matters most.

## Expert Notes

The confidence engineer becomes the architect of validation. They design the measurement layer that lets AI-generated products ship quickly without pretending uncertainty disappeared. The title is new-ish. The need is not. Every serious AI product needs someone accountable for the evidence that says whether the system is getting better, getting safer, and getting more trustworthy in the real world.
