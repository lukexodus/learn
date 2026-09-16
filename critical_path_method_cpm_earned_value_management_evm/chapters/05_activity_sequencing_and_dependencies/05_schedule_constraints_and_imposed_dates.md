## Schedule Constraints and Imposed Dates

### Definition and Purpose

Schedule constraints are date restrictions applied to activities that override or limit the normal forward-pass/backward-pass logic of the Critical Path Method (CPM). Imposed dates are a specific category of constraint—fixed calendar dates mandated by contracts, regulatory bodies, clients, or external stakeholders that a schedule must accommodate regardless of network logic.

Under normal CPM calculation, an activity's early start (ES) and late finish (LF) are derived purely from predecessor/successor relationships and durations. Constraints interrupt this pure logic-driven calculation by forcing an activity to occur on, before, or after a specific date, independent of what the network math would otherwise produce.

### Why Constraints Are Necessary

**Key Points**

- Pure logic-driven schedules assume unlimited resource availability and no external dependencies
- Real projects have contractual milestones, regulatory windows, and resource-driven limitations
- Constraints reconcile the theoretical network diagram with real-world fixed dates
- Overuse of constraints undermines CPM's core value: dynamic float calculation and critical path identification

### Categories of Constraints

Scheduling software (Primavera P6, Microsoft Project) generally classifies constraints along two axes: **direction** (start vs. finish) and **flexibility** (soft vs. hard).

#### One-Directional (Soft) Constraints

These restrict movement in only one direction, allowing the schedule engine to still calculate float logically on the unrestricted side.

- **Start No Earlier Than (SNET)**: Activity cannot start before the specified date, but can start later if predecessors push it. Commonly used for material delivery dates or permit availability.
- **Finish No Earlier Than (FNET)**: Activity cannot finish before the specified date. Rare; typically used to prevent premature completion reporting.
- **Start No Later Than (SNLT)**: Activity must start by the specified date at the latest; can start earlier.
- **Finish No Later Than (FNLT)**: Activity must finish by the specified date at the latest. Frequently used for contractual interim milestones.

#### Two-Directional (Hard) Constraints

These lock an activity to an exact date, overriding both early and late date calculations.

- **Must Start On (MSO)**: Forces both ES and LS to the specified date.
- **Must Finish On (MFO)**: Forces both EF and LF to the specified date.
- **Mandatory Start / Mandatory Finish** (P6 terminology): Functionally identical to MSO/MFO—the most restrictive constraint type, ignoring predecessor logic entirely.

**Key Points**

- Hard constraints can create logical contradictions—an activity may show negative float or be forced to start before its predecessor finishes
- Software will typically flag these as "constraint conflicts" or display negative total float
- Hard constraints should be reserved for genuinely immovable dates (e.g., a regulatory shutdown window)

### Imposed Dates Specifically

Imposed dates are external, non-negotiable dates that originate outside the project team's control and are typically applied as constraints on specific milestones rather than routine activities.

**Common Sources**

- **Contractual milestones**: Substantial completion dates, liquidated damages trigger dates
- **Regulatory/permit windows**: Environmental permits allowing construction only during certain seasons (e.g., in-water work windows for fish spawning restrictions)
- **Client-mandated dates**: Grand opening, fiscal year-end, trade show launch
- **Funding constraints**: Grant expiration dates, bond issuance deadlines
- **Third-party dependencies**: Utility company connection dates, government inspection scheduling

**Example**

A highway bridge project has an environmental permit restricting in-water pile driving to August 1–October 31 only. The "Drive Piers" activity receives:

- SNET: August 1
- FNLT: October 31

This creates a mandatory window rather than a single point, effectively capping the activity's available duration regardless of how early upstream logic would otherwise allow it to start.

### Impact on Float Calculation

Constraints directly alter total float (TF) by changing late dates (LS/LF) independent of the backward pass driven by project completion.

$$TF = LS - ES = LF - EF$$

When a **Finish No Later Than** constraint is tighter than the calculated late finish from network logic, the constraint becomes the governing late date:

$$LF_{new} = \min(LF_{calculated}, \text{FNLT date})$$

This can produce:

- **Reduced float**: Constraint is tighter than logic would demand, making the activity more critical
- **Negative float**: Constraint date has already been violated by current logic-driven dates—an early warning indicator requiring schedule recovery
- **Artificial float**: A Start No Earlier Than constraint delays ES beyond what predecessors dictate, potentially inflating float on the constrained activity while making it appear less urgent than it actually is

[Inference] Some organizations treat any negative float on a constrained milestone as an automatic schedule health "red flag" requiring formal recovery narrative in monthly reporting, though this is a contractual/organizational policy choice rather than a universal CPM rule.

### Constraint Interaction with Critical Path

