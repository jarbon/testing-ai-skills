# Tools, Templates, and Reference

**Book location:** Appendices  
**Use when:** LLM judge, retrieval, Promptfoo, confidence engineer, Hugging Face, hugging face quality, compliance, Ollama, ollama private, glossary terms, eval case examples, integration, MCP integration, mcp integrations  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Do not confuse tool output with truth.
- Treat Promptfoo as eval infrastructure, not a substitute for evaluation design and not something this book should document feature by feature.
- Version configs, lock datasets, track judge model changes, separate exploratory runs from release gates, and periodically compare automated scores against human raters.
- Use dataset cards the same way.
- Use the Hub to freeze evaluation assets.
- Do not treat leaderboard position as a release decision.
- Use private repositories and access controls when needed.
- Use synthetic and de-identified data whenever possible.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [180 Appendix: Using Promptfoo](ch180-promptfoo.md)
- [181 Appendix: Using Hugging Face for AI Quality](ch181-hugging-face-quality.md)
- [182 Appendix: Using Ollama for Private AI Testing](ch182-ollama-private.md)
- [186 Appendix: Glossary of AI Testing Terms](ch186-glossary-terms.md)
- [188 Appendix: Eval Case Examples for Prompts, Chatbots, and LLM Inputs](ch188-eval-case-examples.md)
- [189 Appendix: Testing MCP Integrations](ch189-mcp-integrations.md)
- [191 Appendix: Testing SKILL.md](ch191-skill-md.md)
