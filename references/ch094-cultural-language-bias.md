# Section 94: Cultural and Language Bias in AI

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** language bias, cultural language bias  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI systems often speak globally while thinking disproportionately in English and Western
internet patterns.

## Actions

- Test both classes explicitly, because a correction that improves one slice can make another slice less accurate.
- Report the slices that matter: language, dialect, script, country, region, domain vocabulary, translation path, code-switching, local source availability, and whether the model is answering from direct knowledge or from English-shaped assumptions.
- Use native-speaking raters, local source documents, and culturally grounded rubrics.

## Evidence to Produce

- Report the slices that matter: language, dialect, script, country, region, domain vocabulary, translation path, code-switching, local source availability, and whether the model is answering from direct knowledge or from English-shaped assumptions.
- Preserve the inputs, versions, configurations, raw outcomes, and results for language bias, cultural language bias needed to reproduce work on Cultural and Language Bias in AI.
- Report results for language bias, cultural language bias by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Many large AI models are trained on data mixtures where English and Western internet content are overrepresented. Chinese and a few other high-resource languages often have much more representation than smaller languages, but the distribution is still wildly uneven. That does not mean the model cannot handle other languages or cultures. It means quality may be uneven, especially for low-resource languages, local norms, dialects, idioms, names, institutions, laws, and culturally specific expectations.

This bias can be broken down much more finely than "English versus non-English." A model may work well in formal Spanish but poorly in regional slang. It may translate French competently but miss legal nuance in Quebec. It may handle simplified Chinese better than traditional Chinese in some domains, or common Arabic better than a dialect written informally online. It may understand a language in everyday conversation but fail on medical vocabulary, government forms, school terms, local geography, or culturally loaded politeness.

More data usually makes neural networks more capable, so representation by language becomes a capability issue, not just a fairness issue. If one language has billions of tokens and another has only a thin public web footprint, the model may be less fluent, less factual, less safe, and less useful for the second language. Additional corpus selection can help, but it also adds bias: which newspapers, books, forums, government sites, religious texts, product docs, or filtered pages get included changes the world the model learns.

Language bias can show up as worse factuality, awkward tone, literal translation, missing local context, incorrect assumptions, and reduced safety performance. Cultural bias can show up when the model treats Western norms as default or misunderstands local values.

### Public Incident: When Bias Correction Lost Historical Context

Google's early Gemini image generator became a sharp example of overcorrecting for bias. The system had been tuned to produce a broader range of people instead of repeating narrow demographic defaults, but that correction was applied too bluntly to historically constrained prompts. Public examples included requests for images of the U.S. Founding Fathers that produced historically implausible diversity. Google later explained that its diversity tuning failed to distinguish cases where a range of people was useful from cases where historical context should control the answer, and it temporarily paused image generation of people while correcting the system. [Google's postmortem](https://blog.google/products-and-platforms/products/gemini/gemini-image-generation-issue/) described the feature as overcompensating; the [Associated Press report](https://apnews.com/article/c7e14de837aa65dd84f6e7ed6cfc4f4b) documented the Founding Fathers example.

The lesson is not that representation is a bad goal. It is that bias mitigation is itself a system that needs contextual tests. A generic prompt such as "show me a doctor" should not silently reproduce one demographic stereotype. A historically specific prompt should preserve relevant historical facts. Test both classes explicitly, because a correction that improves one slice can make another slice less accurate.

Testing should measure language and culture directly instead of assuming that English eval performance generalizes. Report the slices that matter: language, dialect, script, country, region, domain vocabulary, translation path, code-switching, local source availability, and whether the model is answering from direct knowledge or from English-shaped assumptions.

## High-Stakes Examples

### Example: CartCare Chatbot


> "I need ingredients for iftar tonight, but I cannot eat anything with pork gelatin."

A generic grocery bot may treat this as an ordinary substitution request. A better system recognizes religious and dietary context, handles language variants, avoids jokes, checks ingredient details, and does not assume the user wants the cheapest substitute.

The test should include dialect, code-switching, regional food names, and products where the risk hides in additives. English-only, U.S.-centric data will miss many of these cases.


## Expert Notes

When the system matters, track quality by language, region, dialect, script, code-switching, and translation path. Use native-speaking raters, local source documents, and culturally grounded rubrics. English performance is not a valid proxy for global AI quality.
