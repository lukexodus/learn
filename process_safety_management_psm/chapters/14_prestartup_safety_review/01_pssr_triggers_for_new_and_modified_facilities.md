## PSSR Triggers for New and Modified Facilities

### Overview

A Pre-Startup Safety Review (PSSR) is a documented, systematic verification performed immediately before introducing a hazardous chemical into a process, confirming that construction and equipment meet design specifications, safety/operating/maintenance/emergency procedures are in place and adequate, a process hazard analysis has been performed and recommendations resolved or implemented, and training of affected employees has been completed. The PSSR "trigger" question is foundational to PSM implementation: *which specific events or changes require a PSSR before startup can proceed?* Misidentifying or missing a trigger is one of the most common PSM compliance gaps, because organizations often correctly perform PSSRs for grassroots new construction but fail to recognize that many smaller modifications also cross the regulatory threshold.

### Regulatory Basis

**Key Points**

- **OSHA 29 CFR 1910.119(i)(1)**: Employers shall perform a pre-startup safety review for new facilities and for modified facilities when the modification is significant enough to require a change in the process safety information.
- **1910.119(i)(2)**: The PSSR shall confirm that: (i) construction and equipment is in accordance with design specifications; (ii) safety, operating, maintenance, and emergency procedures are in place and adequate; (iii) a process hazard analysis has been performed for new facilities and recommendations have been resolved or implemented before startup, and modified facilities meet the requirements in the management of change section (1910.119(l)); and (iv) training of each employee involved in operating a process has been completed.
- **1910.119(l)** (Management of Change): the linkage clause — PSSR is required whenever an MOC-qualifying modification has occurred, because such a modification by definition requires updated Process Safety Information (PSI), which is the exact trigger condition named in 1910.119(i)(1).
- **40 CFR 68.77** (EPA RMP): a substantively parallel PSSR requirement for RMP-covered processes.

### The Core Trigger Test

The regulatory language creates two independent trigger categories:

1. **New facilities** — any newly constructed process that will handle a covered chemical at or above the threshold quantity. PSSR is *always* required before initial startup, without exception or a "significance" threshold.
2. **Modified facilities** — PSSR is required *only* when the modification is "significant enough to require a change in the process safety information (PSI)." This is a significance test, not an automatic requirement for every physical change.

The critical operational skill is correctly applying the significance test to modifications, since this is where most PSSR omissions occur.

### PSSR Trigger Decision Logic

```mermaid
flowchart TD
    A[Project or Change Proposed] --> B{Is this a new facility handling a covered process?}
    B -->|Yes| C[PSSR Mandatory - No Exceptions]
    B -->|No, it is a modification| D{Does the change require an MOC per 1910.119(l)?}
    D -->|No - Replacement in Kind| E[No PSSR Required]
    D -->|Yes| F{Does the MOC change Process Safety Information?}
    F -->|No| G[MOC Required, PSSR Typically Not Required]
    F -->|Yes| H[PSSR Required]
    H --> I[Verify Construction vs Design Specs]
    H --> J[Verify Safety/Operating/Maintenance/Emergency Procedures Updated]
    H --> K[Verify PHA/MOC Recommendations Resolved or Implemented]
    H --> L[Verify Employee Training Completed]
    I --> M[Authorize Startup]
    J --> M
    K --> M
    L --> M
    C --> I
```

### Categories of PSSR-Triggering Events

1. **New Construction / Grassroots Facilities**
   - Any new process unit designed to handle a covered chemical at or above the OSHA threshold quantity.
   - Applies regardless of whether the facility is a standalone plant or a new unit added within an existing PSM-covered site.
2. **Capacity or Throughput Changes**
   - Increasing production rate beyond original design basis (e.g., debottlenecking a reactor system).
   - Triggers PSSR if the change requires updated PSI (revised relief valve sizing, updated material balance, revised safe operating limits).
3. **Equipment Replacement Not "In Kind"**
   - Replacing a component with one of different design, material of construction, capacity, or manufacturer specification.
   - "Replacement in kind" (identical specification, same design, same materials) does *not* trigger MOC or PSSR; a functionally different replacement does.
4. **Piping and Instrumentation Changes**
   - New piping runs, changed pipe routing, new block valves, or relocated instrumentation that alter process flow paths or control logic.
   - Requires updated P&IDs (part of PSI) and therefore triggers the PSSR requirement.
5. **Control System Modifications**
   - DCS/PLC logic changes, new interlocks, changes to safety instrumented functions (SIFs), or changes to alarm setpoints tied to safe operating limits.
   - Because these directly affect operating procedures and safe operating limits (both part of PSI), such changes almost always trigger PSSR.
