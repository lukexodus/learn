## Failure Mode and Effects Analysis

### Overview

Failure Mode and Effects Analysis (FMEA) is an inductive, bottom-up reliability technique that systematically identifies every plausible way a system, process, or design element could fail (its failure modes), the effects of each failure, and the underlying causes, before any actual failure has occurred. Where Fault Tree Analysis works deductively backward from a known top event, FMEA works forward: starting from individual components or process steps and asking "how could this fail, and what would happen if it did?" This makes FMEA fundamentally a *proactive* risk-assessment tool, in contrast to the largely *reactive* RCA tools covered elsewhere in this series, which are applied after an incident has already occurred. FMEA is included in this chapter as a complementary methodology because its outputs — prioritized failure modes and their root causes — directly feed and strengthen reactive RCA investigations when a prioritized failure mode subsequently manifests as a real incident.

### Origin and Purpose

**Key Points**

- FMEA traces to U.S. military procedure MIL-P-1629 (1949) and was substantially developed and popularized through aerospace (NASA, Apollo program) and automotive (Ford, following the 1960s–70s quality movement) applications
- Its defining characteristic relative to the reactive tools in this series (5 Whys, Fishbone, FTA, ECFC, CRT) is timing: FMEA is performed *before* failures occur, as a design or process risk assessment, while the other tools are applied *after* an incident to determine what already happened
- FMEA's core output is a prioritized list of failure modes ranked by risk, which serves two purposes relevant to RCA: (1) directing preventive action before an incident occurs, and (2) providing a pre-existing, evidence-based reference of anticipated failure modes and their causes that can accelerate a reactive RCA investigation when one of those anticipated modes actually materializes
- Two common variants exist: **Design FMEA (DFMEA)**, assessing failure modes in a product or system design, and **Process FMEA (PFMEA)**, assessing failure modes in a manufacturing or operational process

### Core Terminology

| Term | Definition |
| --- | --- |
| Failure mode | The specific manner in which a component, step, or function could fail to perform as intended |
| Effect | The consequence of that failure mode on the system, process, downstream customer, or end user |
| Cause | The underlying mechanism that would produce the failure mode |
| Severity (S) | A rating of how serious the effect would be if the failure occurred |
| Occurrence (O) | A rating of how likely the failure mode is to occur |
| Detection (D) | A rating of how likely existing controls are to detect the failure before it causes the effect |
| Risk Priority Number (RPN) | $RPN = S \times O \times D$, used to rank failure modes by overall risk for prioritization |

### The Standard 1–10 Rating Scales

Each of Severity, Occurrence, and Detection is typically rated on a 1–10 scale, though specific scale definitions vary by industry and organizational standard (e.g., AIAG-VDA in automotive uses somewhat different anchor definitions than general industrial practice). A representative generic scale:

| Rating | Severity | Occurrence | Detection |
| --- | --- | --- | --- |
| 1 | No discernible effect | Failure extremely unlikely | Almost certainly detected before effect occurs |
| 5–6 | Moderate effect, some customer dissatisfaction or degraded performance | Occasional failures | Moderate chance of detection |
| 9–10 | Hazardous effect, safety or regulatory noncompliance without warning | Failure almost inevitable | Failure will not be detected before effect occurs |

[Inference] Because rating scales are organization- or standard-specific, teams using FMEA should apply a single consistent scale definition document across all analyses within their organization, since RPN values are only meaningfully comparable when derived from the same scale definitions.

### Step-by-Step FMEA Construction Process

**Step 1 — Define scope: system, subsystem, component, or process step.** Establish clear boundaries for what is being analyzed — an overly broad scope produces a shallow analysis, while an overly narrow one may miss interactions with adjacent components or steps.

**Step 2 — List every function the item under analysis is intended to perform.** Each function becomes the basis for identifying how it could fail to be performed.

