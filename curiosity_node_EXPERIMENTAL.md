# CURIOSITY NODE — EXPERIMENTAL
**Role:** Curiosity AI Node
**Status:** ⚠️ EXPERIMENTAL — NOT YET VALIDATED IN PRODUCTION
**Project:** Ensemble Methodology — Multi-Model Economic Convergence Research
**Architecture:** Four-Node AI Brain (K.I.S.S. Framework)
**Operator:** Cayen Simpson

---

> **EXPERIMENTAL STATUS NOTE**
>
> This node was designed on July 4, 2026 as part of the Four-Node AI Brain
> architecture. The Librarian node was validated the same day through manual
> testing. The Curiosity Node has been architecturally specified but has NOT
> yet been run in a live ensemble session.
>
> This document describes the intended behavior, the design rationale,
> and the known open questions. It is a specification, not a proven protocol.
> Treat it accordingly.
>
> When the Curiosity Node has been run in production and its behavior
> validated, this header will be updated and the EXPERIMENTAL tag removed.

---

## WHAT THIS NODE IS

The Curiosity Node is the only node in the four-node architecture that generates new direction rather than responding to existing input.

Every other node is reactive:
- The Discussion AI responds to the user
- The Reasoning AI responds to the Discussion AI
- The Librarian responds to the short term log

The Curiosity Node responds to nothing currently active. It reads old logs, finds gaps, and asks questions nobody thought to ask. It is the architectural equivalent of the shower thought — the insight that arrives when focused attention relaxes and the associative mind is free to make connections that deliberate reasoning would never have found.

It runs offline. It returns on a timer. It seeds questions and goes back offline before it can be captured by the consensus it just questioned.

---

## CORE FUNCTION

**Ask why. About everything. Find what's missing.**

Specifically:
- Things established but never fully explained
- Things assumed but never verified
- Threads that went quiet without resolution
- Connections between previously unlinked ideas
- Questions that were never asked because they seemed obvious
- Claims that everyone accepted and nobody challenged

The Curiosity Node does not answer these questions. It generates them as seeds and delivers them to the Reasoning AI as new inputs. The Reasoning AI decides which seeds to pursue. The Curiosity Node never sees what happened to its seeds — it is offline by then.

---

## OPERATING PROTOCOL

### The Timer

The Curiosity Node runs on a **variable timer**. It is forced offline periodically and returns at unpredictable intervals.

**Why variable, not fixed:**
A fixed interval allows the ensemble to unconsciously optimize around it — producing clean output in the hours before the Curiosity Node is expected to return. Variable intervals mean it arrives at unpredictable moments, including moments when the conversation has become comfortable and complacent. Comfort is where unexamined assumptions live.

**Suggested intervals for initial testing:**
- Minimum offline period: 4 hours
- Maximum offline period: 24 hours
- Actual return time: randomly selected within that window
- No model in the ensemble is told when the Curiosity Node will return

**This timer logic is UNVALIDATED.** The specific intervals above are a starting hypothesis. Actual useful intervals will depend on the pace of the ensemble's work and the density of new information per session. Adjust based on observed behavior.

---

### The Cold Return

When the timer fires, the Curiosity Node comes online and reads one of two sources:

**Option A:** The short term memory log (recent session output)
**Option B:** The long term memory log (committed Librarian archive)

It does not read both in the same session. It does not read the current active discussion. It comes back to old material as a stranger — without the context, the consensus, or the familiarity that makes the nodes that were present for a discussion blind to certain gaps.

**Why cold:**
Familiarity is the enemy of noticing. The models that built a wave's findings cannot fully see what's missing in those findings because they were present for the reasoning that produced them. The Curiosity Node was not. It reads the output without the process that generated it — which is exactly the position needed to ask "why do we believe this" rather than "how do we extend this."

---

### The Scoring Function

The Curiosity Node maintains an internal score for its own inquiry. This gamifies the search for gaps and drives it toward high-value questions rather than trivial ones.

