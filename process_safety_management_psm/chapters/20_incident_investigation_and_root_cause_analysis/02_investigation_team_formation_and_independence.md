## Investigation Team Formation and Independence

### Overview

Investigation team formation is the process of selecting, structuring, and authorizing the group of individuals responsible for conducting a Process Safety Management (PSM) incident investigation. The composition and independence of this team directly determine the credibility, thoroughness, and regulatory defensibility of the root cause analysis that follows. OSHA's Process Safety Management standard (29 CFR 1910.119(m)) requires that incidents be investigated promptly, and while the regulation does not prescribe an exact team composition, it establishes a floor for competency and participation that shapes how teams are built.

### Regulatory Basis

**29 CFR 1910.119(m) — Incident Investigation**

The standard requires investigation of any incident that resulted in, or could reasonably have resulted in, a catastrophic release of a highly hazardous chemical. Key team-related requirements include:

- An investigation team must be established "as promptly as possible, but not later than 48 hours following the incident."
- The team must include at least one employee knowledgeable in the process involved, including a contract employee if the incident involved contract work.
- Other team members should have appropriate knowledge and experience to thoroughly investigate and analyze the incident.

**CCPS (Center for Chemical Process Safety) Guidance**

CCPS's "Guidelines for Investigating Chemical Process Incidents" extends beyond the regulatory minimum, recommending multidisciplinary teams sized and structured according to incident severity, and explicitly recommending independence safeguards not mandated by OSHA text but considered industry best practice.

**EPA Risk Management Program (40 CFR Part 68.81)**

Parallel investigation requirements apply to facilities covered under the Risk Management Program, largely mirroring OSHA's team composition language.

### Core Team Composition Requirements

#### Mandatory Members (Per 1910.119(m)(2))

- **At least one employee knowledgeable in the process involved** — typically an operator, process engineer, or process supervisor with direct working knowledge of the unit or system where the incident occurred.
- **A contract employee**, if the incident involved contract work — ensures the perspective and process knowledge of contractors performing the work is represented, not just the host employer's view.

#### Recommended Supplementary Members (Industry Practice)

- **Process safety engineer** — provides technical understanding of process hazards, safeguards, and design intent.
- **Maintenance/mechanical representative** — relevant when equipment failure, mechanical integrity, or inspection history is implicated.
- **Instrumentation and controls (I&C) specialist** — necessary when the incident involves control systems, interlocks, or safety instrumented systems (SIS).
- **Metallurgist or materials engineer** — for incidents involving corrosion, fatigue, or material failure.
- **Human factors/behavioral specialist** — for incidents with significant human performance components.
- **Health and safety (EHS) representative** — ensures regulatory and occupational safety considerations are captured.
- **Team leader/facilitator** — trained in root cause analysis methodologies (e.g., 5 Whys, Fault Tree Analysis, TapRooT, Kepner-Tregoe), responsible for managing team process rather than technical content.
- **Legal/risk management liaison** (non-voting, advisory) — manages privilege and litigation considerations without directing technical findings.

#### Severity-Based Scaling

| Incident Severity | Typical Team Size | Typical Composition |
| --- | --- | --- |
| Near-miss / low consequence | 1–2 investigators | Area supervisor + process knowledgeable employee |
| Moderate (recordable injury, minor release) | 3–5 members | Cross-functional team with facilitator |
| Major (catastrophic release, fatality, major property damage) | 5–10+ members | Multidisciplinary team, senior facilitator, possible third-party/external experts |

### Independence: Core Concept

Independence refers to the degree to which investigation team members and the team leader are free from conflicts of interest, organizational pressure, or personal stake in the outcome that could bias findings toward predetermined conclusions (commonly, findings that avoid implicating management systems or specific individuals).

#### Why Independence Matters

- **Avoiding confirmation bias** — investigators who designed, approved, or operated the process may unconsciously (or consciously) favor explanations that do not implicate their own decisions.
- **Preventing organizational self-protection** — teams reporting to the same management chain responsible for the incident may face pressure, explicit or implicit, to minimize systemic findings.
- **Regulatory and legal defensibility** — investigations perceived as compromised invite regulatory scrutiny (OSHA can review investigation quality during inspections) and undermine credibility in litigation or insurance claims.
- **Preventing root cause suppression** — CCPS analysis of major incidents (e.g., BP Texas City, 2005) has repeatedly identified that investigations lacking independence tend to stop at proximate causes rather than surfacing systemic/latent organizational failures.

#### Independence Safeguards

**Structural Independence**

- Team leader should not report directly to the operations manager responsible for the area where the incident occurred.
- Team members should not include individuals who made the specific operational decisions under investigation (e.g., the shift supervisor who authorized the bypassed interlock should not lead or vote on findings related to that bypass).
- For major incidents, many organizations mandate a corporate-level or third-party-led investigation rather than site-led.

**Procedural Independence**

- Investigation findings should not require pre-approval by the implicated department before release.
- Access to documents, personnel interviews, and physical evidence must not be gated by individuals with a stake in the outcome.
- [Inference] Some organizations use a "chain of custody" model for evidence and interview notes analogous to forensic investigations, though this is not universally standardized across the industry.

**External Independence (for High-Consequence Incidents)**

