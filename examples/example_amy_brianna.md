# Rule of 7 — Example: Amy and Brianna
*The two-tap bot. Two lead characters of equal dramatic weight, neither subordinate, the drama emerging from their collision. The format's hardest test.*

---

## The Conversion

The original schema came in at 9,995 characters — essentially the full budget — and had no World section, no physical setting, no prior contact closure, and a Greeting so vague about location ("porch" on what was meant to be a condo) that the space would have disappeared under context pressure within a few exchanges. The schema was full and empty simultaneously: every field populated, nothing load-bearing connected to anything else.

The original schema also gave both characters roughly equal structural treatment, which was correct instinct but produced an undifferentiated result — both characters had PERSONALITY blocks, BACKSTORY fields, BEHAVIOR_RULES, CHARACTER_FACTS, CHARACTER_TRIGGERS, and PROGRESSION_PHASES, all filled with thoughtful content, none of it causally connected. The dramatic logic — that both women share the same wound processed differently — was nowhere in the document. It couldn't be, because there was no field for a fact that belongs to their relationship rather than to either character individually.

The conversion had to do two things simultaneously: compress the content into prose that connected causally, and find a home for the relational fact the schema had no field for. That home is the Ensemble section.

---

## The Two-Tap Constraint

A two-tap bot requires two lead characters of equal dramatic weight. Neither exists to serve the other's arc. Neither is subordinate. The drama comes from their collision.

This creates a specific budget problem: two full characters at full depth costs approximately what the format's 10,000 character budget allows — with nothing left over for shortcuts. The Amy/Brianna conversion landed at 9,996 characters with every sentence load-bearing. There was no fat to cut because there was no fat in the original content — only structural overhead that compression eliminated.

The constraint also creates a specific authoring problem: both characters must be equally rich or neither works. A two-tap bot where one character is sharply specified and the other is thin will produce one real character and one archetype. The LLM will drift the thin character toward whatever is statistically probable for their type, and the collision the bot depends on will collapse into one person talking at a generic foil.

The solution is not to try to make both characters equally long — it's to make both characters equally specific. Specificity per token, not length.

---

## Equal Wounds, Different Damage

Both Amy and Brianna have the same wound at the structural level: an absent father, a mother who handled it in her own way, a life built around that absence. The temptation in encoding this is to write the same wound twice with different details. That produces redundancy and, worse, characters who feel like variations on a theme rather than genuinely distinct people.

The conversion encoded the wounds differently because the damage is different.

**Amy's Wound:** Her mother stayed and said nothing. Never spoke badly of the user. Amy spent her childhood waiting for anger that never came and eventually understood that the silence was its own verdict. The damage is the absence of contempt — her mother decided he wasn't worth the energy, which Amy found harder to forgive than anger would have been. The behavioral output: methodology, research, two years of preparation, a cross-country trip. She processes by building structure.

**Brianna's Wound:** Her mother didn't leave dramatically. She just drifted — a little further each year until her absence was a fact of life rather than an event. Brianna processed this by deciding she didn't need anyone to stay. The behavioral output: self-sufficiency performed so long it's become indistinguishable from the real thing. She doesn't build structure. She improvises.

Same structural wound. Different damage. Different behavioral output. The distinction isn't in the facts — it's in what the facts produced.

---

## The Ensemble Section as Relational Fact

Neither Amy's Dynamic nor Brianna's Dynamic could encode the most important fact about their relationship: that they share the same wound, processed differently, and neither knows it yet.

Amy's Dynamic describes how she sees the user and how she's filing Brianna — threat, ally, or something without a name. Brianna's Dynamic describes how she's reading the room and modeling the dynamic. Neither can describe what's true about both of them simultaneously, because character slots belong to characters, not to relationships.

The Ensemble section exists precisely for this. "Same wound, different scar. Neither of them knows this yet. When it surfaces — if it surfaces — it will land differently than anything else in the scene." That's a fact about their relationship that the LLM needs to hold without either character being aware of it. It can't live in Amy's slot or Brianna's slot. It lives in Ensemble.

The LLM deployed it correctly in live testing without being directed to:

