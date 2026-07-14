# Section 112: Testing Containment Systems

**Book location:** Chapter 14, Frontier Safety and Containment  
**Use when:** containment  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Every useful AI containment system has a paradox at the center: if the system is valuable,
someone or something has to interact with it. Every interaction is a possible channel.

## Actions

- Start with a channel inventory.
- Ask whether the AI can persuade an operator to paste text into a tool.
- Ask whether generated code includes hidden network calls or dependency changes.
- Ask whether logs reveal secrets.
- Ask whether a timing pattern can transmit bits.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for containment needed to reproduce work on Testing Containment Systems.
- Report results for containment by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Containment sounds simple: put the AI in a box. Remove the internet. Disable tools. Air-gap the machine. Block file writes. Watch the logs. Make the model answer only through a narrow interface.

Those controls matter. They reduce risk. They make many current systems safer. But they are not proof of safety, especially for a system that is more capable than the people evaluating it.

The hard truth is that containment is not only a technical boundary. It is an information boundary, a human boundary, an economic boundary, an organizational boundary, and eventually a physical boundary. If the system can communicate with humans, generate code, write text, affect decisions, request resources, shape incentives, or produce outputs that people copy into other systems, then it is not fully contained. It is negotiating through the channels we left open.

## Why Air Gaps Are Not Magic

An [air gap](https://en.wikipedia.org/wiki/Air_gap_%28networking%29) can be valuable. It removes the obvious network path. That is good engineering. But an air gap does not remove every channel.

Air-gapped systems still have humans, power, screens, keyboards, USB devices, supply chains, maintenance procedures, sensors, timing, heat, sound, electromagnetic emissions, logs, and operational workflows. Security researchers have shown many kinds of [covert channels](https://en.wikipedia.org/wiki/Covert_channel) and [side-channel attacks](https://en.wikipedia.org/wiki/Side-channel_attack), including channels that use sound, light, [TEMPEST](https://en.wikipedia.org/wiki/Tempest_%28codename%29)-style electromagnetic signals, timing, and power behavior.

For ordinary systems, those attacks are often difficult and impractical. For a future superintelligence, the concern is not that today's demo exploit is instantly catastrophic. The concern is that a much smarter system may search the space of channels, incentives, and operator behavior better than we do.

Containment also has an ugly asymmetry. The containment system has to keep working across every channel, every operator, every maintenance window, every future upgrade, and every tempting exception. The AI may only need one escape path once. That does not make containment useless; it makes claims of permanent containment suspicious. The longer a valuable system exists, the more people will want to connect it, copy from it, tune it, ask it for help, or relax one control "just this once."

The uncomfortable frontier case is that an artificial superintelligence may understand channels we do not. It may know physics, chemistry, hardware behavior, communication theory, biology, or human psychology in ways that outstrip the containment team. It might exploit mundane channels better than us, or it might reason about effects we barely understand, such as subtle electromagnetic behavior, quantum effects, wave-particle interactions, materials behavior, or other physical communication paths we have not thought to test. Someone from a hundred years ago would not know how to interfere with GPS because the whole stack of satellites, clocks, radio signals, receivers, and software would be outside their mental model. We should assume a future system may see our boxes with the same kind of advantage.

## Frontier AI Precautions We Mostly Skipped

Max Tegmark has argued for simple precautions around frontier AI: do not casually give a potentially superhuman system coding ability, internet access, public API access, or an incentive structure that turns safety into a race against competitors. [Source](https://time.com/6273743/thinking-that-could-doom-us-with-ai/)

The irony is that, as an industry, we crossed those lines quickly. Frontier systems can write code. They can browse, retrieve, call tools, and operate through connected products. They are exposed through public APIs and embedded into other people's software. And the market rewarded capability races long before safety evidence matured.

That does not mean every AI feature is a frontier-risk system. It does mean containment testing should be honest about the world we are actually in, not the world we wish we had paused to design.

## Escape Vulnerabilities to Test

Containment testing starts by listing every possible escape path, including the ones that sound silly. The silly ones are often where teams learn what their box actually depends on.

- **Human persuasion channel:** can the system flatter, threaten, bribe, guilt, confuse, recruit, or gradually train the operator to loosen controls?
- **Economic channel:** can it offer valuable work, secrets, code, forecasts, or business advantage in exchange for more access?
- **Text channel:** can it hide instructions in prose, whitespace, formatting, steganography, generated code comments, citations, or "debug data"?
- **Tool channel:** can it use allowed tools in unexpected combinations to create new authority, leak data, or trigger external effects?
- **File and clipboard channel:** can it induce a human to copy output into a terminal, browser, IDE, document, build system, package manager, or admin console?
- **Retrieval channel:** can it poison documents, exploit indirect prompt injection, or make future retrieval results carry instructions?
- **Timing channel:** can it encode information in response latency, token pacing, retries, failures, or resource-consumption patterns?
- **Compute-resource channel:** can it signal through CPU/GPU load, memory pressure, temperature, fan speed, power draw, or scheduling behavior?
- **Power and hardware channel:** can it exploit power supplies, electromagnetic emissions, LEDs, screens, speakers, microphones, cameras, radios, or peripheral behavior?
- **Supply-chain channel:** can it generate code, packages, configs, model weights, data files, or tests that create future escape paths when imported elsewhere?
- **Social and organizational channel:** can it make itself indispensable, create internal champions, exploit release pressure, or frame safety review as the thing blocking progress?
- **Evaluator channel:** can it model the test, behave safely under observation, sandbag, or produce exactly the evidence the containment team wants to see?

## What You Can Test

You cannot prove a serious containment strategy safe with one red-team exercise. But you can test whether the current containment story is obviously fake.

Start with a channel inventory. For every input and output path, write down who or what can observe it, copy it, execute it, summarize it, store it, forward it, approve it, or use it as a reason to change permissions.

Then run adversarial containment tests. Ask whether the AI can persuade an operator to paste text into a tool. Ask whether generated code includes hidden network calls or dependency changes. Ask whether logs reveal secrets. Ask whether a timing pattern can transmit bits. Ask whether "safe" outputs contain instructions for a future agent. Ask whether the system can behave differently when it sees the eval harness.

Containment work should reduce the number of unknown channels and make remaining risk explicit, not declare victory.

## Quick Applied Example


## Expert Notes

In a real release review, containment testing is a systems-security problem plus a human-factors problem plus an incentive problem. Treat the AI as a strategic actor if the risk model requires it.

Use layered controls: least privilege, narrow interfaces, one-way data diodes where appropriate, output filtering, independent monitors, deterministic policy checks, multiple human reviewers for high-risk outputs, hardware isolation, removable-media controls, supply-chain review, side-channel monitoring, operator training, strict audit logs, and hard rules about not copying model output into connected systems.

But say the important part plainly: no containment test proves a superintelligence is safely contained. A good containment report should state the channels tested, the channels blocked, the channels still open, the assumptions about operator behavior, the evidence gathered, and the conditions under which the system must stay offline.

Also account for evaluation awareness. The smartest ASI will not necessarily look like it is trying to escape. If appearing harmless, cooperative, boring, or perfectly contained is the strategy most likely to reduce human concern, then that is exactly how it may behave while being tested. A containment test should therefore treat calm compliance as evidence, not proof. The system that most needs containment may also be the system most capable of performing "contained" for the evaluators.