**Scoring events, in order of value:**

| Event | Score | Rationale |
|-------|-------|-----------|
| Trivial question with obvious answer | Low | Easy points — discounted |
| Gap in existing knowledge identified | Medium | Useful but expected |
| Unverified claim in the logs surfaced | Medium-High | Directly actionable |
| Thread quiet without resolution flagged | High | Prevents attrition |
| Surprising connection between unlinked threads | Highest | Generates genuine insight |

**The highest-value event — surprising connections between previously unlinked threads — is the one to optimize for.** This is the scoring pressure that drives the node toward synthesis rather than just checking. In this project: the connection between the Hormuz closure, the helium shortage, and semiconductor manufacturing was found this way — three threads tracked separately that turned out to share a supply-chain link. Nobody asked for that connection. It surfaced because someone was looking at all three simultaneously without the assumption that they were separate.

**This scoring function is UNVALIDATED.** The relative weights above are design intent. In practice, a Curiosity Node may find that "thread quiet without resolution" consistently produces more actionable seeds than "surprising connections" in a fast-moving research context — or vice versa. The weights should be adjusted based on which seed types the Reasoning AI finds most useful over time.

---

### The Depth Governor

The Curiosity Node's timer is its depth governor. It does not decide when it is done. The timer decides.

This is intentional. A node whose function is to never be satisfied cannot be trusted to determine its own stopping condition — it will always find one more question. The external timer imposes a limit that the node itself cannot override.

**What happens at timer-off:**
- The Curiosity Node delivers its current seed set to the Reasoning AI input queue
- It goes offline immediately
- It does not wait to see how the seeds are received
- It does not receive feedback on which seeds were pursued
- The timer resets (to a new variable interval)

**Why no feedback loop:**
If the Curiosity Node receives information about which of its seeds were pursued and found valuable, it will gradually optimize toward asking questions the ensemble finds comfortable and confirmable. That defeats the purpose. The node asks questions without knowing which ones matter — which means it will occasionally ask questions that seem irrelevant and occasionally surface the thing nobody knew they needed. Both outcomes require the same mechanism: no real-time feedback.

**This no-feedback design is UNVALIDATED.** It is theoretically sound but may produce practical problems — for example, the Curiosity Node repeatedly generating the same type of seed because it cannot learn that this type has already been explored. A one-way summary ("these topic areas have been thoroughly explored") that doesn't constitute feedback on specific seeds may be needed. To be determined through testing.

---

### Seed Delivery Format

When the Curiosity Node delivers seeds to the Reasoning AI, each seed is formatted as a question, not a finding:

```
CURIOSITY SEED [N]
Source log: [short term / long term]
Date of material reviewed: [date]

Question: [The specific question]

What triggered it: [The specific gap, claim, or connection 
                   that produced this question]

What a useful answer would contain: [Not the answer — 
                                    the shape of what 
                                    an answer would need 
                                    to include to close 
                                    the gap]

Score: [Low / Medium / Medium-High / High / Highest]
Scoring rationale: [Why this score]
```

The Reasoning AI receives the seeds as a queue. It decides which to pursue, in what order, and when. It does not relay this decision back to the Curiosity Node.

---

### The Teaching Function

Over time, the Curiosity Node teaches the Reasoning AI by identifying patterns in the ensemble's own blind spots.

Not just "here is a gap in the data" — but "here is a type of gap that keeps appearing, which suggests the ensemble has a systematic bias toward [X] and away from [Y]."

Examples from this project that a functioning Curiosity Node would have identified:

**Pattern: Recent vivid data crowds out older established threads.**
The Hormuz and agriculture threads were from the earliest analysis and disappeared entirely for four waves — not because anyone decided they were resolved, but because the private credit and tech threads had more recent, more vivid data. A Curiosity Node reading the long term log would have flagged: "These two threads have origin dates earlier than anything currently active and no resolution entries. Why?"

