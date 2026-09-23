## Intelligence-Style Assessment Writing


---

### The Epistemological Contract

Intelligence writing operates under a strict epistemological contract: the reader must always know _what you know_, _how you know it_, and _how confident you are_. Violation of this contract — presenting inference as fact, omitting source quality, or hedging inconsistently — degrades the product and can cause catastrophic downstream decisions.

This is not academic writing. It is not journalism. It is not persuasive writing. It is a decision-support instrument. Every stylistic choice must serve that function.

---

### Bottom-Line-Up-Front (BLUF)

#### Principle

The BLUF is the single most important structural discipline in intelligence writing. The assessment's main judgment appears in the first sentence or first paragraph — before evidence, before context, before caveats. The reader must be able to act on the document having read only the first paragraph.

This inverts the structure of most academic and journalistic writing, which builds toward a conclusion. Intelligence writing starts with the conclusion and then defends it.

#### Structure of a BLUF

A well-formed BLUF contains three components:

1. **The judgment** — what you assess to be true or most likely
2. **The confidence level** — how strongly you hold that judgment
3. **The driver** — the primary reason or evidence underlying it

**Example:**

> _We assess with moderate confidence that Actor X is preparing for an offensive operation within the next 30–60 days, based on observed logistics movements and a pattern of pre-operational deception consistent with previous cycles._

The reader now knows: what is happening, how sure you are, and why you think so. Everything that follows is elaboration and support.

#### What the BLUF Is Not

- It is not a summary of reporting. Summaries describe what happened. BLUFs make judgments.
- It is not a hedge-first statement ("There are indications that possibly…"). Hedging belongs to confidence language, not sentence structure.
- It is not a question or a topic sentence ("This report examines whether…").

---

### Sourcing

#### Source Attribution Tiers

Intelligence assessments do not cite sources the way academic papers do. Instead, they indicate _source quality and reliability_ through standardized descriptors. Declassified and open-source frameworks use variations of the following:

|Descriptor|Meaning|
|---|---|
|_Reliable source_|Source has been accurate in prior reporting|
|_Usually reliable source_|Generally accurate; occasional gaps|
|_Unconfirmed reporting_|Single-source or unvetted; treat with caution|
|_Multiple independent sources_|Corroborated; higher evidentiary weight|
|_Open source_|Publicly available; no classified access implied|

In open-source analytic writing (which this syllabus uses exclusively), you name sources or characterize them:

- _According to [outlet/document/official record]_
- _Based on [observable indicator / public statement / documented pattern]_
- _Corroborated by [second source]_

#### Source Triangulation

A single source produces a _lead_, not a _finding_. Intelligence assessments require triangulation: at minimum two independent sources pointing to the same conclusion before it can be stated as assessed fact rather than single-source reporting.

When triangulation is unavailable, this must be stated explicitly:

> _This assessment rests on single-source reporting and should be treated accordingly. Confidence would increase with corroboration._

#### Source Quality Degraders

These must be flagged when present:

- **Access uncertainty** — does the source actually have visibility into what they claim?
- **Motivation bias** — does the source benefit from you believing their report?
- **Recency** — is the information current or potentially stale?
- **Chain of transmission** — was this reported firsthand or passed through intermediaries?

Failure to flag degraders is an analytic failure, not a stylistic one.

---

### Analytic Confidence and Hedging Language

#### The Function of Hedging

Hedging in intelligence writing is not weakness. It is precision. Unhedged language implies certainty the analyst does not possess. Over-hedged language renders the product useless. The goal is _calibrated language_ — language that accurately maps to the analyst's actual confidence level.

#### Confidence Tiers

Declassified U.S. intelligence community standards (publicly available in documents such as ICD 203) use three tiers. Open-source analytic frameworks use analogues:

|Tier|Language|Meaning|
|---|---|---|
|High confidence|_We assess_, _The evidence indicates_, _It is likely that_|Strong sourcing, consistent indicators, low alternative explanations|
|Moderate confidence|_We assess with moderate confidence_, _The available evidence suggests_|Credible sourcing but incomplete; plausible alternatives exist|
|Low confidence|_We cannot rule out_, _Reporting suggests but is unconfirmed_, _It is possible that_|Thin sourcing, significant uncertainty, alternatives equally plausible|

#### Probability Language

Vague probability terms cause miscommunication. Readers interpret "likely" differently. Where possible, anchor probability language to numeric ranges, or define terms explicitly within the document.

