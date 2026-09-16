## Mandatory, Discretionary, and External Dependencies


### Overview

Dependencies in a project schedule are not all created equal — they differ in *why* they exist and *how much flexibility* the project team has in modifying them. The PMBOK Guide classifies dependencies into three categories based on their source and rigidity: mandatory (hard logic), discretionary (soft logic/preferred logic), and external. A fourth, often-cited hybrid category — internal dependencies — is also addressed here for completeness. Correctly classifying each dependency is critical because it determines how much schedule compression flexibility exists and how much risk exposure the project carries from factors outside the team's control.

### Mandatory Dependencies (Hard Logic)

**Key Points**

- Dependencies that are inherent to the nature of the work itself — physically, legally, or contractually impossible to sequence any other way.
- Often called **hard logic** because they cannot be altered regardless of preference, resource availability, or schedule pressure.
- Typically arise from physical constraints (a wall cannot be painted before it is built) or legal/regulatory constraints (a permit must be issued before construction begins).

**Example**

"Pour Concrete Foundation" must finish before "Erect Wall Framing" can start. There is no sequencing alternative — framing physically cannot rest on a foundation that does not yet exist. This is a Finish-to-Start relationship rooted in mandatory, physical logic.

```mermaid
graph LR
    A[Pour Foundation] -->|Mandatory FS| B[Erect Framing]
```

### Discretionary Dependencies (Soft Logic / Preferred Logic)

**Key Points**

- Dependencies established by the project team based on best practices, industry experience, or preferred sequencing choices — not physical or legal necessity.
- Also called **soft logic** or **preferred logic**, since the sequence *could* technically be changed if circumstances required it.
- Represent the primary lever available for schedule compression (fast-tracking), since these relationships can be relaxed or reordered without violating any physical or legal constraint.

**Example**

A construction team may choose to complete all electrical rough-in work across an entire floor before starting plumbing rough-in on that same floor, purely as a matter of trade sequencing efficiency and crew logistics — not because plumbing is physically incapable of proceeding first. If schedule pressure mounts, the team could choose to run electrical and plumbing in parallel instead.

[Unverified] Discretionary dependencies are widely cited in scheduling literature as the most common source of unnecessary schedule length, since teams often default to sequential "safe" logic out of habit rather than because it is truly required — though the actual proportion of discretionary versus mandatory logic varies significantly by project type and organizational scheduling maturity.

### External Dependencies

**Key Points**

- Dependencies between a project activity and a factor **outside the project team's control** — typically involving third parties, external organizations, or environmental/regulatory conditions.
- The project team cannot directly manage or accelerate these dependencies; they can only plan around them, build in appropriate buffers, and monitor them proactively.
- Common sources: government permitting agencies, external vendors/suppliers, other projects sharing a resource, weather/seasonal windows, and regulatory bodies.

**Example**

"Site Excavation" cannot begin until the local municipality issues an excavation permit. The project team has no direct authority to expedite the municipal review process — they can only submit early, follow up, and build schedule contingency around the uncertain approval timeline.

```mermaid
graph LR
    Ext[Municipal Permit Approval - External] -->|Mandatory FS| A[Site Excavation]
```

Note that a dependency can be **both mandatory and external simultaneously** — the permit-before-excavation relationship is mandatory (legally required) *and* external (controlled by a third party), illustrating that these categories are not mutually exclusive but describe different dimensions of the same dependency.

### Internal Dependencies (Supplementary Category)

**Key Points**

- Dependencies between project activities that remain fully within the project team's control, as opposed to external dependencies.
- Often paired conceptually with external dependencies to complete the "locus of control" dimension, cutting across the mandatory/discretionary distinction.
- Example: The relationship between "Design Review" and "Design Approval," both performed by internal project staff.

### Comparative Summary Table

| Category | Basis | Flexibility | Who Controls It | Typical Example |
| --- | --- | --- | --- | --- |
| Mandatory (Hard Logic) | Physical or legal necessity | None — fixed by nature of work | N/A (inherent to the work) | Foundation before framing |
| Discretionary (Soft Logic) | Best practice, preference, experience | High — can be reordered or overlapped | Project team | Sequencing trades by floor for efficiency |
| External | Relationship to outside parties/factors | Low — team can only plan around it | Third party (government, vendor, weather) | Permit approval before construction |
| Internal (supplementary) | Relationship within project scope | Varies (can be mandatory or discretionary) | Project team | Design review before design approval |

### Why This Classification Matters for Scheduling

**Key Points**

- **Risk Assessment**: External dependencies represent schedule risk exposure that cannot be mitigated through internal effort alone — they require contingency planning, buffer time, and proactive stakeholder management.
- **Schedule Compression Strategy**: When a project needs to be shortened, discretionary dependencies are the first candidates for fast-tracking (reordering or overlapping activities), since altering mandatory or external dependencies is often impossible or requires third-party negotiation.
- **Documentation and Audit Trail**: Best practice requires documenting *why* each dependency was classified as it was, especially discretionary ones, so that future schedule updates or disputes can trace the rationale rather than treating all logic as immutable.
- **Float Interpretation**: Activities tied to external dependencies with uncertain durations (e.g., "permit approval: 4-12 weeks") warrant closer monitoring even if they currently show positive float, since the estimate itself carries higher uncertainty than internally controlled activities.

### Practical Application Example

**Example**

Consider a software product launch with the following dependencies:

| Activity | Predecessor | Dependency Type | Rationale |
| --- | --- | --- | --- |
| Deploy to Production | Complete QA Testing | Mandatory | Code cannot be deployed before it passes required test gates |
| Write Marketing Copy | UI Design Finalized | Discretionary | Team *prefers* to see final UI before writing copy, but copy could be drafted in parallel using wireframes |
| Public Launch Announcement | Third-Party App Store Approval | External | App store review process is controlled entirely by the platform vendor |
| Internal Training Materials | Feature Freeze | Discretionary | Team could begin training material drafts earlier using a feature list, but chooses to wait for stability |

This example shows how a single project typically contains a mix of all three (or four, including internal) dependency types simultaneously, and how classification directly informs where schedule compression opportunities exist (the discretionary items) versus where risk buffers are needed (the external item).

### Conclusion

Mandatory, discretionary, and external dependencies describe fundamentally different sources of schedule constraint: mandatory dependencies are immovable physical or legal realities, discretionary dependencies are team-chosen sequencing preferences that offer the greatest flexibility for compression, and external dependencies represent risk exposure to factors outside the project's control. Explicitly classifying every dependency during network diagram construction — rather than treating all logic ties as equally fixed — enables more accurate risk assessment, more effective schedule compression decisions, and a clearer audit trail for schedule changes.

**Related Topics**

- Constructing a project network diagram
- Schedule compression: Fast-Tracking and Crashing
- Finish-to-Start, Start-to-Start, Finish-to-Finish, and Start-to-Finish relationships
- Lag and Lead time application
- Risk management for externally-driven schedule activities
- Common network diagramming errors