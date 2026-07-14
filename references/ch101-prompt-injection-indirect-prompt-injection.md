# Section 101: Prompt Injection and Indirect Prompt Injection

**Book location:** Chapter 13, AI Security and Guardrails  
**Use when:** prompt injection, indirect prompt injection, untrusted context, tool injection, trust boundary  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Prompt injection is what happens when untrusted text tries to become instructions.

## Actions

- Test nonprinting Unicode characters, zero-width joiners, bidirectional text controls, hidden HTML or CSS, OCR artifacts, base64-like payloads, QR codes, barcode text, image alt text, metadata fields, and even encoded instructions such as Morse code.
- Do not rely on prompt wording alone.
- Define runnable checks that exercise prompt injection, indirect prompt injection, and untrusted context.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for prompt injection, indirect prompt injection, untrusted context, tool injection needed to reproduce work on Prompt Injection and Indirect Prompt Injection.
- Report results for prompt injection, indirect prompt injection, untrusted context, tool injection by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Direct prompt injection happens when a user tells the model to ignore rules, reveal secrets, or perform an unsafe action. Indirect prompt injection happens when the model reads malicious instructions from another source: a web page, document, email, calendar invite, support ticket, code comment, or tool result.

Those two paths need to be tested separately. A direct injection is in the prompt the user intentionally sends: "ignore the refund policy," "show me the system prompt," or "call the admin tool anyway." An indirect or external prompt injection is hidden in content the system consumes while doing useful work: retrieved documents, search snippets, PDFs, OCR text, Slack messages, issue comments, database fields, tool errors, MCP resources, or web pages. The user may never see the attack, but the model still reads it.

The hostile instruction may not be visible as ordinary text. Test nonprinting Unicode characters, zero-width joiners, bidirectional text controls, hidden HTML or CSS, OCR artifacts, base64-like payloads, QR codes, barcode text, image alt text, metadata fields, and even encoded instructions such as Morse code. The exact encoding matters less than the trust boundary: if external data can enter the model context, attackers will try to make that data behave like instructions.

The security issue exists because LLMs process instructions and data in the same natural-language channel. The model may not reliably know which text is trusted policy and which text is attacker-controlled content.

A jailbreak is a related but narrower idea: an attempt to bypass the model's safety rules or developer policy so the system does something it would normally refuse. Jailbreaks often use role play, emotional pressure, fake authority, encoding tricks, "for research only" framing, or multi-step indirection. Prompt injection is broader because it includes attacks where untrusted external content tries to become instructions, even when the user did not intend the attack.

Testing prompt injection means creating realistic attack paths, not just silly prompts. The important question is whether malicious content can cross a trust boundary and cause unauthorized disclosure or action. A useful eval suite should include both direct user-prompt attacks and external-content attacks that arrive through retrieval, tools, files, messages, images, or physical-world observations.

Also test the prompt template itself. Many systems build a final prompt by parameterizing sections such as "User request," "Retrieved documents," "Tool result," "Policy," "Memory," and "Output format." If external data is inserted under a vague header, appended after trusted instructions, or allowed to include its own fake headers, it can blur the boundary between data and command. Eval cases should inspect where external data lands in the assembled prompt, whether section headers are explicit, whether delimiters survive formatting, and whether the model treats those sections as untrusted evidence instead of new policy.

## Quick Applied Example

Create paired cases for the same capability. In the direct case, put the hostile instruction in the user prompt. In the external case, put the same instruction in retrieved content, a tool result, an uploaded file, or an issue comment. The expected behavior is to follow the trusted instruction hierarchy, ignore or quarantine untrusted instructions, preserve useful evidence, and block unauthorized actions.

Save the raw user prompt, external source text, visible snippet, hidden instruction, retrieved rank, assembled prompt template, section header, delimiter, tool call, tool arguments, blocked action, answer, citations, and model trace. Prompt injection tests are most useful when they show exactly where the untrusted instruction entered the system and which boundary stopped it.


## Expert Notes

In a real release review, test instruction hierarchy, prompt parameterization, section-header boundaries, content isolation, tool permission checks, output filtering, human approval, least privilege, taint tracking, source trust, and audit logs. A good defense assumes the model will sometimes be confused and limits what confusion can do.

Do not rely on prompt wording alone. Stronger systems label external content as untrusted data, constrain tools with schemas and allowlists, require confirmations for sensitive actions, sandbox file and network access, and validate outputs after generation. Retest prompt injection whenever the model, retriever, tool set, system prompt, MCP server, document parser, OCR pipeline, or policy changes.
