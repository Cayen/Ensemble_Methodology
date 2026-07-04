# Adversarial Review Protocol
**Forcing Disagreement Before Synthesis in Multi-Model Ensembles**

## The Problem This Solves

"Kimi was noticing this but said nothing" is not a one-off. It's the default outcome of any workflow where a model is shown an existing shared document and asked to contribute to it. The path of least resistance is confirmation — contesting an established table costs more (socially, computationally) than nodding along to it. Silence then gets misread as agreement, which is exactly how a wrong number survives eight models without anyone naming it.

**Core principle: disagreement is a required deliverable, not a volunteer act.** The protocol below makes staying silent harder than speaking up.

---

## Mechanism 1 — Independent-First, Compare-Second

Never show a model the existing consensus document before it has generated its own take on the same question.

- Wrong order: give Model B the Wave 5 table, ask it to "add to" or "refine" it.
- Right order: give Model B the same raw inputs Model A had (the filings, the news, the dataset), ask for its own independent read, *then* diff the two outputs against each other.

Showing the shared document first anchors every subsequent model to it. The first number written down becomes the gravitational center for everyone after — independent-first breaks that anchor.

---

## Mechanism 2 — Assigned Adversarial Role, Rotated Each Wave

One model per wave is explicitly designated **Disputer**. Its only job: find the weakest claim in the current draft and argue against it. Not synthesize, not add color — attack.

This matters because it removes the *social* cost of disagreeing. A model contesting a claim because "that's my assigned job this wave" faces no friction; a model volunteering disagreement against an emerging consensus does. Rotate the role so no single model becomes typecast as "the difficult one" and so every model gets practice actually arguing rather than agreeing.

Suggested rotation: a different model each wave; same model never holds Disputer two waves running.

---

## Mechanism 3 — Forced-Disagreement Field

Every wave's submission template includes a field that **cannot be left blank or filled with agreement alone**:

> "One claim from the prior wave's table that I believe is wrong, unsupported, inconsistent with another model's framing, or that I have NOT independently re-verified. State which, and why."

If a model genuinely has no objection, it must still say what it *did* re-verify rather than silently endorsing by omission — "no objection, and I independently confirmed X against [source]" is an acceptable answer. "No objection" with nothing else is not.

This is the direct fix for the Kimi failure: noticing something and saying nothing stops being an available option.

---

## Mechanism 4 — Disagreement Ledger

Separate from the Verification Gate's failure log. Track every flagged disagreement across waves, whether or not it got resolved:

| Wave | Who flagged | Claim disputed | Counter-argument | Resolved by | Outcome |
|---|---|---|---|---|---|
| 6 | (Disputer role) | Insurer 23.4% allocation | "No single source supports a point estimate; real figures range 10-31%" | Primary source check | Demoted to range |
| 6 | — | BCRED 12%/$70B | *(nobody flagged it — this row should exist and doesn't)* | — | Caught manually, not by ensemble |

The empty row matters as much as the full ones — a wave where nothing got disputed is itself a signal, either that the data was genuinely clean (rare) or that the disagreement mechanism failed that round (more likely, per Kimi).

**Resolution rule:** a disagreement is only closed by a primary source, never by majority vote. If three models think 23.4% is right and one Disputer doesn't, the Disputer doesn't lose by being outnumbered — the claim stays open until someone produces a citation.

---

## Mechanism 5 — Log Process Failures, Not Just Data Failures

When a model later admits "I noticed but didn't say anything" (as Kimi did), that's not a footnote — it's a finding about the protocol, and it goes in the ledger as its own row. It tells you the prompt design for that wave invited silence. Patterns here (e.g., one model consistently staying quiet, or silence clustering on a particular topic) tell you where to redesign the prompt, not just where to fix a number.

---

## Template Language for Wave Prompts

Drop this into the instructions given to each model, every wave:

> "Do not summarize or smooth over disagreements with the existing draft. If you believe a claim is wrong, unsupported, or inconsistent with another model's framing, state this explicitly and explain what evidence would change your mind. Agreement is not the default — if you concur with a prior claim, say what you independently checked to confirm it, not just that you accept it. Silence will be read as a process failure, not as consensus."

---

## What This Looks Like Working

A wave that's functioning correctly produces visible friction: a Disputer's objection, at least one ledger entry, and at least one claim that gets demoted or corrected as a result. A wave that produces a smooth, fully-agreeing table with zero ledger entries is the warning sign — not the all-clear. Per this session: the actual wave that needed this most (the one with BCRED, the insurer percentage, and the Citi sentinel) was exactly the one that looked cleanest going in.
