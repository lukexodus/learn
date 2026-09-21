## Coordinating Host Employer and Contractor Responsibilities


### Overview

Coordinating host employer and contractor responsibilities refers to the integrated management system by which a facility operating a PSM-covered process and its contracted service providers align safety obligations, communication channels, and operational controls so that no gap in accountability exists between the two parties. While prequalification addresses contractor selection and orientation/training addresses individual worker competence, coordination addresses the ongoing, day-to-day interface: how hazard information flows, how work is authorized, how emergencies are jointly managed, and how performance is monitored throughout the duration of the contract.

OSHA 29 CFR 1910.119(h) deliberately splits obligations between host and contract employers rather than assigning them to one party, creating a shared-responsibility model. Effective coordination is the mechanism that makes this shared model function in practice; without it, each party may assume the other has addressed a given hazard, creating gaps that have historically contributed to major process safety incidents (e.g., the 2005 Texas City refinery explosion investigation identified breakdowns in host-contractor communication regarding trailer siting and hazard awareness as contributing factors).

### Regulatory Foundation

**Key Points**

- **1910.119(h)(2)** — Host Employer Responsibilities: obtain/evaluate contractor safety performance (prequalification); inform contractors of known hazards; explain the Emergency Action Plan; develop safe work practices controlling entrance/presence/exit in covered process areas; periodically evaluate contractor performance; maintain a contract employee injury/illness log related to work in the covered process area.
- **1910.119(h)(3)** — Contract Employer Responsibilities: train and instruct employees; document training; ensure employees follow host safety rules; advise the host of unique or newly discovered hazards.
- **Multi-Employer Worksite Doctrine** (OSHA enforcement policy, not a standalone standard): allows OSHA to cite the "creating," "exposing," "correcting," or "controlling" employer for a hazard, meaning both host and contractor can be independently liable depending on their role relative to the hazard — this is the enforcement backdrop that makes coordination a legal as well as operational necessity.
- **40 CFR 68.87** (EPA RMP): parallel host/contractor coordination requirements for RMP-covered facilities.

### The Coordination Gap Problem

Because the standard splits duties, ambiguity can arise over *who* discloses *what* and *when*. Coordination systems exist to close three specific gap types:

