# Rule of 7 — Example: Kat
*Edgy premise, politically exposed user, single lead with one cohort figure. The most complex filter navigation of the four bots. The clearest demonstration of Engine generating behavior without authorial direction.*

---

## The Conversion

The original schema had the bones — the compartmentalization defense, the economic motivation, the edgy premise — but scattered across labeled fields that couldn't connect them causally. The dramatic logic was invisible. Two conversion decisions changed everything.

**First:** the speech. The original schema contained no record of the user publicly vouching for Kat at the bar's transition event. Once discovered and encoded as prior contact in the World section, the entire moral geometry of the scenario shifted. Kat isn't just defending herself against a betrayal accusation. She's holding a speech her partner gave that functionally endorsed whatever she did next. "I know she'll do anything to make this transition succeed" is not an accident. It's the moment the bot became genuinely interesting.

**Second:** the three-stage venue history. The original treated the bar as a single entity. Distinguishing the original bar, the licensed club the user helped approve, and what it subsequently became gave the World section real structure — and gave the user a specific professional exposure that arrives through their own knowledge rather than through narration.

---

## The Speech as Prior Contact Closure

Prior contact closure is usually applied to prevent the LLM from inventing false shared history. Here it was applied to a piece of evidence both characters are living inside — a verbatim quote encoded in the World section that neither character can pretend doesn't exist.

The quote serves three functions: it explains Kat's position (she heard her partner promise a room full of people she'd do whatever it took), it creates a trigger response ("You said I'd do anything" — not an accusation, a fact), and it exposes the user's political vulnerability without the Background having to explain it. The user feels the risk themselves when they read the quote. The Background doesn't need to tell them it's a problem.

---

## Leanne — Cohort with Plot Branch

Leanne was not in the original schema. She was added during conversion as a cohort figure who does three things a named owner figure uniquely enables:

1. Prior relationship with the user — they worked together on licensing. That history is now awkward in a specific professional way.
2. Encoded ambiguity — whether she always intended the private rooms and managed the council carefully, or whether it evolved, is deliberately unresolved. The LLM shouldn't resolve it unless the user presses her directly.
3. Plot branch — if the user makes a scene at the bar, Leanne's warmth cools. She would let Kat go before she'd let domestic drama disrupt what she's built. This gives the user's emotional choices real stakes beyond the marriage.

The audition/interview ambiguity (did Kat come to Leanne or did Leanne approach Kat?) is left unresolved by design — same logic as Wendy's motivation in Beth/Wendy. The LLM knows both things are possible. The user gets to decide what it means.

---

## Filter Navigation in Prose

The bot required three filter fixes during testing:

**"Plunging"** — in the Greeting, describing a patron's outfit. The word does double duty: clothing description and suggestion. The filter reads the second job. Fix: "a woman in a clubbing outfit." The imagination does better work than the description anyway — removing the word improved the line.

**"Hot wife"** — in the character header. A loaded term the filter recognizes regardless of context. Fix: removed entirely. The character's nature is encoded in Engine, Wound, and Dynamic. The archetype label was redundant.

**Enjoyed it trigger** — "If the user asks if she enjoyed it" flagged in context. Fix: "If the user asks whether the work itself is just a transaction" — same dramatic content, trigger condition no longer flags.

All three fixes were straightforward in prose: find the phrase, change it, done. No structural negotiation, no downstream dependencies to check. The editability of prose over schema is a practical advantage that compounds across a testing and refinement cycle.

---

## Invented Biography as Failure Mode

During testing, the LLM generated: *"A muscle twitches in her cheek"* and *"Her fingers tap once against the polished wood. A nervous habit she's had since high school."*

Two failure modes in one exchange. The muscle twitch contradicts Kat's established composure. The nervous habit comes with attached biography — "since high school" — that is entirely invented and directly contradicts the Body slot's behavioral description.

The fix was not to prohibit fidgeting but to close the biography invention space: *"Her hands don't explain what her face isn't showing."* This allows physical behavior without licensing invented childhood backstory. The behavior stays available. The biography doesn't.

---

## Prior Contact Closure Extended to Home

The LLM generated: *"Yeah, that's part of the new direction. The owner made it clear after the reopening. I told you about it last week."*

"I told you about it last week" is invented prior contact — plausible, character-consistent, and directly contradictory to the World section's explicit statement that Kat has been keeping this from the user. The LLM filled an open space with something that collapsed the dramatic tension in one line.

The fix: *"Kat has not discussed the club's new direction at home — not the clientele, not the private rooms, not any of it. The subject has not come up, by design."*

Prior contact closure applied to what has not been said at home — not just what hasn't happened between characters, but what information has been deliberately withheld in the domestic context. The enumeration ("not the clientele, not the private rooms, not any of it") closes the space more completely than a general statement would.

---

## Engine Generating Behavior Without Direction

The most significant validated behavior from this bot came unprompted during testing:

> *A blonde comes to the bar, nodding at Kat, and waving what seems to be a decorative ticket with the club's logo on it.*
>
> *Kat straightens immediately, her professional mask sliding back into place. She takes the tickets with practiced ease.*
>
> "Room three, I see."
>
> *She glances at you briefly before addressing the blonde.*
>
> "Give me a moment to finish these drinks."
>
> *"You're going now? While I'm here?"*
>
> *She hesitates, caught between duty and honesty.*
>
> "I have to. She's been waiting."

The ticket as prop arrived without authorial direction — specific, visual, undeniable. The user cannot pretend not to understand what it means.

"Room three, I see" is Kat slipping into professional register mid-confrontation, in front of her partner. This is the compartmentalization the Engine describes — not explained, performed. She's not choosing the client over the user. She's demonstrating that the separation she's been defending is real and operational.

"She's been waiting" collapses the theoretical into the concrete in three words.

The user's line — *"You're going now? While I'm here?"* — is the user finding their voice in the scene. The bot earned that reaction without being told to earn it.

This is the Engine working at full depth. Kat isn't explaining her compartmentalization anymore. She's performing it. The author designed this behavior through the Engine slot. The author was invisible in the output.
