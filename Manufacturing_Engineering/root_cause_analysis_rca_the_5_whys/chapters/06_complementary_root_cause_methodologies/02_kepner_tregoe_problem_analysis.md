## Kepner Tregoe Problem Analysis

### Overview

Kepner-Tregoe (KT) Problem Analysis is a structured, question-driven RCA methodology developed by Charles Kepner and Benjamin Tregoe, first published in their 1965 book *The Rational Manager*. Its defining characteristic relative to the visual mapping tools covered earlier in this series (Fishbone, FTA, ECFC, CRT) is that KT Problem Analysis is not primarily a diagramming technique — it is a disciplined, tabular questioning process built around a specific logical technique: precisely bounding what the problem **IS** versus what it plausibly **could be but IS NOT**, and using the *distinctions* between those two sets to test candidate causes systematically. It is widely used in technical support, engineering, and manufacturing environments where a structured, repeatable, team-transferable investigation process is valued as much as the specific tool used to build it.

### Origin and Purpose

**Key Points**

- KT Problem Analysis is one component of a broader Kepner-Tregoe framework that also includes Situation Appraisal (prioritizing and clarifying concerns) and Decision Analysis (choosing among alternatives) — Problem Analysis specifically is the component relevant to root cause identification
- Its core innovation is the **IS/IS NOT** distinction test: rather than asking only "what caused this," KT explicitly asks "what makes the affected cases different from the unaffected but comparable cases that were **not** affected" — turning the *absence* of a problem in comparable situations into positive diagnostic evidence
- KT is deliberately question-driven and tabular rather than visual, making it highly suited to environments requiring a standardized, auditable, step-by-step investigation record — historically strong adoption in technical support, aerospace, and manufacturing quality contexts
- The method treats cause identification as a process of *elimination through comparison*, rather than direct traversal (as in 5 Whys) or category brainstorming (as in Fishbone) — a structurally distinct approach from every other tool in this series

### The Four-Dimension Specification Framework

KT Problem Analysis organizes every fact about the problem along four standard dimensions, each split into IS and IS NOT columns:

| Dimension | IS (question) | IS NOT (question) |
| --- | --- | --- |
| **What** | What object/unit is affected? What specifically is the defect/deviation? | What comparable object/unit, that could reasonably have been affected, was not? |
| **Where** | Where (geographically, or on the object) is the problem observed? | Where, on a comparable object or location, is the problem not observed? |
| **When** | When was the problem first observed? When, in a cycle or pattern, does it appear? | When, in a comparable timeframe or cycle, has the problem not appeared? |
| **Extent** | How many units/instances are affected? What is the trend (size, rate) of the problem? | How many comparable units/instances are not affected? |

### Step-by-Step Construction Process

**Step 1 — Write a precise problem statement (the "deviation").** KT specifically frames the problem as a deviation from expected/normal performance — "what should be happening, that is not, or what is happening, that should not be."

**Step 2 — Populate the IS columns using verified facts only.** For each of the four dimensions (What, Where, When, Extent), record only evidence-based observations — per the fact/assumption discipline established earlier in this series, an IS entry without a traceable source should not be accepted as fact.

**Step 3 — Populate the IS NOT columns with comparably plausible alternatives that were NOT affected.** This is the step most distinct from other RCA tools and the most frequent source of construction error: the IS NOT entries must be *genuinely comparable* cases that could plausibly have exhibited the problem but did not — not simply "everything else in the world." A poorly chosen IS NOT comparison (one too dissimilar to the IS case) yields uninformative distinctions.

**Step 4 — Identify distinctions between each IS/IS NOT pair.** For each dimension, ask: "What is genuinely different between the affected case and the comparable unaffected case?" These distinctions are the raw diagnostic material KT uses to generate and test causes.

**Step 5 — Identify changes associated with each distinction.** For each distinction, ask: "What changed, at or around the time this distinction came into being?" Changes are a key causal signal in KT methodology — problems are frequently traced to something that changed, rather than to a condition that was always present.

**Step 6 — Generate possible causes from the distinctions and changes.** Each distinction/change pair becomes a candidate explanation for why the IS case exhibits the problem while the IS NOT case does not.

**Step 7 — Test each possible cause against every fact in the IS/IS NOT table.** This is the core validation step: a genuine root cause must be able to explain **every** IS and IS NOT fact simultaneously — not just some of them. A candidate cause that explains the IS facts but fails to explain why the IS NOT cases were unaffected is rejected, even if it seems otherwise plausible.

**Step 8 — Verify the most probable cause with direct evidence.** Once a candidate cause passes the "explains all facts" test, it should still be confirmed through direct verification (physical inspection, targeted data pull, reproducing the condition) before being accepted as the root cause — passing the logical test narrows the field but does not substitute for evidentiary confirmation.

### Worked Example

**Problem statement:** Weld porosity defects have increased on Line 3.

