# Section 51: Observability and Tracing for AI Systems

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** latency, observability, retrieval, observability tracing  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

You cannot debug a final answer if you cannot see the path that produced it.

## Actions

- Use a small set that covers user-visible quality, safety, latency, tool reliability, and cost.
- Keep catastrophic events, such as cross-customer data exposure or an unauthorized irreversible action, out of a comforting average.
- Save the user-visible output, prompt assembly, model and prompt versions, policy version, retrieval snapshot, tool inputs and results, timing, permissions, judge decisions, and deployment state.
- Apply privacy and access controls; incident evidence can contain the most sensitive data in the system.
- Do not let uncertainty about the model become an excuse for silence about observed impact.

## Evidence to Produce

- Save the user-visible output, prompt assembly, model and prompt versions, policy version, retrieval snapshot, tool inputs and results, timing, permissions, judge decisions, and deployment state.
- Preserve the smallest faithful reproduction, add nearby variants and affected slices, assign an owner, and connect the regression case to the release gate and production monitor.
- Log the request, but also log confirmation.
- Preserve the inputs, versions, configurations, raw outcomes, and results for latency, observability, retrieval, observability tracing needed to reproduce work on Observability and Tracing for AI Systems.

## Chapter Guidance

## Overview

Observability is the evidence trail for AI systems. It captures prompts, retrieved context, tool calls, model responses, judge scores, token counts, cost, latency, errors, and user-visible outcomes.
For example, an agent may give a wrong refund answer because retrieval missed the newest policy, a tool returned stale account data, the model ignored a permission rule, or a downstream service timed out. The final answer alone does not tell you which layer failed.

A trace breaks an AI interaction into spans: user input, prompt construction, retrieval, ranking, model call, tool call, parser, guardrail, judge, and final response. That structure lets builders inspect the system like a real workflow instead of a magic text box.


For agents, tracing is essential. The final answer is only the last artifact. Quality also depends on plan choice, tool choice, arguments, observations, retries, permissions, and recovery steps.
Useful traces include timing and cost. A response can be correct but too slow, too expensive, or dependent on repeated retries that will fail under load.
Trace storage should be designed with privacy in mind. Prompts and retrieved context can contain user data, internal policy, medical-style records, source code, secrets, or proprietary business logic.
Tools such as LangSmith, Braintrust, Arize Phoenix, Langfuse, and OpenTelemetry-based instrumentation can help teams collect and inspect traces. The exact tool matters less than whether the trace captures the whole decision path.
Observability should connect to evaluation. A failing eval should link to the trace. A production failure should become a test case. A high-latency trace should feed cost and performance regression checks.
Dashboards are not enough. Confidence Engineers need trace-to-fix workflows: isolate the failing layer, reproduce it, add a regression case, verify the fix, and monitor the category after release.
A system without traces can still be tested from the outside, but it cannot be debugged or improved with the same precision.

## SLOs, Error Budgets, and AI Incident Response

Observability becomes operational quality when it is tied to explicit service objectives and a practiced incident process.

A **service-level indicator (SLI)** is a measured behavior, such as p95 latency, grounded-answer rate, successful tool completion, severe-policy-failure rate, or cost per completed task. A **service-level objective (SLO)** is the target for that indicator over a window, such as "99% of eligible support conversations complete without an incorrect account action over 28 days." An **error budget** is the amount of failure the objective permits. If the SLO allows 1% failure, that 1% is the budget the team can spend while changing the system.

AI systems need more than one SLO. A single availability target will miss fluent but wrong answers. Use a small set that covers user-visible quality, safety, latency, tool reliability, and cost. Keep catastrophic events, such as cross-customer data exposure or an unauthorized irreversible action, out of a comforting average. Those may require a separate near-zero budget and immediate release block.

An AI incident response should move through a deliberate sequence:

1. **Detect.** Alert on direct failures and weak signals: policy violations, judge-human disagreement, repeated prompts, tool retries, empty retrieval, unusual token growth, escalations, and user corrections.
2. **Contain.** Disable the risky tool, route to a safer model, narrow the affected slice, freeze a retrieval source, switch to read-only mode, or stop the release. Containment is about reducing harm before proving the root cause.
3. **Preserve evidence.** Save the user-visible output, prompt assembly, model and prompt versions, policy version, retrieval snapshot, tool inputs and results, timing, permissions, judge decisions, and deployment state. Apply privacy and access controls; incident evidence can contain the most sensitive data in the system.
4. **Assess impact.** Identify affected users, time window, slices, actions, financial or safety consequences, and whether the failure propagated to downstream systems. Count confirmed impact separately from the population that may have been exposed.
5. **Recover.** Roll back, repair state, verify the rollback path, and independently confirm the user-visible result. A successful deployment command is not proof of recovery.
6. **Notify.** Follow the product's customer, security, privacy, legal, and regulatory notification rules. Do not let uncertainty about the model become an excuse for silence about observed impact.
7. **Learn.** Write a blameless postmortem that covers the technical path, monitoring gaps, decision delays, and why defenses did not stop the event sooner.
8. **Promote the incident into the eval suite.** Preserve the smallest faithful reproduction, add nearby variants and affected slices, assign an owner, and connect the regression case to the release gate and production monitor.

The final step closes the loop. An incident that produces only a document can recur. An incident that becomes a versioned eval, monitor, and recovery drill permanently improves the measurement system.

## Case Study: Three Mile Island

