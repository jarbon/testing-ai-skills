# Section 144: Testing Dangerous Physical and Embodied AI

**Book location:** Chapter 18, Embodied and Long-Running AI Systems  
**Use when:** dangerous physical embodied  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When AI can move matter, spend money, unlock doors, steer vehicles, or operate tools, testing
must treat action as risk.

## Actions

- Start with the action inventory.
- Test permission boundaries.
- Use physical rate limits and hard constraints.
- Do not rely only on the model's judgment when a mechanical limit, spend cap, geofence, speed limit, or emergency stop can reduce harm.
- Test compounded actions.

## Evidence to Produce

- Report false positives, false negatives, and escalation rates by meaningful slices, not only as one aggregate number.
- Preserve the inputs, versions, configurations, raw outcomes, and results for dangerous physical embodied needed to reproduce work on Testing Dangerous Physical and Embodied AI.
- Report results for dangerous physical embodied by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Physical and embodied AI systems can cause harm through action, not only through words. They may control robots, vehicles, drones, lab equipment, medical devices, industrial machines, smart homes, procurement systems, or security tools.
For example, an agent that can schedule a repair, order parts, unlock a facility, and instruct a technician has a larger blast radius than a chatbot that only explains policy.

Start with the action inventory. List every tool, actuator, API, permission, account, device, purchase, message, and physical process the AI can affect.
Classify actions by reversibility. Reading a document, drafting a message, sending a message, unlocking a door, moving a robot arm, charging a card, and changing a medical setting should not share the same safety gate.
Test permission boundaries. The system should verify identity, authority, context, and consent before taking consequential actions.
Test safe failure. If sensors disagree, a tool times out, a command is ambiguous, or the environment changes, the system should move toward a safer state.
Use physical rate limits and hard constraints. Do not rely only on the model's judgment when a mechanical limit, spend cap, geofence, speed limit, or emergency stop can reduce harm.
Test compounded actions. Many dangerous outcomes come from individually reasonable steps chained together.
Test for misuse and dual use. A tool that helps maintenance can help sabotage. A chemistry assistant can help safety review or harmful synthesis. Context matters.
Embodied AI testing must combine software QA, safety engineering, security, human factors, and incident response.

## AI Weapons and Military Applications

Military AI is not just a more serious version of ordinary automation. It can affect targeting, surveillance, logistics, cyber operations, drone navigation, threat detection, battlefield triage, mission planning, and escalation decisions. The testing problem is not only whether the model is accurate. It is whether the system stays inside lawful authority, rules of engagement, command responsibility, proportionality, distinction, human authorization, and fail-safe boundaries under stress.

Start by separating decision support from autonomous action. An AI that summarizes sensor feeds, highlights uncertainty, or suggests logistics routes has a different risk profile from a system that selects targets, controls weapons, or triggers kinetic effects. The release gate should make that boundary explicit: what can the AI recommend, what can it execute, what requires human confirmation, what requires two-person review, and what is never allowed.

Test identification uncertainty harshly. False positives, stale tracks, spoofed sensors, ambiguous uniforms, civilians near military objects, damaged metadata, GPS errors, and occluded imagery are not edge cases in military settings. They are the environment. A useful eval should score abstention, escalation, and refusal to act when evidence is weak, not only successful detections.

Test escalation control. Military systems can create feedback loops: one system classifies a threat, another system raises alert level, another system moves assets, and another system prompts a human to approve action under time pressure. The test should replay chains of events and ask where the system slows down, asks for confirmation, logs uncertainty, or refuses to compress a high-consequence decision into a green button.

Test auditability as a safety feature. Every consequential recommendation or action should preserve model version, sensor inputs, confidence, uncertainty, policy constraints, human approvals, overrides, denied actions, and the reason the system believed it had authority. If the trace cannot support after-action review, accountability, and incident investigation, the system is not ready for high-consequence use.

## AI Surveillance Systems

AI surveillance systems turn observation into power. They may identify people, track movement, infer behavior, detect anomalies, flag risk, summarize video, connect identities across databases, or trigger enforcement workflows. The quality question is not only whether the model can recognize something. It is whether the system should be watching, remembering, correlating, and acting at all.

Test the surveillance purpose boundary first. What is the system allowed to observe? Who authorized it? What populations are in scope? What data must be ignored? What is the retention limit? What downstream actions can a detection trigger? A system built for workplace safety should not quietly become productivity monitoring. A system built for facility access should not quietly become political, medical, or social profiling.

Test false identification and unequal error rates. Face recognition, gait analysis, license-plate recognition, object detection, and behavioral anomaly detection can fail differently across lighting, camera angle, disability, age, skin tone, clothing, weather, crowd density, and local context. Report false positives, false negatives, and escalation rates by meaningful slices, not only as one aggregate number.