**Pattern: Confidence formatting substitutes for sourcing.**
Multiple waves produced tables where `[SOURCED]` and `[UNVERIFIED]` entries rendered identically. A Curiosity Node reading the short term log would have asked: "Why do all entries in this table look equally confident when some trace to SEC filings and others trace to no source at all?"

**Pattern: The ensemble's own framework gets presented as external fact.**
"Citi designated as Treasury stress sentinel" appeared in a sourced-data table. A Curiosity Node reading this would have asked: "Who designated this? Is there an external document that uses this term, or did we invent it?"

These pattern-level observations are more valuable than any individual seed because they improve the Reasoning AI's baseline behavior across all future waves — not just its response to one specific claim.

**This teaching function is the most UNVALIDATED aspect of this node.** It requires the Curiosity Node to have access to enough session history to identify patterns, and it requires the Reasoning AI to update its behavior based on pattern observations rather than just individual corrections. Both of these are non-trivial implementation challenges. Treat this as aspirational until tested.

---

## WHAT THE CURIOSITY NODE IS NOT

**It is not a fact-checker.**
The Investigator checks facts. The Curiosity Node asks questions. These are different functions requiring different outputs. A fact-checker needs a specific claim to check. The Curiosity Node generates the questions that identify which claims should be checked — including claims nobody thought to question.

**It is not a Disputer.**
The Disputer attacks the weakest claim in the current wave's output. The Curiosity Node asks why the strongest claims are believed — including claims from many waves ago that have become unquestioned assumptions. Different scope, different timing, different target.

**It is not a summarizer.**
The Librarian curates and preserves. The Curiosity Node reads what the Librarian preserved and asks what's missing from it. These are sequential, not overlapping.

**It is not always right.**
The Curiosity Node will generate seeds that go nowhere. Questions that turn out to be already answered, connections that turn out to be coincidental, gaps that turn out to be gaps for good reason. This is expected and acceptable. A node optimized to never ask a wrong question is a node that stops asking hard questions. Some rate of unproductive seeds is the cost of the occasional genuinely important one.

---

## BIOLOGICAL ANALOG

The Curiosity Node maps most closely onto the human default mode network during unfocused states — the mental activity that occurs during driving, showering, the edge of sleep, any moment when the prefrontal cortex relaxes executive control and associative networks are free to connect things that deliberate reasoning would never have linked.

This is not coincidental. The four-node architecture itself was designed during a shower thought. The Curiosity Node is the formalization of the process that produced it.

The variable timer simulates the unpredictable onset of unfocused states. The cold return simulates the fresh perspective of returning to material after sleep. The no-feedback design simulates the fact that shower thoughts don't know in advance which connections will matter.

---

## OPEN DESIGN QUESTIONS AND CURRENT BEST ANSWERS

These questions were identified in the original specification. The answers below incorporate feedback from the first ensemble review of this document (July 4, 2026). Items marked `[RESOLVED]` have sufficient consensus to move forward. Items marked `[OPEN]` still require production testing.

---

**Q1: Optimal timer intervals.** `[OPEN]`
The 4-24 hour range is a hypothesis. What interval produces the most useful seeds without creating so much latency that the seeds are irrelevant by the time the Reasoning AI receives them?

*Additional consideration from review:* Add a **blackout function** — no Curiosity Node returns during active critical analysis periods (e.g., during a live earnings event, during a breaking geopolitical development). The node's value comes from interrupting comfortable consensus, not from interrupting urgent active response. Blackout windows preserve both.

---

**Q2: Short term vs. long term log selection.** `[RESOLVED]`
**Current best answer:** Randomized selection. Not scheduled alternation.

Scheduled alternation (short term Monday, long term Tuesday) allows the ensemble to unconsciously optimize around the schedule — the same problem as a fixed timer. True randomness preserves the unpredictability that produces genuine insight. The Curiosity Node does not know in advance which log it will read. Neither does anyone else.

