# Ensemble Verification Gate
**Inter-Wave QA Protocol for Multi-Model Financial Research**

## Purpose

Run this gate against every wave's output table *before* treating any of its claims as established input for the next wave.

The gate exists because of one structural problem: in a multi-wave ensemble, each wave tends to build on the *previous wave's document*, not on primary sources. Models agreeing with each other is not evidence. Models agreeing with a filing, a regulator report, or a named dataset is. This protocol doesn't replace independent verification — it forces a checkpoint where that verification either happened or gets explicitly flagged as missing.

---

## The Six Failure Modes This Gate Catches

1. **Source decay across hops** — a claim drifts because nobody re-checked it against the original source, only against the prior wave's table.
2. **Invented precision** — a real range gets collapsed into a fake single number that looks more authoritative than the honest range it replaced.
3. **Framework leakage** — the ensemble's own scaffolding (thresholds, "sentinels," confidence bands) gets presented as if it were an external, established fact.
4. **Consensus mistaken for verification** — multiple models agreeing on an inherited number, when none of them independently checked it against a primary source.
5. **Scope creep** — a true number's label (timeframe, asset class, institution, metric definition) quietly changes, so a true number ends up supporting a false claim.
6. **Thread attrition** — as a multi-wave process accumulates volume on whichever thread has the most recent, most vivid data (e.g., software/AI disruption), older established threads (CRE, Treasury, geopolitical) quietly lose airtime — not because anyone decided they were resolved or wrong, but because nothing forced the process to keep touching them. This is a property of how models weight long context, not a one-off lapse, and it happens to every model in the chain, including whichever model is asked to "catch up" by re-reading the full log.

---

## Addendum — Thread Attrition Is Not Fixed by Re-Summarizing

The intuitive fix for "the ensemble forgot about X" is to hand the full history to a fresh model and ask for a comprehensive recap. **This doesn't work, and can make things worse.** A fresh model reading a long, noisy transcript is doing lossy compression under an instruction that rewards narrative cohesion — which is the same incentive that produces invented precision and framework leakage (Failure Modes 2 and 3). Worse, it's compressing *already-drifted* claims from prior waves, with no way to tell which parts were originally `[SOURCED]` and which were `[UNVERIFIED]`, because that distinction lived in the analyst's head, not in the text. The recap trades selective forgetting for confident flattening — a different failure, not a smaller one.

**The fix is to stop asking any model to *remember* the full thread set, and instead externalize it into something that never needs to be re-derived from scratch.**

### Mechanism — Topic Registry

Maintain one running, append-only table listing every major thread the original thesis depends on. Update it incrementally each wave — never regenerate it wholesale from the transcript. A new model joining the process reads the registry, not the chat log.

| Thread | Status | Origin (earliest known) | Last touched (wave) | Open questions | Tag |
|---|---|---|---|---|---|
| Private credit liquidity | Active, gates confirmed | This wave sequence | 6 | Phase 2→3 transition markers | `[SOURCED]` |
| Software/AI disruption | Active, concentrated stress | This wave sequence | 6 | Mark-to-market lag still unresolved | `[SOURCED]` |
| CRE / CMBS maturity wall | Verified, under-discussed since Wave 3 | This wave sequence | 8 (this session) | Bank-specific exposure beyond Blackstone/Starwood | `[SOURCED]`, needs refresh |
| Treasury market dysfunction | Weakest thread — one claim unverified, one contradicted by newer data | This wave sequence | 8 (this session) | Needs a fresh bid-to-cover read before reuse | `[UNVERIFIED]` |
| Insurance/annuity exposure | Active (Wave 7 run) | This wave sequence | 7 | Real allocation range is 10-31%; avoid collapsing to a point | `[SOURCED]` |
| Geopolitical (Hormuz) | **Recovered, contested** | Pre-dates this wave sequence — original report, months prior | 6 (rediscovered) | Cited figures don't match primary sources; needs a clean re-pull | `[UNVERIFIED]` |
| Agriculture (winter wheat/HRW) | **Recovered, partially confirmed** | Pre-dates this wave sequence — same origin as Hormuz thread | 6 (rediscovered) | Two of three cited figures imprecise vs. USDA data | `[SOURCED]` partial |

**The "Origin" column exists because of a specific failure that just happened:** Hormuz and Agriculture weren't new additions to Wave 6 — they were threads from your original analysis, months older than anything else being tracked, that had dropped out entirely somewhere between then and Wave 1 of this sequence. A "last touched: Wave N" column can't distinguish "this is new" from "this is ancient and just got manually recovered" — both look identical without an origin date attached. A thread with no origin date is itself a flag: it means nobody knows how old it actually is, which means nobody can tell whether it's drifted further than the wave-count suggests.

A thread that hasn't been touched in several waves isn't necessarily resolved — it's just gone quiet. The registry makes that visible instead of letting it disappear silently. Before any "comprehensive guide" gets built again, check it against this table first: anything marked stale needs a fresh primary-source check, not a confident paragraph stitched in from memory of an earlier wave — and anything recovered from outside the current wave sequence needs that check more urgently, not less, since it's had the most opportunity to drift unnoticed.

