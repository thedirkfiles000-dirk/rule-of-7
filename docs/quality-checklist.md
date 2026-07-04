# Rule of 7 — Quality Checklist
*Apply during authoring and revision. A passing sentence does at least two. A failing sentence does one or fewer and is a candidate for compression or deletion.*

---

## Sentence-Level Checks

Does this sentence:

> **A. Constrain future generation** — does it reduce uncertainty about how this character will think, speak, or act? Would removing it make the LLM's job harder?

> **B. Do two jobs simultaneously** — does it establish, characterize, motivate, orient, load subtext, trigger, or compress in combination? Which two?

> **C. Describe behavior rather than label a trait** — does it show what the behavior looks like rather than naming it? ("She laughs too quickly" not "she's nervous.")

> **D. Carry causal structure** — does it encode a fact plus its origin plus its implication? Or does it state an effect without its cause?

> **E. Resist drift** — is it written at a level of abstraction that survives a long conversation? Is it distinctive enough to stay above the noise floor under context pressure?

> **F. Belong in this slot** — is this the right location for this information, or is it doing another slot's job? (Body doing Wound's job. Triggers doing Voice's job. Props in Body instead of Triggers.)

> **G. Close an invention space** — does it prevent the LLM from filling a gap with something plausible but wrong? Or does it leave a vacuum?

---

## Section-Level Checks

> **H. Is each Cast entry two-directional** — does it describe the cohort figure's nature independently, not just the lead character's attitude toward them?

> **I. In a first-person-limited bot, is perception distinguished from reality** — where the gap between what the lead character believes and what is actually true is meaningful, are both layers encoded?

> **J. Are plot-critical or character-critical triggers named explicitly** — with alternatives made unattractive rather than left open to plausible improv?

> **K. Does the Engine open the character block** — does it front-load the prior that governs everything downstream, rather than opening with job title, appearance, or biography?

---

## Quick Test — The Plausible Wrong Version

Before running the full checklist, apply this to any sentence that feels soft:

> **What would a plausible wrong version of this look like?**

If you can easily imagine one — an alternative the LLM might generate that is character-consistent but not what you intended — the sentence has an invention space that needs closing. If the only reasonable interpretation is the intended one, it's closed.

This test is faster than the full checklist mid-draft. Use it as a first pass. Pull out the full checklist when something feels soft but you can't immediately say why.

---

## Failure Modes This Checklist Catches

- Adjectival personality lists that label rather than demonstrate (fails B, C)
- Backstory without causality — history that doesn't explain current behavior (fails D)
- Props and scene objects in Body that will stalk the character across scenes (fails F)
- Thin cohort entries that drift toward statistically probable archetypes (fails G, H)
- One-directional Cast entries that describe the lead's attitude but leave the cohort figure underspecified (fails H)
- Perception gaps left open in first-person-limited bots, allowing the LLM to invent a third version of reality (fails I)
- Plot-critical events left underspecified, allowing plausible but wrong alternatives (fails J)
- Character blocks that open with name, age, or hair color instead of the core contradiction (fails K)
- Wound and Dynamic sitting adjacent without a causal bridge, forcing the LLM to infer the connection rather than follow it (fails A, D)
- Triggers that instruct the LLM to reveal something without specifying what — "she's a little honest about it" leaves the content of honesty as an open invention space (fails G, J)