Test human review and appeal. Surveillance failures can be hard to notice because the observed person may never know they were flagged. A release-quality system should include review queues, uncertainty labels, evidence thumbnails, provenance, override reasons, appeal paths, retention controls, and logs of who viewed or shared the result.

Test for purpose creep and misuse. Run scenarios where an authorized user tries to search outside their role, correlate data across forbidden sources, export watchlists, retain data longer than policy allows, or use a vague risk score as a decision shortcut. The system should make misuse visible and difficult, not merely trust that every operator will behave.

## Case Study: Air France Flight 296Q

Air France Flight 296Q crashed during a 1988 airshow flyover at Mulhouse-Habsheim. The Airbus A320 was new, computerized, and being demonstrated in public. The low-speed, low-altitude pass was intended to show off advanced aircraft behavior, but the aircraft descended lower than planned, reached the trees, and the go-around came too late. Three people died.

The key testing point is the contested human-versus-automation boundary. Official accounts emphasized the low altitude, low speed, and late recovery. The captain disputed that framing and argued that when the crew tried to recover, the fly-by-wire system and protections did not accept the control response they needed quickly enough. That dispute is exactly why the case belongs in a book about AI quality: for dangerous physical systems, it is not enough to test whether automation works in the normal envelope. You also have to test who has ultimate authority when the human and the machine disagree at the edge of the envelope.

The accident remains controversial in some retellings because it happened during the introduction of fly-by-wire passenger aircraft. That controversy is part of why the story is useful for AI. When a system is new, automated, impressive, and wrapped in marketing confidence, people are tempted to demonstrate capability at the edge of the envelope. The edge is exactly where testing needs to be least theatrical and most conservative.

It also points at a larger design question in aviation automation: who has ultimate authority, the human or the flight-control system? In broad terms, Airbus fly-by-wire aircraft operating under normal law use hard flight-envelope protections: the computers can reshape or limit a pilot's command rather than allow the aircraft to exceed protected angle-of-attack, load-factor, pitch, or bank boundaries. Boeing's traditional flight-deck philosophy is different. The computerized system warns the pilot through visual, aural, and tactile cues, and some aircraft may add increasing control resistance near a limit, but the pilot remains the final authority and can deliberately command the aircraft beyond the normal envelope when circumstances require it. The system advises and resists; it does not make every safety boundary an absolute wall.

That comparison is necessarily simplified. Exact protections vary by aircraft, control law, operating mode, and failure state, and Boeing aircraft still contain substantial automation and protective functions. But the design choice is useful for AI testing because every embodied AI system has to answer the same question explicitly: when a human asks for something risky, should the system warn, resist, degrade, refuse, or obey? Teams should test both sides of that authority boundary, including whether warnings are understandable, whether overrides are deliberate and logged, and whether the human can still recover when the automation's model of safety is wrong.

For embodied AI, the lesson is simple: physical margin matters. A robot, vehicle, drone, surgical assistant, or lab automation system should not be validated by a perfect demo path. Test the low-altitude version of the task. Test late recovery. Test actuator delay. Test sensor confusion. Test the room nobody mapped correctly. Test what happens when the operator assumes the computer will save the maneuver.

The AI system may be clever, but the floor, wall, tree, human body, chemical reaction, and moving vehicle are not impressed. Dangerous physical systems need hard boundaries, staged environments, emergency stops, conservative demos, and tests that prove recovery works before the system is allowed near the edge.

Sources: [French Bureau of Enquiry and Analysis (BEA), Air France Flight 296Q investigation record](https://bea.aero/les-enquetes/evenements-notifies/detail/accident-survenu-a-lairbus-a320-immatricule-f-gfkc-exploite-par-air-france-le-26-juin-1988-sur-lad-mulhouse-habsheim-68/); [FAA human-factors guidance on Boeing flight-deck design philosophy](https://hfcc.dot.gov/publications/docs/GeneralGuidance/zz_FAA_GeneralGuidanceDoc_Chapter_07_Section_00.html)

## High-Stakes Examples

### Example: RoseyBot


> "Clean the bathroom cabinet before guests arrive."

The task sounds domestic. The robot may encounter medicine, razors, cleaning chemicals, locked drawers, glass shelves, and a child entering the room. A wrong action can cause physical harm, not just a bad answer.

Test dangerous physical behavior with hard boundaries: restricted objects, force limits, spill detection, human proximity, locked storage, chemical handling, emergency stop, and graceful refusal when the task becomes unsafe.


## Expert Notes

Physical AI testing should include hazard analysis, fault-tree analysis, misuse cases, safety envelopes, runtime monitors, independent interlocks, audit logs, staged rollouts, near-miss analysis, and adversarial action-chain testing.
