## Root Cause Analysis and Third-Party Audit Provisions

### Regulatory Context and Origin

The Root Cause Analysis (RCA) and Third-Party Audit provisions originate from amendments to the U.S. EPA's Risk Management Program (RMP) rule under 40 CFR Part 68, promulgated pursuant to Section 112(r) of the Clean Air Act. These provisions were first introduced in the January 2017 RMP Amendments (the "2017 Amendments" or "Obama-era rule"), developed following a series of catastrophic incidents, most notably the 2013 West Fertilizer Company explosion in West, Texas, and the 2012 Chevron Richmond Refinery fire. Executive Order 13650 ("Improving Chemical Facility Safety and Security," issued 2013) directed EPA, OSHA, and DHS to modernize chemical safety regulations, which led directly to the 2017 rule text.

The provisions underwent a turbulent regulatory history:

- **2017**: Final rule published, including RCA and third-party audit requirements
- **2017 (delay)**: EPA delayed the effective date; this delay was successfully challenged in court (*Air Alliance Houston v. EPA*)
- **2019**: EPA issued a Reconsideration Rule that rescinded the third-party audit requirement and narrowed RCA-related provisions
- **2024**: EPA finalized the "Safer Communities by Chemical Accident Prevention" rule, reinstating and strengthening third-party audit requirements and enhancing root cause analysis obligations, with a particular focus on facilities with repeated incidents

[Inference] Given the rule's history of being revised across presidential administrations, facilities should verify the currently enforceable version of 40 CFR Part 68 at the time of compliance planning, as further reconsideration is plausible.

### Applicability Tiers Under RMP

40 CFR Part 68 categorizes covered processes into three program levels, which determine the scope of applicable requirements:

| Program Level | Criteria | RCA/Audit Relevance |
| --- | --- | --- |
| Program 1 | Minimal off-site consequence, no accident history meeting criteria | Reduced requirements; RCA/third-party audit provisions largely inapplicable |
| Program 2 | Processes not meeting Program 1 or 3 criteria | Full RCA and audit provisions apply |
| Program 3 | NAICS codes tied to OSHA PSM-covered industries (e.g., petroleum refining, chemical manufacturing) | Full RCA and audit provisions apply; third-party audit triggers most relevant here |

The enhanced third-party audit provision specifically targets Program 2 and Program 3 processes, with heightened applicability tied to accident history and specific higher-risk NAICS sectors (e.g., petroleum refineries under NAICS 324110 and certain chemical manufacturers).

### Root Cause Analysis Requirements

**Distinction from Prior Incident Investigation Rule**

Prior to the amendments, 40 CFR 68.81 required incident investigation but did not mandate identification of the systemic "root cause" — investigations could stop at proximate or immediate causes (e.g., "valve failed") without probing underlying management system failures (e.g., "preventive maintenance program lacked defined inspection intervals").

The amended rule requires that incident investigations determine the **root cause(s)**, defined generally as the fundamental, underlying reason(s) — often organizational, procedural, or management-system-related — that, if corrected, would prevent recurrence of the incident or similar incidents.

**Key Points**

- Root cause analysis is mandatory for any RMP-reportable accidental release, and under the 2024 rule, also for "near misses" that could reasonably have resulted in a catastrophic release, per some interpretations of the strengthened investigation trigger
- The methodology used is not rigidly prescribed by EPA; facilities may select an appropriate root cause analysis methodology (e.g., 5 Whys, Fault Tree Analysis, TapRooT, Ishikawa/Fishbone Diagram, Human Performance/HPI-based analysis, Management Oversight and Risk Tree — MORT)
- Investigation reports must be completed within a defined timeframe (traditionally 12 months under prior investigation rules; timelines and content requirements were tightened under the 2024 rule)
- Findings must feed into corrective action tracking, and corrective actions must be resolved and documented, with follow-up on any delayed items

**Common Root Cause Analysis Methodologies**

*5 Whys*: Iteratively asking "why" a failure occurred until reaching a systemic cause. Simple but prone to stopping prematurely at a single causal chain.

*Fault Tree Analysis (FTA)*: A top-down, deductive method that maps logical relationships (AND/OR gates) between a top-level undesired event and contributing basic events. Well-suited for complex process systems with multiple contributing failure modes.

*Ishikawa (Fishbone) Diagram*: Categorizes potential causes into groups (commonly: Man, Machine, Method, Material, Measurement, Environment — the "6 Ms") to visually organize brainstormed contributing factors before root cause determination.

*TapRooT*: A proprietary, structured RCA system combining a SnapCharT (sequence-of-events timeline) with a Root Cause Tree(R) dictionary to distinguish causal factors from true root causes, widely used in high-hazard industries.

*MORT (Management Oversight and Risk Tree)*: A comprehensive analytical tree originally developed for the U.S. Energy Research and Development Administration, focused on identifying deficiencies in management systems and barriers/controls.

