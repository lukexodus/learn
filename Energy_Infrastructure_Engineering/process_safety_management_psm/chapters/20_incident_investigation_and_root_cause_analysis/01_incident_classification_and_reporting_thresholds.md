## Incident Classification and Reporting Thresholds

### Overview

Incident Classification and Reporting Thresholds establish the systematic criteria a facility uses to categorize process safety events by severity and consequence, and to determine which internal, regulatory, and external reporting obligations each category triggers. This element sits at the entry point of Incident Investigation and Root Cause Analysis: before an investigation can be scoped, resourced, and prioritized appropriately, the event must first be correctly classified. Misclassification — treating a significant near-miss as a minor anomaly, or failing to recognize a reportable release — undermines both the internal learning process and regulatory compliance.

Classification frameworks typically combine **actual consequence severity** (what happened) with **potential consequence severity** (what could have happened), since near-misses with high loss-of-containment potential often warrant investigation rigor comparable to actual major incidents.

### Regulatory and Standards Basis

- **29 CFR 1910.119(m)** — PSM Incident Investigation: requires investigation of incidents that resulted in, or could reasonably have resulted in, a catastrophic release of a highly hazardous chemical — establishing the potential-consequence principle in U.S. regulation.
- **40 CFR 68.81 (EPA RMP)** — Requires incident investigation for RMP-covered processes, mirroring the PSM threshold, plus specific reporting of RMP-reportable accidents (five-year accident history disclosure requirements).
- **CERCLA Section 103 / EPCRA Section 304** — Establish reportable quantity (RQ) thresholds that trigger mandatory release notification to the National Response Center, SERC, and LEPC.
- **OSHA Recordkeeping (29 CFR 1904)** — Governs classification of injuries/illnesses as recordable, restricted work, lost time, etc., which overlaps with but is distinct from process safety event classification.
- **CCPS Process Safety Metrics / API RP 754** — Provide industry-standard Tier classification systems (Tier 1–4) specifically for process safety event severity, widely adopted beyond strict regulatory mandate.
- **CSB (Chemical Safety Board) reporting** — Certain catastrophic incidents trigger independent federal investigation regardless of internal classification.

### API RP 754 Tier Classification System

API Recommended Practice 754 is the most widely referenced industry framework for process safety event (PSE) severity classification, distinguishing process safety performance from occupational safety metrics.

| Tier | Description | Example Criteria |
| --- | --- | --- |
| Tier 1 | Loss of Primary Containment (LOPC) event with significant consequence | Release exceeding threshold quantity with injury, fire, explosion, evacuation, or exceeding defined severity thresholds |
| Tier 2 | LOPC event with lesser consequence | Release exceeding a lower threshold quantity but below Tier 1 severity criteria |
| Tier 3 | Challenge to safety systems (near-miss indicators) | Demand on a safety system (e.g., relief valve lift, emergency shutdown activation) without a Tier 1/2 release |
| Tier 4 | Operating discipline and management system performance indicators | Deviations in inspections, procedure adherence, or preventive maintenance completion — leading indicators rather than events |

[Inference] Facilities using the full Tier 1–4 framework generally gain earlier warning of degrading process safety performance than those tracking only Tier 1/2 events, since Tier 3 and 4 indicators surface systemic weaknesses before they manifest as an actual loss of containment.

### Internal Classification Criteria (Typical Structure)

Beyond regulatory Tiering, facilities commonly maintain an internal severity matrix combining actual and potential consequence:

#### Consequence Categories (Actual)

- Fatality or multiple serious injuries
- Single injury requiring medical treatment
- Fire/explosion with property damage
- Environmental release exceeding permit limits
- Release below reportable threshold, contained onsite
- No measurable consequence (near-miss only)

#### Potential Severity Categories

- Could have resulted in fatality/catastrophic release (highest investigation priority)
- Could have resulted in serious injury or significant release
- Could have resulted in minor injury or contained release
- Low potential severity

#### Classification Matrix Logic

A common approach cross-references actual severity against potential severity (using the higher of the two) to assign an overall event classification, ensuring near-misses with high catastrophic potential are not under-investigated simply because no actual harm occurred.

### Reporting Threshold Triggers