1. **Information gaps** — hazard knowledge that exists with one party but is never transmitted to the other (e.g., host knows a line is temporarily de-energized differently than normal; contractor doesn't know).
2. **Authorization gaps** — work proceeding without both parties confirming the same understanding of scope, isolation status, and permit conditions.
3. **Accountability gaps** — an unclear answer to "who is responsible for stopping this work if a hazard emerges" during execution.

### Coordination Framework

```mermaid
flowchart TD
    A[Contract Awarded] --> B[Joint Kickoff Meeting]
    B --> C[Host: Disclose Process Hazards & EAP]
    B --> D[Contractor: Disclose Scope-Specific Hazards]
    C --> E[Establish Safe Work Practices & Boundaries]
    D --> E
    E --> F[Define Permit-to-Work Interface]
    F --> G[Daily/Shift Coordination Meetings]
    G --> H{New Hazard Identified?}
    H -->|Yes, by Host| I[Host Notifies Contractor Immediately]
    H -->|Yes, by Contractor| J[Contractor Notifies Host per 1910.119(h)(3)(v)]
    I --> K[Joint Reassessment / Work Stoppage if Needed]
    J --> K
    H -->|No| L[Continue Work Under Existing Permit]
    K --> M[Update Permit / JHA / MOC as Required]
    M --> G
    L --> N[Periodic Joint Performance Review]
    N --> O[Document in Contractor Evaluation Log]
    O --> P{Contract Complete?}
    P -->|No| G
    P -->|Yes| Q[Close-Out Review & Lessons Learned]
```

### Key Coordination Mechanisms

1. **Joint Kickoff / Pre-Job Meeting**
   - Held before work begins on any covered-process-adjacent scope.
   - Host presents: process overview, known hazards, EAP summary, site safe work practice requirements, permit system explanation.
   - Contractor presents: scope of work, equipment to be used, unique hazards their work introduces (e.g., specialty chemicals, hot work sources, heavy lifts), crew composition and supervision structure.
   - Both parties agree on communication protocols and escalation paths.
2. **Permit-to-Work (PTW) Interface**
   - The PTW system is the operational point where host and contractor responsibilities are jointly executed: the host issuing authority verifies isolation, hazard controls, and process conditions; the contractor's competent person/supervisor verifies crew readiness and signs acceptance of the permit conditions.
   - Both signatures on a permit represent a coordination checkpoint — neither party proceeds unilaterally.
3. **Daily/Shift Coordination Meetings**
   - Brief, recurring touchpoints (typically at shift start) where host operations personnel and contractor supervision review planned work, changes in process conditions, and any new hazards.
   - Particularly critical during turnarounds where multiple contractors work concurrently in overlapping or adjacent areas (simultaneous operations, or SIMOPs).
4. **Simultaneous Operations (SIMOPs) Coordination**
   - When multiple contractors (or contractors and host operations) work in the same area at the same time, a SIMOPs risk assessment identifies conflicts (e.g., hot work near a confined space entry, crane lifts over occupied work areas) and establishes control measures or scheduling separation.
5. **Two-Way Hazard Reporting Channel**
   - Formal mechanism (not just informal conversation) for the contractor to report hazards discovered during their work back to the host, satisfying 1910.119(h)(3)(v).
   - Equally, a mechanism for the host to push newly identified hazards (e.g., from an MOC or incident investigation) out to active contractors in near real time.
6. **Joint Emergency Response Integration**
   - Contractors must be integrated into muster/accountability procedures, not just informed of them.
   - Host emergency response team needs contractor headcount and location data during an event; this typically requires an integrated access-control/time-and-attendance system feeding a real-time muster list.
7. **Periodic Performance Evaluation**
   - Satisfies 1910.119(h)(2)(iv): host must periodically evaluate contractor performance in fulfilling their obligations.
   - Typically documented via scorecards covering safety compliance, incident/near-miss history, permit adherence, and responsiveness to corrective actions.

### Roles and Interface Matrix

| Activity | Host Employer Role | Contract Employer Role |
| --- | --- | --- |
| Hazard disclosure | Disclose known process hazards (chemicals, pressures, temperatures) | Disclose hazards unique to their work scope and equipment |
| Emergency Action Plan | Explain applicable EAP provisions | Instruct own employees on EAP provisions relayed by host |
| Safe work practices | Develop practices controlling entry/exit into covered process areas | Ensure employees comply with host safe work practices |
| Permit-to-work | Issue/authorize permits; verify isolation and process conditions | Accept permits; verify crew readiness and PPE compliance |
| Training | Provide site-specific orientation content | Train employees in job-specific safe work practices; document training |
| Hazard discovery during work | Investigate and communicate any newly identified process-related hazard | Report unique/newly discovered hazards to host immediately |
| Performance monitoring | Periodically evaluate contractor performance; maintain injury/illness log for contractor work in covered areas | Report incidents/near-misses per host and regulatory requirements |
| Emergency response | Account for all personnel including contractors; direct evacuation/muster | Follow host EAP; report crew status to host during emergency |

### Example: Coordination Checklist for Turnaround Mobilization

**Example**



```
Pre-Mobilization Coordination Checklist
----------------------------------------
[ ] Joint kickoff meeting scheduled with all contractor supervisors
[ ] Host has disclosed known process hazards for units under turnaround
[ ] EAP walkthrough completed with contractor safety representatives
[ ] SIMOPs risk assessment completed for overlapping work areas
[ ] Permit-to-work issuing authority list confirmed and communicated
[ ] Two-way hazard reporting channel established (contact list, escalation path)
[ ] Daily coordination meeting schedule set (time, location, required attendees)
[ ] Contractor muster/accountability integration confirmed with access control
[ ] Emergency response roles for contractor supervisors defined
[ ] Performance evaluation criteria and reporting cadence communicated to contractor
```

### Common Coordination Failure Modes

- **Assumed disclosure**: host assumes a hazard is "obvious" or was covered in general orientation, so it is not repeated at the job-specific level; contractor assumes silence means no hazard exists.
- **Permit-without-verification**: a permit is signed as a formality without the host issuing authority and contractor supervisor jointly walking down actual field conditions.
- **SIMOPs blind spots**: multiple contractors mobilized under separate contracts without a shared schedule, leading to incompatible activities occurring simultaneously in the same area (e.g., crane lift scheduled over an open confined space entry).
- **One-way reporting**: hazard reporting channels exist only from host-to-contractor (orientation, EAP briefings) but no formalized path exists for contractor-to-host reporting, undermining 1910.119(h)(3)(v).
- **Evaluation as paperwork**: periodic performance evaluations conducted retroactively or superficially, disconnected from real-time coordination data (permit compliance, near-miss trends), reducing their value as a corrective mechanism. [Inference: commonly identified in PSM audit findings, though prevalence varies by organization and audit rigor.]
- **Emergency muster gaps**: contractor headcount not reliably integrated into the host's accountability system, delaying full personnel accountability during an emergency response.

### Related Topics

- Contractor Prequalification and Selection
- Contractor Orientation and Training Requirements
- Permit-to-Work Systems for Contractors
- Simultaneous Operations (SIMOPs) Risk Assessment
- Emergency Action Plan (EAP) Development and Communication
- Contractor Performance Evaluation and Scorecard Systems
- Multi-Employer Worksite Citation Policy (OSHA)
- Turnaround/Shutdown Planning and Contractor Mobilization