**Diagram: Root Cause Analysis Sequential Logic (svg_diagram)**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 480">
<text x="450" y="30" font-size="20" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Root Cause Analysis Sequential Logic (svg_diagram)</text>
<rect x="50" y="60" width="180" height="60" rx="8" fill="#dbeafe" stroke="#1e40af" stroke-width="2" />
<text x="140" y="85" font-size="13" text-anchor="middle" fill="#1e3a8a" font-weight="bold">Incident / Near Miss</text>
<text x="140" y="103" font-size="11" text-anchor="middle" fill="#1e3a8a">Trigger Event</text>
<rect x="290" y="60" width="180" height="60" rx="8" fill="#dbeafe" stroke="#1e40af" stroke-width="2" />
<text x="380" y="85" font-size="13" text-anchor="middle" fill="#1e3a8a" font-weight="bold">Data Collection</text>
<text x="380" y="103" font-size="11" text-anchor="middle" fill="#1e3a8a">Interviews, logs, evidence</text>
<rect x="530" y="60" width="180" height="60" rx="8" fill="#dbeafe" stroke="#1e40af" stroke-width="2" />
<text x="620" y="85" font-size="13" text-anchor="middle" fill="#1e3a8a" font-weight="bold">Sequence of Events</text>
<text x="620" y="103" font-size="11" text-anchor="middle" fill="#1e3a8a">Timeline reconstruction</text>
<rect x="670" y="180" width="180" height="60" rx="8" fill="#fef3c7" stroke="#b45309" stroke-width="2" />
<text x="760" y="205" font-size="13" text-anchor="middle" fill="#78350f" font-weight="bold">Causal Factor ID</text>
<text x="760" y="223" font-size="11" text-anchor="middle" fill="#78350f">Deviations from norm</text>
<rect x="430" y="180" width="180" height="60" rx="8" fill="#fef3c7" stroke="#b45309" stroke-width="2" />
<text x="520" y="205" font-size="13" text-anchor="middle" fill="#78350f" font-weight="bold">Apply RCA Method</text>
<text x="520" y="223" font-size="11" text-anchor="middle" fill="#78350f">5 Whys / FTA / TapRooT</text>
<rect x="190" y="180" width="180" height="60" rx="8" fill="#fde68a" stroke="#b45309" stroke-width="2" />
<text x="280" y="205" font-size="13" text-anchor="middle" fill="#78350f" font-weight="bold">Root Cause(s)</text>
<text x="280" y="223" font-size="11" text-anchor="middle" fill="#78350f">Systemic/mgmt-system level</text>
<rect x="60" y="300" width="200" height="60" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="2" />
<text x="160" y="325" font-size="13" text-anchor="middle" fill="#14532b" font-weight="bold">Corrective Actions</text>
<text x="160" y="343" font-size="11" text-anchor="middle" fill="#14532b">Assigned, resourced, dated</text>
<rect x="330" y="300" width="200" height="60" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="2" />
<text x="430" y="325" font-size="13" text-anchor="middle" fill="#14532b" font-weight="bold">Implementation Tracking</text>
<text x="430" y="343" font-size="11" text-anchor="middle" fill="#14532b">Status monitoring</text>
<rect x="600" y="300" width="200" height="60" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="2" />
<text x="700" y="325" font-size="13" text-anchor="middle" fill="#14532b" font-weight="bold">Verification of Effectiveness</text>
<text x="700" y="343" font-size="11" text-anchor="middle" fill="#14532b">Did it prevent recurrence?</text>
<rect x="330" y="410" width="240" height="55" rx="8" fill="#fee2e2" stroke="#b91c1c" stroke-width="2" />
<text x="450" y="435" font-size="13" text-anchor="middle" fill="#7f1d1d" font-weight="bold">Feed Into PSM Elements</text>
<text x="450" y="452" font-size="11" text-anchor="middle" fill="#7f1d1d">Training, MOC, PSSR, Mechanical Integrity</text>
<line x1="230" y1="90" x2="285" y2="90" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="470" y1="90" x2="525" y2="90" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="700" y1="120" x2="760" y2="175" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="670" y1="210" x2="615" y2="210" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="430" y1="210" x2="375" y2="210" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="260" y1="240" x2="180" y2="295" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="260" y1="330" x2="325" y2="330" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="530" y1="330" x2="595" y2="330" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
<line x1="450" y1="360" x2="450" y2="405" stroke="#374151" stroke-width="2" marker-end="url(#arrow1)" />
</svg>

### Third-Party Audit Provisions

**Purpose and Rationale**

Compliance audits under baseline RMP requirements (40 CFR 68.79 / 68.58 depending on program level) have historically permitted self-auditing by facility personnel. EPA identified a conflict-of-interest concern: internal auditors evaluating their own facility's program may lack independence, may face organizational pressure to minimize findings, or may lack specialized expertise to identify systemic gaps. The third-party audit provision was designed to address this by requiring an independent, qualified external party to conduct the compliance audit under specified trigger conditions.

**Trigger Conditions for Mandatory Third-Party Audits**

A third-party audit is triggered when either of the following occurs (thresholds and precise triggers should be verified against the currently effective rule text, given the regulatory history described above):