The Three Mile Island accident included a deceptively simple observability failure: operators saw an indicator showing that a relief valve had been commanded closed, but the valve was actually stuck open. The control room signal represented the system's intended or commanded state, not the physical state that mattered.

That distinction is central to AI tracing. A trace that says "refund issued," "file deleted," "policy checked," "retrieval succeeded," or "doctor escalation requested" may only prove that the agent attempted an action or received a plausible tool response. It may not prove that the downstream state changed, that the user saw the right result, or that the real-world system is now safe.

For AI agents, observability has to separate intent, command, tool response, actual state, and impact. Log the request, but also log confirmation. Record the model's plan, but also record what happened after each tool call. Capture the state before and after the action. When possible, use independent checks: a second read after a write, an audit event from the downstream system, or a user-visible receipt that proves the operation completed.

The Three Mile Island lesson is uncomfortable but useful: a dashboard can be telling the truth about the wrong thing. In AI systems, a fluent trace can still be a fiction if it records what the agent believed instead of what the world did.

Source: [U.S. NRC backgrounder on Three Mile Island](https://www.nrc.gov/reading-rm/doc-collections/fact-sheets/3mile-isle.html)

## From the Field: Dogfooding the Wrong Scale

When I was working on the book *How Google Tests Software*, I decided I should dogfood Google Docs and use it for the manuscript. James was smarter than me and used Microsoft Word.

Around 25 or 30 pages in, Google Docs started getting flaky. By flaky, I mean JavaScript crashes, reload loops, and lost text. Sometimes I would lose roughly a page of writing. Coming from Microsoft, data loss felt like one of the ultimate product sins. You just do not lose the customer's data.

So I did what testers do. I tracked when it happened, captured the client console logs I could get, saved repro notes, and talked to the SRE-style operations folks near me in Kirkland. They could see signs that something was wrong in production, and that it probably was not only me, but the systems were secure and siloed enough that no one person could easily pull the whole thread together. They also deliberately did not log much beyond the fact that a crash happened, partly to limit storage costs and partly to avoid collecting PII. Those were reasonable concerns, but they also meant the evidence trail was thinner when something serious went wrong.

Later, when I was visiting the Google New York office, I found the Google Docs team. I waited until their standup ended and talked to a tech lead. I explained that I was writing a book about how Google tests software, that Docs was crashing and losing text, and that I had logs and possible production signals to connect. The response I remember was basically: it was not designed for that. It was designed for office documents, not writing books.

That answer has stayed with me. It may have been technically true for the architecture and machine limits of the time, but from the user's side it did not matter. I was using the product to write. It was losing data. The product boundary and the user's expectation did not match.

The AI lesson is that observability has to include product reality, not only intended use. Users will stretch the system. They will use a chatbot as a workflow engine, a spreadsheet as a database, a code agent as a junior engineer, or a document editor as a book-writing tool. If telemetry, logs, support channels, and bug reports say users are pushing past the original design envelope, that is not just misuse. It is product evidence.

The second lesson is that someone has to monitor the monitors. Logs do not fix production. Dashboards do not care. Alerting systems do not feel embarrassment about data loss. A lot of production quality failures persist because the human system around the telemetry does not follow up, cannot connect the siloed evidence, or decides the use case does not count. Observability only becomes quality when a team has ownership, curiosity, and authority to act on what the logs are saying.

I eventually moved much of the writing to another next-generation writing app and even gave that team feedback about what it was like to write long-form content on mobile. They were polite and curious. That is still my advice: if you find real product pain, do not only complain about it in public. File the bug. Send the logs. Talk to the team if you can. Sometimes that weak signal is exactly what the product needs.

## From the Field: The Back Button Knew First

When I worked on Chrome, we tested hundreds of thousands of websites every night. We found crashes, rendering issues, compatibility problems, and plenty of ordinary bugs. But one of the best production-quality tools the Chrome team had was not exotic at all. It was a small set of simple counters: how often users clicked back, forward, bookmarks, menus, and the other bits of browser chrome.

Chrome was named Chrome because the team wanted to remove as much of the browser chrome as possible and let the content be the hero. The irony is that the little remaining pieces of chrome became incredibly useful health signals.

One day, during bug triage in Mountain View, we saw a sudden spike after a deployment. Back-button clicks had jumped dramatically. It did not immediately make sense. The browser was not obviously crashing. We could compare channels like Canary, Dev, and production, but the pattern was still strange.

The insight was that the only major change in that build was in the JavaScript engine. At first, that sounded unrelated. Then the room started to connect the dots. At the time, many websites were single-page applications. Pressing the browser back button did not always navigate to a previous URL; the page might capture the back action and move to a previous in-app state. If that behavior broke, users would press back, nothing useful would happen, and they would press back again.

That simple counter told us the product was unhealthy before we had a clean repro. The symptom was far away from the cause: a spike in back-button clicks pointed toward a JavaScript engine behavior change. After the change was reverted and fixed, the numbers returned to normal.

That is the observability lesson for AI systems. You do not always need a huge trace platform to notice quality drift. Sometimes a tiny behavior counter is the first signal: regenerate clicks, undo actions, repeated prompts, longer conversations, escalation spikes, copy-rate drops, tool retries, abandoned flows, or users asking the same question twice. None of those signals proves the model is wrong by itself. But it tells you where reality is pushing back.

## Expert Notes

In a real release review, traces should have stable correlation IDs, privacy-aware redaction, span-level metadata, model and prompt versions, retrieval snapshots, tool inputs and outputs, token/cost metrics, latency percentiles, judge scores, and links back to eval cases and production incidents.
