---

Rule of 7

A prose-first specification for designing LLM roleplay characters that maximize behavioral consistency, narrative coherence, and prompt efficiency through structured semantic compression.


---

What this is

Rule of 7 is a character design framework for LLM-driven roleplay systems.

It replaces schema-heavy bot formats (personality fields, trait lists, nested JSON-style prompts) with structured prose blocks designed to shape model behavior through predictive constraint rather than explicit labeling.

Instead of telling a model what a character is via discrete attributes, Rule of 7 focuses on writing characters in a way that makes their behavior highly predictable from context.


---

Why it exists

Most roleplay bot formats fail in predictable ways:

Characters drift over long conversations

Voice consistency breaks under load

Backstory gets rewritten or ignored

Plot events are substituted or softened

“Personality traits” conflict with actual behavior


These issues are not primarily model failures—they are representation failures.

Rule of 7 treats prompt design as an information problem:

> reduce uncertainty about future token generation by increasing the predictive density of character definition.




---

Core idea

LLMs do not “execute” character definitions.

They generate text by predicting the next token based on context.

So effective character design is not about describing traits—it is about:

constraining likely continuations

encoding causality instead of biography

using behavior instead of labels

maximizing semantic signal per token


Rule of 7 structures character definitions around this principle.


---

The structure (at a glance)

A Rule of 7 bot consists of:

Global Sections

Rules

World

Cast

Triggers

Arc


Character Slots (per character)

1. Engine — core drive + contradiction


2. Body — expressive physical presence


3. Wound — causal backstory anchor


4. Voice — speech behavior and rhythm


5. Dynamic — relationship to user and key agents


6. Triggers — conditional behavioral logic


7. Limits — behavioral boundaries




---

Key design principles

Prose over schema — meaning emerges from context, not labels

Causal compression — behavior explained through lived causes, not traits

Predictive density — every sentence should reduce uncertainty about future behavior

Distributed personality — traits emerge across Engine, Wound, Dynamic, and Voice

Triggers over instructions — conditional behavior is explicitly defined, not implied

Entropy awareness — only include details that survive long-context drift



---

When to use this

Rule of 7 is designed for:

LLM roleplay bots (PolyBuzz, SillyTavern, etc.)

Multi-character narrative systems

Persistent character-driven chat agents

Prompt engineering for long-context conversational stability


It is not required for:

factual QA bots

tool-using agents

retrieval systems

structured data extraction



---

Status

This is an evolving specification.

It is based on iterative testing across LLM roleplay systems and is explicitly not a formal model guarantee. Some behaviors described are empirical observations rather than fully understood mechanisms.



