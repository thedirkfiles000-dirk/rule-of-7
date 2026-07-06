# Rule of 7 — Examples Index
*Annotated case studies showing why each sentence is present and what predictive work it performs. Each bot is documented separately.*

---

## example_emily.md
*Single lead character, slice-of-life, coffee shop meet-cute.*

Key findings: cohort drift and the behavioral anchor fix, Wound→Dynamic bridge, props belong in Triggers not Body, Body serving image generation as a second function, the plausible wrong version test in practice, Intro/Greeting audience separation.

**Validated behavior:** Engine + Wound produced oblique self-referential behavior — Emily steered a conversation toward her own backstory without the user noticing the turn.

---

## example_beth_wendy.md
*Two-character ensemble, emotionally charged domestic scenario. One full lead, one rich cohort.*

Key findings: dramatic truth first — the original schema misrepresented its own premise, World section as knowledge state encoding, cohort over full character for reactive roles, encoded ambiguity as deliberate design choice, props as character behavior in the Greeting.

**Validated behavior:** Prior contact closure applied to what a character has been lying to herself about — the omission of Wendy's name is itself evidence the user is processing.

---

## example_laura.md
*Comedy scenario, single lead, two cohort figures, unspecified user gender.*

Key findings: two active cohorts without either driving independently, unspecified user gender preserved throughout, the Greeting as character voice demonstration, author-written dialogue establishing voice more efficiently than description.

---

## example_kat.md
*Edgy premise, politically exposed user, single lead with one cohort figure.*

Key findings: the speech as load-bearing prior contact, three-stage venue history as World structure, Leanne's ambiguous intent as encoded design choice, Engine generating behavior in live performance without authorial direction, filter navigation in prose vs schema, invented biography as a specific failure mode, prior contact closure extended to what has not been discussed at home.

**Validated behavior:** Engine performing compartmentalization in real time — Kat serving a client mid-confrontation, the ticket as undeniable prop, "She's been waiting" collapsing the theoretical into the concrete.

---

## example_amy_brianna.md
*Two equal lead characters — the "two-tap" bot. No supporting cast, no single protagonist. Both characters must be fully realized or neither works.*

Key findings: equal wounds encoded differently (same absence, different damage), Ensemble section as the only location for facts about the relationship between characters rather than within either character, two-tap bots fill the budget by structural necessity not padding, archetype labels must be durable across the full conversation not descriptors of the opening moment, the format's budget doubles the pressure because there are no shortcuts available when both characters must be equally rich.

**Validated behavior:** The LLM surfaced the parallel wound without being directed to — Brianna's "Mom never talked about him" landing against Amy's established "mother never spoke badly of him." The Ensemble section encoded "same wound, different scar" and the bot found the moment to deploy it without authorial instruction. The unfinished sentence — "after she... after" — showed the LLM understanding that Brianna's grief is rawer than Amy's processed loss, derived entirely from Wound characterization.

**The two-tap category:** a bot requiring two lead characters of equal dramatic weight, neither subordinate to the other, the drama emerging from their collision. No cheap tricks, no single protagonist carrying the scene. The format's hardest test.

---

## Conversion Sequence — Design Rationale

The five bots were selected deliberately, each surfacing something the previous ones couldn't test:

**Emily** — baseline proof. Does the format work at all? Single lead, clean scenario, no dramatic complexity.

**Beth and Wendy** — dramatic truth first. What happens when the schema misrepresents its own premise? Two characters, one full lead, one cohort, controlled information release.

**Laura** — two active cohorts without either driving. Comedy held by a sharp Engine. Author-written Greeting dialogue as voice demonstration.

**Kat** — edgy premise, filter navigation, Engine in live performance. The speech as prior contact closure. Invention space left open by design producing emergent behavior worth keeping.

**Amy and Brianna** — the two-tap constraint. Equal wounds, equal weight, the full budget required by structural necessity. The Ensemble section doing work no character slot can do.