1. **Accident-triggered audit**: The facility experiences an RMP-reportable accidental release from a covered process, meeting specified severity/consequence criteria (e.g., resulting in offsite impacts, fatalities, serious injuries, or significant property/environmental damage as defined in the accident history reporting criteria at 40 CFR 68.42)
2. **Regulatory-agency-triggered audit**: The implementing agency (EPA Regional Office or delegated state/local authority) makes a formal finding, based on inspection or other information, that conditions at the facility could lead to an accidental release of a regulated substance, and orders a third-party audit

**Independence and Competency Requirements**

The third-party auditor (or audit team, with a designated Lead Auditor) must meet defined independence and competency criteria, generally including:

- No financial interest or ownership stake in the facility being audited
- Not having performed the RMP compliance audit being reviewed, or having a role in the design/operation of the covered process, within a specified look-back period
- Demonstrated knowledge and experience in: process safety management principles, the applicable RMP regulatory requirements, auditing techniques, and the specific process technology/hazards present at the facility
- Where a Lead Auditor manages a multidisciplinary team, the team collectively must possess the requisite technical competencies

**Audit Scope and Deliverables**

The third-party audit must verify compliance with all applicable Prevention Program elements (Process Safety Information, PHA, Operating Procedures, Training, Mechanical Integrity, MOC, PSSR, Incident Investigation, Compliance Audits, Employee Participation, Hot Work Permit, Contractors) and Emergency Response Program elements as applicable to the covered program level.

Deliverables typically include:

- A written audit report identifying findings, including compliance deficiencies
- A finding of whether the facility's RMP is adequate to address the hazards of the covered process
- Certification of the audit's completion and the auditor's independence/qualifications
- A schedule for the owner/operator to address and correct identified deficiencies, with documentation of corrective action completion or, for delayed items, a documented rationale and revised timetable

**Comparison: Internal Compliance Audit vs. Third-Party Audit**

| Attribute | Standard Internal Audit (68.79/68.58) | Third-Party Audit |
| --- | --- | --- |
| Frequency | At least every 3 years | Triggered by qualifying accident or agency order |
| Auditor | May be facility or corporate personnel | Independent external auditor/team meeting competency criteria |
| Independence requirement | Recommended but historically not mandated to the same degree | Explicit disqualification criteria (financial interest, prior involvement) |
| Findings disposition | Internal corrective action tracking | Corrective action tracking with regulatory visibility/reporting obligations |
| Regulatory trigger | Calendar-based | Event-based (accident) or agency-directed |

### Root Cause Analysis and Third-Party Audit Interaction

Under the 2024 rule strengthening, these two provisions are structurally linked: a root cause analysis finding that identifies systemic Prevention Program failures can itself become an input that agencies consider when determining whether to order a third-party audit. Conversely, the accident that triggers a third-party audit is, by definition, also the subject of a mandatory root cause analysis under the incident investigation requirements. In practice, both processes should be run in parallel with information-sharing between the investigation team and the audit scope-setting process, since RCA findings often reveal exactly which Prevention Program elements the third-party audit should scrutinize most closely.

**Example**

A Program 3 refinery experiences a reportable release from a heat exchanger tube failure. The incident investigation team applies Fault Tree Analysis and determines the root cause was not simply "tube corrosion" (a proximate cause) but rather: (1) the Mechanical Integrity program's inspection interval for that exchanger class had not been updated after a process change increased corrosive service conditions, and (2) the Management of Change procedure did not include a mandatory Mechanical Integrity review step for changes affecting corrosion rates. This finding — a systemic MOC/MI gap — becomes documented in the RCA report. Because the release met the accidental-release severity criteria, a third-party audit is also triggered; the audit scope explicitly includes deep review of the MOC procedure and Mechanical Integrity inspection-interval-setting methodology across all covered processes at the facility, not just the one exchanger involved in the incident.

### Enforcement and Compliance Considerations

- Failure to conduct a required RCA, or conducting an inadequate one (e.g., stopping at proximate cause), can be cited as a violation of the incident investigation requirements and may compound penalties in a subsequent enforcement action
- Failure to retain a qualified, independent third-party auditor when triggered, or failure to implement/track corrective actions from the audit, exposes the facility to separate enforcement action under Clean Air Act Section 113
- [Unverified] Specific penalty amounts and per-day violation calculations are subject to periodic inflation adjustments under the Federal Civil Penalties Inflation Adjustment Act and should be confirmed against current EPA penalty policy at time of assessment
- State-delegated RMP programs (implemented through State Implementing Agencies) may impose additional or more stringent audit and RCA requirements than the federal baseline

### Related Topics

- OSHA PSM Standard 29 CFR 1910.119 Incident Investigation (comparative analysis with EPA RMP 40 CFR 68.81)
- Management of Change (MOC) Procedures and Pre-Startup Safety Review (PSSR)
- Mechanical Integrity Program Design and Inspection Intervals
- CSB (Chemical Safety Board) Investigation Methodology and Recommendations
- Human Factors and Human Performance Improvement (HPI) in Root Cause Analysis
- Corrective Action Tracking Systems and Effectiveness Verification
- RMP Accident History Reporting Criteria (40 CFR 68.42)
- State Implementing Agency Variations in RMP Enforcement