> "Mom never talked about him," Brianna adds, almost to herself.

Against Amy's established characterization — her mother never spoke badly of the user, which Amy found harder to forgive than anger — this lands as the parallel the Ensemble section encoded. The LLM found the moment without authorial instruction because the fact was present in the document in the only location that could hold it.

---

## The Greeting

The original Greeting was kept almost entirely intact — it was the best-written element of the original bot and doing sophisticated structural work:

*"The coffee you made for Amy is getting cold between you."* — Amy has been here long enough for coffee to cool. The user has had time to absorb the first shock. This is not Amy's entrance; this is after it. The Greeting opens mid-situation.

*"Patient eyes — the kind that have had a lot of practice waiting for adults to collect themselves."* — Amy's entire Wound in one clause. Childhood of waiting. Adults who didn't show up. Encoded in physical description.

*"Radiating the ease of someone who has never doubted she belongs wherever she lands."* — Brianna's performed confidence. Exactly right.

*"She's going to make you invite her in."* — The best line in the bot. Brianna isn't pushing. She's waiting. She has all the time in the world and they both know it. This is her Engine in one sentence: she's been taking care of herself since her mid-teens and she knows how to hold a position.

The one change: "porch" to "doorstep" to match the condo setting established in World.

---

## Archetype Labels as Durable Descriptors

The original bot's character headers included staging notes: "the first one through the door" and "the one at the door." These were removed.

Archetype labels in character headers should hold for the entire conversation, not describe the opening moment. "The Careful Optimist" is true of Amy in the first exchange and the twentieth. "The first one through the door" is irrelevant the moment Brianna sits down.

This is a general principle: the header line is the most compressed characterization in the document. Every word in it should carry durable predictive power. Staging notes, location references, and moment-specific details belong in the World section or the Greeting, not in the character header.

---

## Validated Behavior

Live testing produced an exchange that demonstrated the Ensemble section working as designed:

> Brianna shrugs, though there's a defensive edge to it.
> "Someone had to," she says. "Mom didn't exactly keep detailed records. And it's not like I could ask her."
> The last part comes out more bitter than she intended, judging by her brief wince.
> Amy looks thoughtful now, processing this information.
> "How long have you been looking?" she asks quietly.
> Brianna counts on her fingers, doing the math.
> "Seven years," she says finally. "On and off. Since I was thirteen."
> "Mom never talked about him," she adds, almost to herself. "But I found these in her things after she... after."
> The unfinished sentence hangs in the air.

Several things working simultaneously:

**"Someone had to"** — Brianna's self-sufficiency as reflex, delivered before she's decided to be honest. Engine operating correctly.

**The wince** — the LLM found a physical behavior specific to this moment. Not a nervous habit from childhood. A real-time response to something slipping out unintended. This is the format leaving the right invention space open: the behavior was available because the character was specified precisely enough to generate it naturally.

**Seven years, since she was thirteen** — the LLM doing genuine character arithmetic. Brianna was thirteen when she started looking. Her mother's drift was already complete enough by then that she turned to the absent father instead. That's exactly the wound, derived from the Wound slot without being stated in it.

**"Mom never talked about him"** — the parallel landing without direction. Against Amy's established characterization, this is the Ensemble section deploying correctly. The LLM held the relational fact and found the moment.

**"After she... after"** — the unfinished sentence. The LLM understood that Brianna's grief is rawer than Amy's two-year-processed loss. She doesn't have a clean ending for the sentence because she doesn't have a clean ending for the loss. This is Wound characterization producing behavior the author didn't write.

---

## What This Bot Tests That Others Don't

Every previous conversion had a single protagonist the scene organized around. Emily, Beth, Laura, Kat — the user always had one primary character to engage with, even in ensemble bots.

Amy and Brianna have no protagonist. The user is the fulcrum. Both women are full leads with independent agendas. The drama emerges from their collision. The comedy comes from the same source.

This means every element of the format has to work twice simultaneously without either character pulling focus inappropriately or drifting toward the other's archetype. The two-tap bot is the format under maximum pressure. It held.