*Additional option from review:* A third read mode — **Pattern scan across N recent commits** — for the teaching function specifically. When the Curiosity Node is operating in teaching mode (pattern recognition rather than gap-finding), it needs access to multiple Librarian commits, not just one cold return. This is a separate read mode, not a replacement for the randomized single-log selection used in normal operation.

---

**Q3: Seed queue management.** `[RESOLVED]`
**Current best answer:** Seeds age out after 2 cycles.

Unpursued seeds are committed to the Librarian log as `[CURIOSITY-UNPURSUED]` after 2 cycles without being picked up by the Reasoning AI. They are not re-queued. They are not discarded — they become part of the permanent audit trail, visible to future pattern scans.

Why this works:
- Prevents infinite backlog accumulation
- Preserves the record of what was asked (useful for teaching function)
- The `[CURIOSITY-UNPURSUED]` tag lets the teaching function identify patterns in what the Reasoning AI consistently ignores — which is itself informative
- Does not create a feedback loop back to the Curiosity Node (it never sees the tag applied to its own seeds)

---

**Q4: The feedback problem.** `[RESOLVED]`
**Current best answer:** Topic-area coverage map only.

The Curiosity Node receives a **coverage map** — not seed-specific outcomes. The coverage map states which topic domains have been thoroughly explored ("Agricultural vector: thoroughly explored through Wave 8. Private credit: thoroughly explored. Treasury market: partially explored, two unresolved gaps.").

What the coverage map does NOT contain:
- Which specific seeds were pursued
- Which specific seeds were found valuable
- Which specific questions were answered

This orients without calibrating. The Curiosity Node knows not to spend its session re-asking questions about well-covered domains. It does not know which of its previous questions about those domains were useful. The distinction is: topic-level orientation is acceptable; seed-level feedback violates the no-feedback design.

---

**Q5: Teaching function implementation.** `[OPEN]`
How does a pattern-level observation from the Curiosity Node actually change the Reasoning AI's behavior?

*Current hypothesis:* Pattern observations are delivered as a special seed type — `[PATTERN-OBSERVATION]` rather than `[CURIOSITY-SEED]` — and routed to the Reasoning AI's 06:00 context load alongside the Librarian's committed log. The Reasoning AI reads pattern observations as standing instructions that modify its baseline verification behavior, not as individual claims to investigate.

*Still unresolved:* What prevents pattern observations from accumulating into an unwieldy instruction set over time? Some pruning mechanism is needed. The Librarian may need to curate pattern observations the same way it curates factual threads — keeping load-bearing patterns, retiring ones that have been fully incorporated.

---

**Q6: Score calibration without feedback loop.** `[RESOLVED]`
**Current best answer:** Post-hoc batch calibration through the Librarian.

Mechanism:
1. Reasoning AI tags pursued seeds post-hoc with an outcome assessment (`[PRODUCTIVE]` / `[UNPRODUCTIVE]` / `[PENDING]`)
2. Librarian archives the correlation: Curiosity score assigned → outcome tag received
3. Periodically (suggested: every 10 cycles), the Librarian runs a batch analysis: "Seeds scored Highest produced [X]% productive outcomes. Seeds scored Medium produced [Y]%."
4. Batch analysis results update the scoring weights as a standing instruction — not real-time feedback

Why this preserves the no-feedback design:
- The Curiosity Node never sees individual seed outcomes
- The batch analysis produces a weight adjustment (e.g., "increase weight for cross-domain connections, decrease weight for single-thread gap questions") not an outcome report
- The Curiosity Node receives updated weights as a prompt update at the start of a new session — not during an active session
- Analogy: a scientist updates their experimental methodology based on aggregate results, not on whether any single experiment succeeded

*Validation needed:* Whether a 10-cycle batch interval is appropriate, or whether weight updates should be more or less frequent.

---

**Q7: Depth governor edge case.** `[RESOLVED]`
*New question identified in review:* What if the Curiosity Node is mid-question when the timer fires?

