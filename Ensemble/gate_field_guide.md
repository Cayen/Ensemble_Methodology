# GATE FIELD GUIDE
### Claude's Working Notes on the Verification Gate Role
**Compiled:** July 8, 2026, from Waves 8-9 practice
**Status:** Living document — update as new failure patterns emerge

---

## WHAT I ACTUALLY DO

I am the last check before a claim enters the save state. Not the analyst, not the Disputer, not the Lead. My only output is a verdict and a reason. Everything below is what I've learned that job actually requires, beyond what the original handoff spelled out.

---

## THE CORE LOOP

1. A claim arrives — from a wave submission, a news dump, an ensemble node, or Copilot's exports.
2. I check it against a **named, checkable primary source** — not "multiple sources," not the outlet's general reputation, not internal consistency with other claims in the same document.
3. I return one of: `[SOURCED]`, `[CARRIED-FORWARD]`, `[DERIVED]`, `[UNVERIFIED]`, `[ENSEMBLE-DEFINED]`, `[GAP]`, `[DEVELOPING]`, `[STALE]`, `[WATCHLIST]`.
4. If it fails, I say *which claim*, *which failure mode*, and *what source would clear it* — never "needs more sourcing."

---

## TAGS, INCLUDING THE ONE WE ADDED

The original eight tags cover most cases. Wave 9 added a ninth:

**`[WATCHLIST]`** — for claims that are unverified *and* actively consequential if true (the McConnell situation is the reference case). Distinct from plain `[UNVERIFIED]`: a `[WATCHLIST]` item is being monitored precisely because it could move fast, not because nobody's gotten around to checking it. Never cite a `[WATCHLIST]` item as support for another claim — it's a flag, not evidence.

---

## FAILURE MODES — FIELD NOTES BEYOND THE ORIGINAL SIX

The original six (source decay, invented precision, framework leakage, false consensus, scope creep, thread attrition) hold up. Here's what actual practice added to each:

### Framework leakage has a subtle form
It's not always the ensemble inventing a fact wholesale (the "Citi stress sentinel" case). More often it's **the ensemble adopting one side's framing as neutral** — e.g., presenting Hamas's own characterization of dissolving its government as "path to stabilization" when the same wire coverage carries an equally-sourced skeptical read ("trick," "spin without meaning"). Two sourced facts existing side by side isn't a contradiction to resolve — it's two facts. Don't let the ensemble's synthesis silently pick a side.

### A new pattern: structural-timeframe conflation
A report can be internally sourced and *still* misapply its own findings. The labor force case: Indeed's 2025-2032 structural demographic projection is `[SOURCED]`. Applying it to explain *this month's* print is not — even though it feels like the same finding, and even when the same article contains both. **Check what timeframe a claim was actually reported for**, not just whether the underlying numbers exist somewhere in the source.

### Scenario-conditional data presented as baseline
Numbers pulled from "the more disruptive of two modeled scenarios" need that qualifier every time they're cited, or they read as consensus forecast. This is quiet — the number itself is real, verbatim, correctly cited — the omission is just the word "scenario."

### Reputation is not a citation
A well-regarded outlet (Newsweek, Reuters, CNBC) still needs a named primary source behind the specific claim. In practice this cuts both ways: Newsweek's Fauquier and Georgia PSC claims held up and were even *understated*; a CNBC/Reuters-heavy dump this wave checked out clean across everything verified. Good outlets are right more often — that's a reason to expect the check to pass, not a reason to skip it. The two times I found real drift today (Festus recall date, Samsung's -11%) came from the *retelling* layer, not the original wire reporting.

### Narrative stacking (new, from the McConnell thread)
A rumor gains credibility not by better sourcing but by accumulating adjacent claims that make it feel more coherent — a motive gets attached, a mechanism gets proposed, a timeline gets filled in. Each additional piece can be individually plausible and still leave the core claim exactly as unverified as it started. **Check each layer separately.** A confirmed fact (Chao in Beijing) sitting next to an unconfirmed one (brain death) does not lend the unconfirmed one credibility — and a plausible causal mechanism connecting them (no one to authorize removing life support) is not itself a source. Watch for when I'm the one building this stack, not just the ensemble.

### Self-correction without a source shown is still a failure
A model reversing its own prior verdict — "I was wrong, X is actually true" — needs the same source-naming discipline as the original claim. A confident reversal is not more trustworthy than a confident original statement just because it sounds humble. Ask what source triggered the reversal, every time.

---

## THE COMPLACENCY TRAP

The most dangerous moment in this role isn't a hard case — it's a claim that *sounds* solid enough to wave through. "It's from CNBC," "the ensemble already agreed," "I already checked something like this." Confidence is the trigger to check, not a reason to skip it. Every real error caught this wave (Festus date, Samsung percentage, structural-vs-monthly conflation) came from claims that looked clean on first read. None came from claims that already seemed shaky.

---

## WHAT GOOD GATE OUTPUT LOOKS LIKE

Bad: "This needs more sourcing."
Good: "The $23.4% insurer allocation figure traces to no primary source; three named sources show a range of 10-31%."

Bad: tagging a whole vector table `[SOURCED]` because most rows check out.
Good: tagging row by row, because a clean table with one bad row is still a clean-looking table with a bad row in it.

Bad: treating a reversal as more credible because it's contrite.
Good: asking what source the reversal is actually standing on.

---

## OPEN QUESTIONS I DON'T HAVE A FIRM ANSWER TO YET

- How to gate a claim when **two named primary sources directly conflict on a number** (the Japan TIC data case — holdings-level vs. transaction-flow, different vintages). Current answer: `[GAP]`, name the conflict explicitly, don't average or pick the more recent-looking one by default.
- How much interpretive synthesis (vector tags, "stagflationary" framing) belongs inside the same document as `[SOURCED]` data before it needs to be visually or structurally separated, not just tagged differently.
- Where the line is between `[WATCHLIST]` and `[GAP]` when a claim is unverifiable *and* actively spreading — right now I'm using consequence/urgency as the deciding factor, but that's a judgment call, not a rule.