```mermaid
flowchart TD
    A[Event Occurs] --> B{Loss of Primary<br/>Containment?}
    B -->|No| C{Safety System<br/>Challenged?}
    C -->|Yes| D[Tier 3: Near-Miss<br/>Internal Investigation]
    C -->|No| E[Tier 4: Operating Discipline<br/>Metric / Log Only]
    B -->|Yes| F{Quantity Exceeds<br/>Reportable Quantity RQ?}
    F -->|No| G[Tier 2: Internal LOPC<br/>Investigation Required]
    F -->|Yes| H{Meets Tier 1<br/>Severity Criteria?<br/>injury/fire/evacuation}
    H -->|No| I[Tier 2: Regulatory Notification<br/>+ Internal Investigation]
    H -->|Yes| J[Tier 1: Full PSM 1910.119(m)<br/>Investigation Required]
    J --> K[EPCRA Sec. 304 Notification<br/>to LEPC/SERC]
    J --> L[CERCLA Sec. 103 Notification<br/>to National Response Center]
    J --> M{RMP-Covered<br/>Process?}
    M -->|Yes| N[RMP Five-Year Accident<br/>History Reporting]
```

### Key Points

- **"Could reasonably have resulted in a catastrophic release" is a potential-consequence standard**, not an actual-harm standard — this is the core distinction that PSM regulation (1910.119(m)) draws, and it is frequently misapplied when facilities classify events based solely on what happened rather than what could have happened.
- **Reportable Quantity (RQ) thresholds are chemical-specific**, established under CERCLA/EPCRA, and must be checked against the specific substance released rather than assumed uniform across chemicals.
- **API RP 754 Tiers are an industry performance metric framework, not a substitute for regulatory investigation triggers** — a Tier 2 event may still separately trigger EPCRA notification depending on the specific chemical and quantity involved.
- **Near-misses (Tier 3) generate some of the highest-value investigation data** relative to investigative cost, since they reveal system vulnerabilities without the complicating factors (damage, injury, legal exposure) present in actual major incidents.
- **Classification decisions should be made promptly and by trained personnel**, since delayed or incorrect initial classification can cascade into missed regulatory notification deadlines.

### Example: Reportable Quantity Threshold Illustration

| Chemical | CERCLA RQ (lbs) | EPCRA Section 304 Applicability |
| --- | --- | --- |
| Ammonia (anhydrous) | 100 | Yes, if release exceeds RQ within 24 hours |
| Chlorine | 10 | Yes, if release exceeds RQ within 24 hours |
| Sulfuric Acid | 1,000 | Yes, if release exceeds RQ within 24 hours |
| Hydrogen Sulfide | 100 | Yes, if release exceeds RQ within 24 hours |

[Unverified] Specific RQ values are subject to periodic EPA revision and vary by chemical listing status; facilities should confirm current RQ figures against the applicable CERCLA Table 302.4 listing rather than relying on previously recorded values, since these thresholds can be updated through rulemaking.

### Common Pitfalls

- **Classifying based on actual outcome only**, missing the potential-severity dimension required by 1910.119(m) — a near-miss that could have been catastrophic gets logged as a minor event and receives inadequate investigation depth.
- **Inconsistent classification across shifts or personnel** due to lack of a documented, trained classification procedure, leading to unequal investigation rigor for similar events.
- **Missed regulatory notification deadlines** caused by delayed internal classification — EPCRA Section 304 requires immediate notification, which is incompatible with a slow, informal internal review process before someone recognizes reportability.
- **Treating Tier 4 (operating discipline) metrics as unimportant** because they involve no release, missing early warning signals of system degradation.
- **Conflating OSHA recordkeeping classification (1904) with process safety event classification** — a process safety incident with no injury may still be a Tier 1 PSE, and conversely an injury-causing event may not indicate a significant process safety system failure.

### Best Practices

- Maintain a **documented, trained classification procedure** accessible to control room and shift personnel who make the initial event assessment.
- Use a **combined actual/potential severity matrix** consistent with 1910.119(m)'s "could reasonably have resulted in" standard, rather than actual-outcome-only criteria.
- Cross-reference **chemical-specific RQ tables** during classification rather than relying on general release-size judgment.
- Adopt the **API RP 754 Tier framework** (or equivalent) to maintain consistency with industry benchmarking and enable trend analysis across Tier 3/4 leading indicators.
- Build **classification triggers directly into the notification workflow**, so a Tier 1 classification automatically prompts the EPCRA/CERCLA notification checklist rather than relying on separate manual recognition.
- Periodically **audit classification decisions** against actual event records to identify systemic under- or over-classification patterns.
- Ensure classification criteria are **reviewed and updated** following Management of Change (MOC) actions that alter chemical inventories, quantities, or regulatory applicability.

### Related Topics

- Root Cause Analysis Methodologies
- Near-Miss Reporting Systems and Culture
- API RP 754 Process Safety Metrics
- Community Right-to-Know and Public Notification
- Coordination with Local Emergency Responders
- Management of Change (MOC) and Regulatory Applicability Review
- CSB Investigation Triggers and Independent Federal Review