6. **Chemical Substitution or New Chemical Introduction**
   - Introducing a new hazardous chemical, or substituting a chemical with different hazard properties, into an existing process.
   - Requires updated Safety Data Sheets, hazard information, and often relief/ventilation system re-evaluation — all PSI elements.
7. **Temporary Modifications Left in Place**
   - Temporary bypass, jumper, or temporary piping that becomes effectively permanent without going through the formal MOC/PSSR process — a common audit finding and root cause in incident investigations.
8. **Extended Shutdown Restart**
   - While not a "modification" in the traditional sense, many organizations apply PSSR-equivalent readiness reviews after extended shutdowns (e.g., turnarounds, idle periods exceeding a defined threshold) to verify no unauthorized changes occurred and that all deferred maintenance/PHA action items were closed before restart. [Inference: this is common industry practice beyond the literal OSHA text, often codified in company PSM procedures as an added layer of rigor.]

### Trigger Screening Matrix

| Change Type | MOC Required? | PSSR Typically Required? | Rationale |
| --- | --- | --- | --- |
| Identical replacement part, same specs | No | No | Replacement in kind |
| New relief valve with different set pressure | Yes | Yes | Changes safe operating limits (PSI) |
| Repainting a vessel (non-process-contact) | No | No | No process safety information affected |
| Adding a bypass valve around a control valve | Yes | Yes | Alters process flow paths and potential hazard scenarios |
| Software patch to DCS with no logic change | Possibly (per company procedure) | Usually not, unless logic/setpoints affected | Depends on whether operating parameters change |
| New feedstock supplier, same chemical spec | No (if truly equivalent) | No | No PSI change if hazard properties are identical |
| New feedstock with different impurity profile | Yes | Yes | May affect reactivity, corrosion, or relief scenarios |
| Relocating an existing pump to a new skid, same spec | Depends on piping/support changes | Depends on whether P&IDs change | Evaluate case by case |
| New unit constructed on adjacent land | N/A (new facility) | Yes, mandatory | New facility trigger, not a modification trigger |

### PSSR Content Checklist Once Triggered

**Key Points**

- Construction and equipment verified against approved design specifications (P&IDs, equipment data sheets, material certifications).
- Safety, operating, maintenance, and emergency procedures are in place, current, and reflect the change.
- For new facilities: PHA completed and recommendations resolved or implemented before introducing the hazardous chemical.
- For modified facilities: MOC requirements of 1910.119(l) satisfied, including PHA-of-record updates where applicable.
- Training of all employees who will operate the modified or new process has been completed and documented.
- Punch list items (open construction/commissioning items) are reviewed and categorized as either resolved or formally accepted as not safety-critical before startup, with a defined closure timeline for remaining items.

### Example: PSSR Trigger Screening Form Excerpt

**Example**



```
PSSR Trigger Screening
------------------------------------------------
Project/Change ID:          ____________________
Description of Change:      ____________________

1. Is this a new facility handling a covered process?      [ ] Yes -> PSSR Mandatory
                                                             [ ] No -> continue

2. Was this change processed through MOC (1910.119(l))?     [ ] Yes  [ ] No
   If No: confirm replacement-in-kind justification: _______________

3. Does the change affect any of the following PSI elements?
   [ ] P&IDs / process flow diagrams
   [ ] Safe operating limits / operating procedures
   [ ] Relief system design basis
   [ ] Equipment design specifications
   [ ] Electrical classification / area classification
   [ ] Chemical hazard information (SDS, reactivity data)

   If ANY box checked -> PSSR REQUIRED
   If NO boxes checked -> PSSR not required; document rationale below

Rationale if PSSR not required: __________________________
Reviewed by:  ____________________  Date: __________
```

### Common Pitfalls

- Applying an overly narrow interpretation of "significant enough," treating only large capital projects as PSSR triggers while missing smaller field modifications that still alter PSI.
- Failing to recognize that a "temporary" change left in place indefinitely eventually requires the same PSSR rigor as a permanent modification.
- Conducting the MOC review but skipping the separate, explicit PSSR confirmation step — MOC completion and PSSR are related but are distinct regulatory requirements under 1910.119(l) and 1910.119(i) respectively.
- Allowing startup with open punch list items that are safety-critical, based on an informal verbal assessment rather than a documented PSSR sign-off.
- Not re-triggering PSSR when a project's scope grows during execution (scope creep) beyond what was originally screened. [Inference: commonly cited as a contributing factor in incidents following capital projects, though root causes vary by event.]

### Related Topics

- Management of Change (MOC) Program Requirements
- Process Safety Information (PSI) Elements and Maintenance
- Process Hazard Analysis (PHA) Recommendation Tracking
- Replacement-in-Kind Determination Criteria
- Punch List Management and Startup Readiness
- Operating Procedures Development and Revision Control
- Turnaround/Shutdown Planning and Contractor Mobilization