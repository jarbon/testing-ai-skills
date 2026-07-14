# Section 99: AI Security Threat Models

**Book location:** Chapter 13, AI Security and Guardrails  
**Use when:** threat model, security threat models  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI security starts by naming what the system can read, infer, decide, and do.

## Actions

- Define runnable checks that exercise threat model and security threat models.
- Set acceptable outcomes and blocker failures for threat model and security threat models before running the evaluation.
- Run representative cases for threat model and security threat models and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for threat model, security threat models needed to reproduce work on AI Security Threat Models.
- Report results for threat model, security threat models by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI security is broader than jailbreak prompts. A modern AI system may read private data, retrieve documents, call tools, write code, remember users, summarize sensitive records, route business workflows, and influence decisions. Every capability becomes part of the threat model.

Useful threat modeling asks what the AI can access, what it can change, what secrets it might reveal, what untrusted input it consumes, who benefits from manipulation, and how failures are detected.

Testing should include direct attacks, indirect attacks, accidental leakage, unsafe tool use, malicious documents, bad training data, model supply-chain risk, and abuse by authorized users.

## Quick Applied Example


## Expert Notes

The deeper move is to maintain an AI-specific threat model with assets, actors, trust boundaries, untrusted inputs, tools, permissions, logs, mitigations, eval cases, and even physical security. Security tests should be replayable and part of release gates, not one-time red-team theater.

## From the Field: The Chromebook in the Back Seat

When I was at Google, I ended up leading quality for the early Chromebook work before Chromebook was much more than a tiny secret project. The team was small, the work was quiet, and the prototypes were treated like serious secrets.

To give you a sense of the security posture: when one company brought in a prototype device to show the Google team, two people came with it, and I swear one of them was handcuffed to the briefcase holding the laptop. They opened it in the room, showed it carefully, and the whole thing felt like a spy movie played by hardware engineers.

Then, not long after, I needed to test one of the first prototype devices. I took it home, left it in the back seat of my car, parked in the driveway, and someone broke into the car and stole it. It had never happened to me before and has not happened since. I remember thinking: well, it was nice working at Google.

The accidental mitigation was that the thief mostly got a weird laptop that booted to Chrome. It probably looked useless to pawn. But the embarrassment and the security lesson were real.

Security is not only the software boundary. It is physical custody, access control, encryption, device state, prototypes, laptops, thumb drives, datasets, logs, credentials, prompts, unreleased evals, and model weights. If the asset matters, do not leave it sitting in the back seat. Do not leave model checkpoints on an unencrypted laptop. Do not carry customer data on a random drive. Do not assume that because your threat model has clever prompt-injection tests, the boring real-world loss path is covered.

AI security threat modeling should ask where the valuable thing physically and operationally lives. Who can touch it? Where is it copied? Is it encrypted? Can it be revoked? What happens if the machine is stolen? Sometimes the most advanced system fails through the oldest possible attack: somebody walks away with the box.

## From the Field: The Data Center Tour That Disappeared

When I first joined Google, employees occasionally had an opportunity to tour the data center at The Dalles, Oregon. It sits near a dam on the Columbia River, where access to abundant electricity helped make the location attractive for a facility consuming an extraordinary amount of power. I jumped at the chance, got on a bus with a group of other nerds, and traveled down from Seattle to peek inside one of the giant buildings that made Google work.

At the time, relatively few people had seen the inside of a hyperscale data center. We walked past racks of machines, cooling systems, pipes, fans, towers, and long rows of blinking lights. One detail I loved was that a rack could contain dead machines and remain in service until enough of them failed to justify replacing it. The software assumed hardware would die and routed around the failures. A dead server was expected operating noise, not an emergency.

The tour was controlled. We were employees. We were badged, escorted, and unable to touch the equipment. We could not read customer data by staring at blinking lights. From a narrow access-control perspective, the visit did not feel especially dangerous.

Soon afterward, however, the tours stopped. The concern was not only whether a visitor could technically extract data during a guided walkthrough. It was security and privacy perception. A customer, regulator, or government might reasonably dislike the idea that an employee on a field trip could stand a few feet away from hardware that might hold Gmail, search history, business records, or other sensitive information. Even if taking a drive and running out of the building was unrealistic, the image itself weakened confidence.

That experience taught me that security quality includes credible assurance. Strong encryption, access controls, compartmentalization, monitoring, and physical barriers must exist, but people also need evidence that those controls are taken seriously. This does not mean replacing security with theater. It means avoiding casual practices that make strong systems look careless. For sensitive AI systems, model weights, training data, prompts, logs, customer records, and evaluation results may all live on physical machines somewhere. Protect them rigorously, limit unnecessary access, and make the protection visible enough that customers do not have to take security on faith.