```mermaid
flowchart LR
    A[Design Complete] --> B[Procure Materials]
    B --> C[Mobilize Site]
    C --> D[Drive Piers<br/>SNET Aug 1 / FNLT Oct 31]
    D --> E[Construct Superstructure]
    E --> F[Substantial Completion<br/>MFO Dec 15]

    style D fill:#f96,stroke:#333
    style F fill:#f96,stroke:#333
```

In this simplified sequence, the SNET/FNLT window on "Drive Piers" and the MFO on "Substantial Completion" both act as governing constraints. If the calculated critical path (via normal logic) would finish Substantial Completion earlier than December 15, the near-critical path running through the piers activity may become critical instead once the window constraint compresses available duration—this is sometimes called a **constraint-driven critical path** versus a **logic-driven critical path**.

### Constraint Diagram (Timeline View)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 220" font-family="Arial, sans-serif">
<text x="360" y="20" text-anchor="middle" font-size="14" font-weight="bold">Constraint Window on Activity Timeline (svg_diagram)</text>
<line x1="60" y1="100" x2="660" y2="100" stroke="#333" stroke-width="2" />
<polygon points="660,100 650,95 650,105" fill="#333" />
<line x1="120" y1="90" x2="120" y2="110" stroke="#555" stroke-width="1" />
<text x="120" y="130" text-anchor="middle" font-size="11">Aug 1 (SNET)</text>
<line x1="540" y1="90" x2="540" y2="110" stroke="#555" stroke-width="1" />
<text x="540" y="130" text-anchor="middle" font-size="11">Oct 31 (FNLT)</text>
<rect x="180" y="70" width="220" height="60" fill="#ffd580" stroke="#cc8400" stroke-width="1.5" rx="4" />
<text x="290" y="105" text-anchor="middle" font-size="12" font-weight="bold">Drive Piers (Actual Duration)</text>
<rect x="120" y="80" width="60" height="40" fill="none" stroke="#aaa" stroke-dasharray="4,2" />
<text x="150" y="150" text-anchor="middle" font-size="10" fill="#888">Cannot start early</text>
<rect x="400" y="80" width="140" height="40" fill="none" stroke="#aaa" stroke-dasharray="4,2" />
<text x="470" y="150" text-anchor="middle" font-size="10" fill="#888">Cannot finish late</text>

<text x="360" y="190" text-anchor="middle" font-size="11" font-style="italic">Allowable execution window: Aug 1 – Oct 31</text>

</svg>

### Constraints in EVM Context

Imposed dates interact with Earned Value Management through the **Performance Measurement Baseline (PMB)**:

- Constrained milestones typically anchor budget time-phasing; a fixed FNLT date on a contractual milestone directly shapes the Planned Value (PV) curve, since work must be time-phased to fit within the imposed window
- If a constraint later proves unachievable, the baseline itself is affected, requiring a formal change to the PMB via the change control process rather than simply re-forecasting
- Schedule Performance Index ($SPI = EV / PV$) calculated against a constrained baseline can misrepresent true schedule health if the constraint artificially compressed or extended the planned duration—[Inference] this is a recognized practical caution in EVM literature, though exact treatment varies by organizational EVM system description (EVMS)

### Best Practices

**Key Points**

- Apply hard constraints (MSO/MFO) only to genuinely immovable dates; overuse defeats the purpose of network-based scheduling
- Prefer one-directional constraints (SNET, FNLT) over hard constraints wherever possible, since they preserve logic-driven float calculation on the unconstrained side
- Document the source and justification for every imposed date constraint (contract clause, permit number, regulatory citation) in schedule basis documentation
- Run regular "constraint audits" to identify activities with constraints that no longer reflect current conditions
- Distinguish constraints from **deadlines**: in some software (e.g., Microsoft Project), a "deadline" is a visual marker that flags lateness without altering calculated dates, whereas a true constraint changes the calculation itself
- Avoid stacking multiple constraints on a single activity without documented reason, as this can mask true logic and confuse float interpretation for other schedule users

### Common Pitfalls

- **Constraint proliferation**: Schedulers apply SNET dates to "lock in" a plan, inadvertently masking true float and creating a false sense of schedule flexibility elsewhere
- **Negative float ignored**: A hard constraint conflicting with logic produces negative float that gets overlooked because the activity still displays a "valid" date range
- **Stale constraints**: Imposed dates tied to permits or contracts that have since been renegotiated but were never updated in the schedule model
- **Confusing constraints with dependencies**: A constraint is not a substitute for a missing logic link; using an SNET date instead of properly linking a predecessor activity breaks the dynamic nature of CPM (the date won't automatically shift if the true driving activity slips)

### Related Topics

- Total Float vs. Free Float calculation methodology
- Critical Path Method forward pass and backward pass mechanics
- Baseline schedule development and Performance Measurement Baseline (PMB)
- Schedule risk analysis and Monte Carlo simulation with constrained milestones
- Contractual milestone tracking and liquidated damages exposure
- Schedule Performance Index (SPI) interpretation limitations
- Primavera P6 vs. Microsoft Project constraint-handling differences [Unverified — specific software behaviors are version-dependent]