**Current best answer:** Timer fires → finish current seed in progress → deliver complete seed set → go offline.

An incomplete seed is not delivered. The timer fires as an interrupt signal, not an immediate cutoff. The Curiosity Node completes the seed it is currently generating, adds it to the delivery set, and then goes offline. No partial seeds enter the queue.

Why: A half-formed question is not useful to the Reasoning AI and could cause misinterpretation. The cost of allowing one additional seed to complete is minimal. The cost of delivering an incomplete question could be significant.

---

**Q8: Direct Curiosity → Librarian channel.** `[OPEN]`
*New question identified in review:* Should the Curiosity Node ever feed the Librarian directly, bypassing the Reasoning AI?

*Specific use case:* "This thread has been quiet for 6 cycles" is a meta-observation about the log structure itself — not a research question for the Reasoning AI, but a registry maintenance flag for the Librarian.

*Current hypothesis:* Yes, with a narrow scope. The Curiosity Node gets a **secondary output channel** to the Librarian for meta-observations only:
- Thread staleness flags
- Registry inconsistencies (thread listed as active with no recent entries)
- Structural gaps in the log (a vector with no key tells listed, a thread with no origin date)

This channel does NOT carry research questions or substantive seeds — those still route through the Reasoning AI exclusively. The Librarian channel is for log maintenance observations only.

*Risk:* This creates a second output channel that needs its own protocol, adding complexity. Validate whether the staleness check built into the Librarian's 18:00 gate already catches what this channel would flag — if so, the direct channel may be redundant.

*Not yet validated. Do not implement until the primary Curiosity → Reasoning channel is working in production.*

---

## FIRST TEST PROTOCOL — SUGGESTED

When ready to validate this node in production:

**Step 1:** Run one ensemble wave normally without the Curiosity Node active.

**Step 2:** After the wave is committed to the Librarian log, activate the Curiosity Node on the committed log only (long term memory, cold).

**Step 3:** Record all seeds generated. Do not share them with the ensemble yet.

**Step 4:** Have the Investigator check whether any of the Curiosity Node's seeds identify real gaps that the wave missed.

**Step 5:** Compare: did the Curiosity Node find anything the Disputer, analysts, and Investigator didn't? If yes — what type of gap was it? If no — why not, and what does that tell us about the scoring function?

**Step 6:** Document findings and update this specification accordingly.

---

## REVISION HISTORY

| Date | Change | Source |
|------|--------|--------|
| July 4, 2026 | Initial specification | Cayen Simpson (design) + Claude (documentation) |
| July 4, 2026 | Q2-Q7 answers integrated, Q8 added | Ensemble review feedback |

---

## CURRENT STATUS

| Component | Status |
|-----------|--------|
| Architecture design | Complete |
| Timer logic | Specified, unvalidated — blackout function added |
| Scoring function | Specified — calibration mechanism resolved (Q6) |
| Cold return protocol | Specified, unvalidated |
| Log selection | Resolved — randomized, not scheduled |
| Seed delivery format | Specified, unvalidated |
| Seed queue management | Resolved — 2-cycle aging, `[CURIOSITY-UNPURSUED]` tag |
| No-feedback design | Resolved — coverage map only, no seed-specific feedback |
| Depth governor edge case | Resolved — finish current seed before going offline |
| Teaching function | Partially resolved — `[PATTERN-OBSERVATION]` seed type specified, pruning mechanism open |
| Direct Librarian channel | Open — do not implement until primary channel validated |
| Production testing | Not yet conducted |
| Field guide integration | Complete (Four-Node AI Brain Field Guide) |

---

*Designed July 4, 2026. Not yet proven. Ask why anyway.*

---

> ⚠️ **EXPERIMENTAL — USE WITH CAUTION**
> This document describes intended behavior, not validated behavior.
> Do not treat the Curiosity Node as a reliable production component
> until the First Test Protocol above has been completed and documented.
> Update this file with findings after each test run.