Publicly available analytic tradecraft standards (e.g., NATO analytic standards, Sherman Kent's probability words) map roughly as follows:

|Term|Approximate probability|
|---|---|
|Almost certainly / near certainty|95%+|
|Highly likely / very probably|80–95%|
|Likely / probably|55–80%|
|Roughly even chance|45–55%|
|Unlikely / probably not|20–45%|
|Remote / almost certainly not|Under 10%|

[Inference] These ranges represent common analytic convention, not a universal enforced standard. Individual agencies and organizations vary. The value is internal consistency within a document or organization, not adherence to any single external table.

#### Common Hedging Failures

**Under-hedging:**

> _Actor X will attack within 30 days._

This implies certainty no analyst can possess about future events. Replace with:

> _We assess with moderate confidence that Actor X is likely to initiate offensive action within 30 days._

**Over-hedging:**

> _It is possible that Actor X may potentially be considering actions that could possibly be interpreted as preparation._

This communicates nothing. The analyst is protecting themselves from being wrong rather than providing decision support.

**Hedge stacking:** Placing multiple hedges in sequence ("possibly may suggest") doubles down on uncertainty without adding information. Use one hedge term, calibrated correctly.

**Inconsistent hedging:** If the BLUF says "likely" but the body says "almost certainly," the document has an internal contradiction. Confidence language must be consistent throughout.

---

### Document Structure

#### Standard Assessment Architecture

A complete intelligence assessment follows this skeleton:

```
[CLASSIFICATION / HANDLING] — for open-source: UNCLASSIFIED or label as [OPEN SOURCE]

SUBJECT: [One-line topic, actor, or event]
DATE:
PREPARED BY:

KEY JUDGMENT / BOTTOM LINE
[1–3 sentences. The assessment. Confidence level stated explicitly.]

BACKGROUND
[Minimum necessary context. Not a history lesson. Only what is required
to understand the judgment.]

EVIDENCE AND ANALYSIS
[Organized by sub-question or line of analysis. Each claim sourced.
Confidence noted where it varies from the overall judgment.]

ALTERNATIVE ANALYSES
[What else could explain the evidence? Why was this alternative
assessed as less likely? This section is mandatory in rigorous analytic
writing and is frequently omitted — that omission is an analytic failure.]

INDICATORS TO WATCH
[What would confirm or refute the judgment? What would cause a
reassessment? This section converts the assessment into an ongoing
analytic task.]

SOURCES / BASIS FOR ASSESSMENT
[List or characterize the evidence base. Note quality degraders.]
```

#### The Alternative Analysis Requirement

Alternative analysis is the discipline of steel-manning competing explanations. It forces the analyst to ask: _what if I am wrong, and what would have to be true for the alternative to be correct?_

This is not hedging. It is structural honesty. An assessment with no alternative analysis has not been stress-tested and should be treated accordingly.

The alternative section does not require equal treatment of all alternatives — only those that meet a minimum evidentiary threshold. A completely implausible alternative does not require formal rebuttal. A plausible one does, even if you ultimately assess it as less likely.

---

### Analytic Line Integrity

#### Distinguishing Fact, Inference, and Judgment

Every claim in an intelligence assessment belongs to one of three categories:

|Category|Definition|Example|
|---|---|---|
|**Fact**|Confirmed, observable, documented|_Actor X conducted a military exercise on [date], per official government announcement._|
|**Inference**|Logically derived from facts|_The scale of the exercise [Inference] suggests preparation for sustained operations rather than routine training._|
|**Judgment**|Analytic assessment integrating facts and inferences|_We assess with moderate confidence that Actor X is signaling intent to regional adversaries._|

Mixing these categories without labeling is the primary source of analytic error in amateur intelligence writing. A chain of inferences presented as facts produces a document that _sounds_ certain but rests on nothing confirmed.

#### The Single Inference Rule

Do not chain inferences without labeling each link. If Fact A leads to Inference B, and Inference B leads to Inference C, then C is at minimum two steps removed from confirmed reality. Each link degrades confidence. Each link must be labeled.

---

### Tone and Register

Intelligence assessments use:

- **Active voice** wherever possible — passive voice obscures agency and responsibility
- **Third person** — personal opinion framing ("I think") is replaced by institutional analytic voice ("We assess")
- **Present tense for judgments** — "Actor X is assessed to be" not "Actor X was assessed to be"
- **No intensifiers** — "very," "clearly," "obviously" imply certainty and signal weak analytic discipline
- **No loaded language** — avoid adjectives that editorialize rather than describe ("brutal," "reckless," "impressive") unless quoting a primary source
- **Short sentences for key judgments** — complexity belongs in the evidence section, not the BLUF

---

### Practical Calibration Exercise

To train calibrated hedging, practice the following with any claim you encounter:

1. State the claim in the most confident possible form.
2. List every reason you might be wrong.
3. List every source gap that remains.
4. Re-state the claim in language that accurately reflects steps 2 and 3.
5. Check: is the resulting sentence still useful to a decision-maker? If not, you have either over-hedged or need more evidence before writing.

---

**Key Points**

- BLUF leads with judgment, confidence, and driver — before evidence
- Every claim requires source attribution and quality characterization
- Confidence language must be calibrated, consistent, and non-stacked
- Facts, inferences, and judgments are categorically distinct and must be labeled as such
- Alternative analysis is not optional — its absence is an analytic deficiency
- The document serves a decision-maker, not the analyst's self-protection

---