| Dimension | IS | IS NOT |
| --- | --- | --- |
| **What** | Weld porosity defects, specifically on the vertical seam weld | Horizontal seam welds on the same units; other defect types (undercut, spatter) |
| **Where** | Station 4 on Line 3 | Station 4 on Lines 1 and 2 (identical equipment model); Stations 3 and 5 on Line 3 |
| **When** | Began March 3rd; present on both shifts since then | Not present before March 3rd; not present at Station 4 on Lines 1/2 during the same period |
| **Extent** | Approximately 15% of vertical seam welds at this station | Horizontal seams at the same station: 0% defect rate; Station 4 on Lines 1/2: 0% defect rate |

**Distinctions identified:** Line 3 Station 4 uses a shielding gas supply from a different regulator than Lines 1/2 (Where distinction); a regulator was serviced on Line 3 on March 2nd (When distinction/change).

**Candidate cause generated:** The March 2nd regulator service on Line 3's shielding gas supply introduced a flow rate deviation affecting weld gas coverage.

**Testing against all facts:** This candidate cause explains why the defect appears only on Line 3 (Where — different regulator), only after March 3rd (When — service occurred March 2nd), only on the vertical seam (What — if the vertical weld path has less gas coverage margin than horizontal, consistent with a marginal flow reduction), and at the observed 15% rate (Extent — consistent with an intermittent flow issue rather than a complete failure). The cause is accepted pending direct verification (checking the regulator's actual flow setting against specification).

Note how this differs structurally from a Fishbone or linear 5 Whys approach to the same problem: rather than brainstorming candidate cause categories or drilling down a single assumed thread, the KT method derived the candidate cause directly from a comparison between affected and unaffected — but otherwise comparable — cases, and validated it against the complete fact set before accepting it.

### KT Problem Analysis Compared to Other RCA Tools

| Aspect | 5 Whys | Fishbone/Ishikawa | Fault Tree Analysis | Kepner-Tregoe |
| --- | --- | --- | --- | --- |
| Core mechanism | Sequential causal drilling | Categorized brainstorming | Formal AND/OR logic decomposition | Comparative distinction analysis (IS/IS NOT) |
| Uses "unaffected" cases as evidence | No | No | No | Yes — central to the method |
| Format | Linear text/list | Visual diagram | Visual logic tree | Structured tabular worksheet |
| Best suited for | Simple, single-threaded, one-cause problems | Broad divergent survey | Multi-cause, safety-critical, or probabilistic analysis | Problems with a clear, comparable "unaffected" population (intermittent, localized, or recently-changed problems) |
| Requires comparable unaffected cases to exist | No | No | No | Yes — a significant precondition for effective use |

### When Kepner-Tregoe Is Particularly Effective

KT Problem Analysis performs best in situations where:

- A **comparable unaffected population** genuinely exists (other lines, other units, other time periods, other locations) that can serve as a meaningful IS NOT baseline
- The problem is **intermittent or localized** rather than universal — if 100% of all possible cases are affected with no unaffected comparison available, the IS NOT columns cannot be meaningfully populated, and the method's core mechanism is unavailable
- The investigation benefits from a **standardized, transferable worksheet format** — particularly valuable in technical support or manufacturing environments where investigations are frequently handed between team members or shifts and need to be resumable without loss of context
- A recent **change** is suspected but not yet identified — the method's explicit change-detection step (Step 5) is particularly effective at surfacing causes tied to a specific change event rather than a longstanding condition

### Common Pitfalls

- **Choosing IS NOT comparisons that are not genuinely comparable** — selecting an IS NOT case too dissimilar from the IS case (e.g., comparing a defect on a manufacturing line to an entirely different, unrelated product) produces distinctions that are trivial or irrelevant, undermining the method's diagnostic value
- **Populating IS/IS NOT columns with assumptions rather than verified facts** — as with every RCA tool in this series, the KT worksheet's value depends entirely on the fact/assumption rigor applied when populating it; an IS NOT entry asserted without verification ("Line 1 probably isn't affected") can produce a false distinction
- **Accepting a candidate cause that explains most, but not all, facts** — the defining discipline of KT is testing candidate causes against the *complete* fact set; a cause that explains the IS facts but cannot account for why comparable IS NOT cases were unaffected should be rejected or revised, not accepted with an unexplained exception
- **Applying KT to universally-present problems with no unaffected comparison available** — the method's core mechanism depends on a meaningful IS NOT population; forcing the framework onto a problem where everything is uniformly affected produces empty or meaningless IS NOT columns
- **Skipping the direct verification step after logical testing** — passing the "explains all facts" test narrows the field of candidate causes but is not itself proof; treating logical consistency as sufficient without direct confirming evidence risks accepting a plausible-but-wrong cause

**Related Topics**

- 5 Whys methodology and drill-down technique
- Fishbone or Ishikawa diagram construction
- Distinguishing fact from assumption (evidentiary tagging discipline)
- Cross referencing multiple evidence sources
- Failure mode and effects analysis
- Change analysis and change-point detection in incident investigation