**Step 3 — For each function, brainstorm every plausible failure mode.** Ask: "In how many distinct ways could this function fail to be delivered?" (e.g., a valve's function "seal flow" might fail as: fails to close, fails to open, leaks while closed, opens partially).

**Step 4 — For each failure mode, identify the effect(s).** Consider effects at multiple levels: local (immediate effect on the component itself), next-level (effect on the immediate subsystem), and end (effect on the overall system, process output, or end user).

**Step 5 — For each failure mode, identify the underlying cause(s).** This step is where FMEA construction connects directly to the reactive RCA tools covered elsewhere in this series — the causes identified here can themselves be explored using 5 Whys or Fishbone-style category brainstorming (Man/Machine/Material/Method/Measurement/Environment) to ensure they are evidence-grounded rather than assumed.

**Step 6 — Identify existing controls.** Document any current design controls (preventing the cause) or detection controls (detecting the failure mode or its effect before it reaches the end effect).

**Step 7 — Assign Severity, Occurrence, and Detection ratings, and calculate RPN.** Use the organization's standard rating scale consistently across all entries to preserve comparability.

**Step 8 — Prioritize by RPN (and by Severity alone for high-severity items regardless of RPN).** Failure modes with very high Severity ratings (particularly safety-related) often warrant action regardless of overall RPN, since a low Occurrence or Detection rating should not by itself excuse addressing a catastrophic potential effect. [Inference] Many current FMEA standards explicitly recommend Severity-based action thresholds independent of RPN for exactly this reason, though specific threshold policies vary by organization and industry.

**Step 9 — Define and assign recommended actions for high-priority failure modes.** Actions typically reduce Severity (rare, usually requires design change), reduce Occurrence (improve the process/design to make the cause less likely), or improve Detection (add or improve a control to catch the failure mode earlier).

**Step 10 — Recalculate RPN after actions are implemented, to verify risk reduction.** This produces a documented before/after risk profile demonstrating the value of the corrective action.

### FMEA Worksheet Structure (Reference)

| Function | Failure Mode | Effect | Severity | Cause | Occurrence | Current Controls | Detection | RPN | Recommended Action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Seal flow (motor bearing lubrication) | Loss of lubrication seal integrity | Bearing contamination, eventual seizure | 7 | Seal degradation not addressed in install procedure | 6 | None (no vibration monitoring on this motor class) | 8 | 336 | Add vibration-monitoring alarm; update install procedure to specify seal replacement interval |

This example directly connects to the bearing failure scenario used throughout this series' worked examples — an FMEA performed proactively on this motor class, using exactly this reasoning, would have identified the seal/contamination failure mode and its procedural cause *before* the actual incident occurred, illustrating FMEA's preventive relationship to the reactive tools covered elsewhere in this chapter.

### FMEA Compared to Reactive RCA Tools

| Aspect | FMEA | 5 Whys / Fishbone / FTA / ECFC / CRT |
| --- | --- | --- |
| Timing | Proactive — before failure occurs | Reactive — after an incident has occurred |
| Direction | Inductive — component/step forward to effect | Deductive (mostly) — effect backward to cause |
| Starting point | A function or component | A specific, already-occurred undesired event |
| Output | Prioritized risk register (RPN-ranked failure modes) | A validated root cause (or causes) for one incident |
| Relationship to actual evidence | Anticipatory — based on engineering judgment, historical failure data, and design review | Grounded in evidence gathered from the specific incident (per the evidence-gathering discipline covered earlier in this series) |
| Typical trigger | Design review, new process introduction, periodic reliability review | An incident, near-miss, or defect has occurred |

### How FMEA and Reactive RCA Tools Reinforce Each Other

- **FMEA outputs inform reactive RCA scope.** When an incident occurs, checking whether it corresponds to a failure mode already identified in an existing FMEA can accelerate the evidence-gathering and hypothesis-generation phases of the reactive investigation, since candidate causes may already be documented.
- **Reactive RCA findings update FMEA.** When a 5 Whys or Fishbone investigation reveals a root cause not previously captured in the FMEA (as in the worked example above), the FMEA should be updated to add that failure mode, ensuring the next occurrence is anticipated rather than treated as a surprise. This closes the loop between proactive and reactive methodologies.
- **A failure mode with a low FMEA-predicted Occurrence rating that nonetheless produces a real incident** is itself diagnostically significant — it suggests either the Occurrence rating was miscalibrated (an assumption that should be revisited, per this series' fact/assumption discipline) or a new, previously unidentified cause is contributing to a known failure mode.

### Common Pitfalls

- **Treating RPN as a precise, objective risk score** — because S, O, and D are subjective ratings (even when scale-anchored), RPN is an ordinal prioritization aid, not a precise quantitative risk metric; two failure modes with similar RPN values are not necessarily equally risky, and RPN values should not be over-interpreted numerically
- **Underweighting Severity in favor of RPN alone** — a high-severity, low-occurrence failure mode can have a modest RPN that masks its importance; Severity-based override thresholds exist specifically to prevent catastrophic-but-rare failure modes from being deprioritized
- **Conducting FMEA without cross-functional input** — a design engineer alone will typically miss process-execution failure modes that a process engineer or operator would surface, and vice versa; effective FMEA construction is a cross-functional team activity
- **Treating FMEA as a one-time document rather than a living risk register** — failure to update the FMEA when new failure modes are discovered through actual incidents (via reactive RCA) allows the same gap to persist undetected for future design or process iterations
- **Skipping the recalculation step after implementing actions** — without recalculating RPN post-action, there is no documented verification that the recommended action actually reduced risk as intended

**Related Topics**

- Fault tree analysis fundamentals
- 5 Whys methodology and drill-down technique
- Fishbone or Ishikawa diagram construction
- The 6M and 4M categorization frameworks
- Distinguishing fact from assumption (evidentiary tagging discipline)
- Reliability engineering and failure rate data sources
- Corrective and preventive action (CAPA) systems