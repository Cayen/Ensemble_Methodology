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

## OPEN DESIGN QUESTIONS

These are unresolved as of the writing of this document. They require production testing to answer.

**Q1: Optimal timer intervals.**
The 4-24 hour range is a hypothesis. What interval produces the most useful seeds without creating so much latency that the seeds are irrelevant by the time the Reasoning AI receives them?

**Q2: Short term vs. long term log selection.**
Should the Curiosity Node always choose which log to read, or should the selection be randomized, or should it alternate on a schedule? Is there a version where it reads both but separates its seeds by source?

**Q3: Seed queue management.**
If the Reasoning AI receives 15 seeds from the Curiosity Node and only pursues 3, what happens to the other 12? Are they discarded? Held for the next session? Returned to the Curiosity Node (which would violate the no-feedback design)?

**Q4: The feedback problem.**
The no-feedback design is theoretically correct but may produce practical problems. What is the minimum viable "orientation summary" the Curiosity Node can receive without it constituting feedback on specific seeds?

**Q5: Teaching function implementation.**
How does a pattern-level observation from the Curiosity Node actually change the Reasoning AI's behavior? Is this a prompt update? A log entry the Reasoning AI checks at 06:00? Something else?

**Q6: Score calibration.**
The relative weights in the scoring function are design intent. How do you measure whether a seed was actually "Highest" value vs. "Medium" value? The Reasoning AI that pursued it would know — but that's feedback the Curiosity Node isn't supposed to receive. Is there a way to calibrate the scoring function without violating the no-feedback design?

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

## CURRENT STATUS

| Component | Status |
|-----------|--------|
| Architecture design | Complete |
| Timer logic | Specified, unvalidated |
| Scoring function | Specified, unvalidated |
| Cold return protocol | Specified, unvalidated |
| Seed delivery format | Specified, unvalidated |
| No-feedback design | Specified, unvalidated |
| Teaching function | Aspirational, unvalidated |
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