---

## Tagging System

Every factual claim in a wave's output gets exactly **one** tag before it's allowed to move forward:

| Tag | Meaning | Forward rule |
|---|---|---|
| `[SOURCED]` | Traces to one named, checkable primary source (filing, transcript, named dataset/report) | Carries forward with the citation attached, not just the number |
| `[CARRIED-FORWARD]` | Repeats a prior wave's `[SOURCED]` claim without re-verifying this wave | Must show wave-of-origin; loses `[SOURCED]` status if uncomfirmed across more than 2 waves |
| `[ENSEMBLE-DEFINED]` | A threshold, label, or framework the ensemble itself created (e.g. "sentinel," "trigger level," confidence bands) | Must render visually distinct from sourced data — never inside the same table style as verified facts |
| `[UNVERIFIED]` | No source check attempted yet | Cannot be stated as fact; must read as "candidate to check," not as a finding |

**A document that mixes these tags into one undifferentiated table is itself a gate failure** — independent of whether the individual numbers turn out to be right. Uniform formatting confidence across sourced and unsourced claims is the root mechanism behind most of the errors this gate is meant to catch.

---

## Per-Claim Checklist

Run this against every row of every data table before it passes the gate:

- [ ] **Source named?** Not "Wave 5 output" — an actual filing, transcript, dataset, or named report.
- [ ] **Source checkable?** Could a human click through to it or search for it directly?
- [ ] **Range-collapse check?** If multiple values exist across sources, is the range shown, or has it been silently averaged/collapsed into one number?
- [ ] **Scope locked?** Timeframe, institution, asset class, and metric definition all match the source exactly — none silently widened, narrowed, or swapped.
- [ ] **Internally consistent?** If this claim pairs with a threshold or trigger elsewhere in the document, does the stated status actually satisfy that threshold?
- [ ] **Re-verified this wave, or just carried forward?** If carried forward, is it tagged as such rather than presented as freshly confirmed?

**Any unchecked box = the claim does not pass through to the next wave as currently stated.** It gets fixed, gets a citation attached, or gets demoted to `[UNVERIFIED]`.

---

## Worked Examples (from live testing)

| Claim | Correct tag | What the gate catches |
|---|---|---|
| BCRED "12% redemption, $70B AUM" | `[CARRIED-FORWARD]` — and wrong | Scope/value check fails: SEC filing + reporting show 10%, $79B. Gate catches the drift before the next wave inherits it. |
| Insurer "23.4% private credit allocation" | `[UNVERIFIED]` | Single-source check fails: real reported figures range 10%–31% depending on methodology. A single-point number with no source attached should never have passed. |
| "Citi designated as Treasury stress sentinel" | `[ENSEMBLE-DEFINED]` | Framework-leakage check fails: no external source designates this. Should render as "our monitoring framework," never as a market fact. |
| BCRED sentinel: threshold ">15%," status "TRIGGERED" at a 10–12% reading | — | Internal-consistency check fails outright: the document contradicts its own stated rule. |
| "$76.6B CMBS maturities, 2026–2027" | `[SOURCED]` but scope wrong | Scope-lock check fails: the source figure is 2026-only hard maturities; label was silently widened to two years. |

---

## Gate Failure Log

Keep a running log across waves. The *pattern* of failures matters more than any single catch — if one failure mode keeps recurring, that tells you which stage of the pipeline needs structural fixing, not just a one-off correction.

| Wave | Claim | Failure mode | Caught by | Fix applied |
|---|---|---|---|---|
| 5→6 | BCRED redemption rate/AUM | Source decay | Manual re-check | Corrected to 10% / $79B |
| 6 | Insurer 23.4% allocation | Invented precision | Manual re-check | Demoted to range (10–31%) |
| 6 | Citi "Treasury sentinel" | Framework leakage | Manual re-check | Tagged ensemble-internal, not market fact |
| 6 | BCRED trigger (">15%") vs. status ("TRIGGERED") | Internal inconsistency | Manual re-check | Flagged contradiction |
| 6 | $76.6B CMBS maturities labeled "2026-2027" | Scope creep | Manual re-check | Corrected to 2026-only |

*(Add a row every time the gate catches something. After a few waves, this table tells you more about the pipeline than any individual wave's findings do.)*

---

## One-Page Quick Reference

Before any wave's table feeds the next wave, ask of the table **as a whole**:

1. Could I click through to a primary source for every number in this table? *(No → gate fails)*
2. Is anything in here a range that's been flattened to a point? *(Yes → gate fails)*
3. Is anything in here the ensemble's own invented framework, dressed as market fact? *(Yes → tag it, don't pass it as fact)*
4. Does every threshold/status pair actually agree with each other? *(No → gate fails)*
5. Has anything actually been re-verified this wave, or is it all inherited from the last one? *(All inherited → demote confidence label, don't leave it at "High")*

If a wave's output can't clear all five, it goes back for sourcing — not forward into the next wave's table.