- Third-party investigators or regulatory-adjacent bodies (e.g., CSB — U.S. Chemical Safety and Hazard Investigation Board — for major incidents) may be engaged.
- The CSB itself operates as an independent federal agency with no regulatory or enforcement authority, specifically to preserve investigatory independence — its findings cannot be used as enforcement evidence, which is designed to encourage open cooperation from facility personnel.

### Team Formation Process

```mermaid
flowchart TD
    A[Incident Occurs] --> B{Meets PSM 1910.119(m) Threshold?}
    B -->|No| C[Handle via standard incident reporting]
    B -->|Yes| D[Initiate investigation within 48 hours]
    D --> E[Secure scene and preserve evidence]
    E --> F[Select Team Leader - Independent of implicated area]
    F --> G[Identify mandatory members: process-knowledgeable employee, contractor rep if applicable]
    G --> H[Add supplementary technical members based on incident type]
    H --> I{Severity assessment}
    I -->|Major/Catastrophic| J[Consider third-party or corporate-level involvement]
    I -->|Moderate/Minor| K[Site-level cross-functional team]
    J --> L[Formal charter: scope, authority, timeline]
    K --> L
    L --> M[Conduct investigation]
    M --> N[Draft findings and recommendations]
    N --> O[Independent review before finalization]
    O --> P[Report distribution and corrective action tracking]
```

### Team Charter Elements

A formal charter or terms-of-reference document should be established at team formation to prevent scope drift and clarify authority. Typical elements:

- **Scope statement** — defines the boundaries of the investigation (single incident vs. systemic review of related events).
- **Authority level** — what access the team has (documents, interviews, equipment, ability to halt operations if similar hazards are found elsewhere).
- **Timeline and milestones** — interim reporting requirements, target completion date.
- **Reporting line** — to whom the team reports (ideally, a level above the implicated operational unit, e.g., site manager, corporate EHS, or a PSM steering committee).
- **Confidentiality and just culture provisions** — assurance that the investigation is oriented toward systemic learning, not individual blame, to encourage candid participation (see Just Culture principles below).

### Just Culture and Its Relationship to Independence

A "just culture" framework distinguishes between:

- **Human error** (unintentional, system-induced) — treated as a systems/design issue.
- **At-risk behavior** (risk not recognized or believed justified) — addressed through coaching and system redesign.
- **Reckless behavior** (conscious disregard of substantial risk) — addressed through disciplinary action.

**Key Point:** Investigation teams that conflate independence with punitive intent often see reduced candor from witnesses. Independence should be framed as impartiality toward *systemic causes*, not as a mechanism for assigning blame. Teams perceived as "hunting for someone to fire" tend to produce shallower investigations because personnel become defensive and withhold information.

### Common Pitfalls in Team Formation

- **Insufficient process knowledge on the team** — leads to superficial technical findings; violates the explicit 1910.119(m) requirement if no process-knowledgeable employee is included.
- **Team leader with a conflict of interest** — e.g., the engineering manager who approved the original design leading an investigation into a design-related failure.
- **Excluding contractor perspective** — when contract personnel were involved in the incident, omitting a contractor representative violates the regulatory requirement and produces an incomplete factual record.
- **Undersized teams for major incidents** — a single investigator attempting a catastrophic-release investigation typically cannot cover process, mechanical, human factors, and management system dimensions with sufficient rigor.
- **Delayed formation** — exceeding practical timeliness allows evidence degradation (volatile process conditions, faded witness memory, equipment already returned to service).
- **No independent review step** — findings drafted and finalized by the same individuals without a check by someone outside the investigating unit.

### Example: Team Formation Scenario

A pressure relief valve (PRV) failure results in a minor hydrocarbon release with no injuries at a refinery unit. Under a well-structured team formation approach:

- **Team Leader:** Corporate process safety engineer (not site-based, avoiding proximity bias to the unit).
- **Mandatory member:** Unit operator on shift during the release (process-knowledgeable employee).
- **Mandatory member (if applicable):** Representative from the third-party contractor who last serviced the PRV.
- **Supplementary members:** Mechanical integrity engineer (PRV inspection history), instrumentation technician (if the PRV setpoint was electronically monitored), EHS representative.
- **Independence safeguard applied:** The unit's operations manager, who had deferred a previously scheduled PRV inspection due to production pressure, is interviewed as a witness but is explicitly excluded from the investigation team and from reviewing draft findings before submission.

### Documentation Requirements

Per 1910.119(m)(3)–(5), the investigation report must be prepared and must address, at minimum:

- Date of incident
- Date investigation began
- A description of the incident
- The factors that contributed to the incident
- Recommendations resulting from the investigation

While team composition itself is not a listed report element, OSHA compliance officers reviewing PSM programs frequently evaluate whether the team included the required process-knowledgeable employee and contractor representative, as this is a documented, auditable requirement.

### Related Topics

- Root Cause Analysis Methodologies (5 Whys, Fault Tree Analysis, TapRooT, Kepner-Tregoe)
- Incident Classification and Investigation Triggering Criteria
- Evidence Preservation and Chain of Custody in Process Incidents
- Interviewing Techniques for Incident Witnesses
- Human Factors Analysis in Process Safety Investigations
- Just Culture Frameworks and Disciplinary Decision Trees
- Corrective Action Tracking and Verification of Effectiveness
- Management of Change (MOC) Failures as Root Causes
- CSB Case Studies (e.g., BP Texas City, Chevron Richmond, West Fertilizer)
- Multi-Site and Systemic Incident Investigation (Recurring Incident Analysis)