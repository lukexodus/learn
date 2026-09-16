## State Program Primacy and Delegation of Federal Authority


### Conceptual Overview

"Primacy" refers to the mechanism by which a state assumes primary responsibility for administering and enforcing a federal environmental program within its borders, in lieu of direct federal implementation by EPA (or another federal agency). Rather than commandeering states to implement federal law — which the Tenth Amendment's anti-commandeering doctrine forbids — cooperative federalism statutes offer states the *option* to apply for delegated authority, subject to EPA approval and continuing federal oversight. Primacy is the operational core of cooperative federalism: it transforms nominally federal regulatory programs into state-administered programs operating under a federally approved framework, while EPA retains a backstop role.

$$\text{State Program} \supseteq \text{Federal Minimum Requirements} \implies \text{EPA Approval} \rightarrow \text{Primacy Granted}$$

### Constitutional Foundation: Voluntary Cooperation, Not Commandeering

**Key Points**

- ***New York v. United States***, 505 U.S. 144 (1992): The Supreme Court held that Congress cannot compel states to enact or administer a federal regulatory program (there, low-level radioactive waste disposal); Congress can only **encourage** state participation through incentives such as conditional federal funding or conditional preemption.
- ***Printz v. United States***, 521 U.S. 898 (1997): Extended the anti-commandeering principle to bar Congress from compelling state executive officials to administer federal regulatory programs.
- **Design consequence**: Every major cooperative federalism environmental statute therefore structures state administration as **optional** — states may apply for primacy, but if they decline or fail to meet approval criteria, EPA administers the program directly in that state, ensuring the statute remains constitutionally valid encouragement rather than unconstitutional compulsion.

```mermaid
flowchart TD
    A[Federal Environmental Statute (svg_diagram)] --> B{State Elects to Seek Primacy?}
    B -->|No| C[EPA Administers Program Directly in State]
    B -->|Yes| D[State Submits Program for EPA Approval]
    D --> E{Meets Statutory Minimum Criteria?}
    E -->|No| F[EPA Denies/Returns for Revision]
    E -->|Yes| G[EPA Approves - State Assumes Primacy]
    G --> H[State Issues Permits, Enforces, Administers]
    H --> I{State Program Falls Below Federal Minimum or Fails to Enforce?}
    I -->|Yes| J[EPA May Withdraw Approval / Federal Overfiling]
    I -->|No| K[State Retains Primacy]
```

### Statutory Primacy Mechanisms

**Clean Water Act — NPDES Permitting (§402)**

- States may apply to administer the National Pollutant Discharge Elimination System (NPDES) permit program in lieu of EPA, provided the state program meets minimum statutory and regulatory requirements, including adequate enforcement authority, adequate legal authority to issue permits consistent with CWA requirements, and public participation procedures.
- Most states hold NPDES primacy; EPA retains direct implementation authority in the small number of non-delegated states and in Indian country absent separate tribal authorization.
- EPA retains **veto authority** over individual state-issued permits that fail to meet CWA requirements, and reserves enforcement authority as a backstop even in primacy states.

**Clean Air Act — State Implementation Plans (SIPs)**

- Rather than a discrete "primacy application," the CAA structures state authority around **State Implementation Plans**: EPA sets NAAQS (National Ambient Air Quality Standards) and other federal criteria, and states submit SIPs demonstrating how they will achieve and maintain compliance within their borders.
- EPA must approve, disapprove, or partially approve a SIP; if a state fails to submit an adequate SIP, EPA promulgates a **Federal Implementation Plan (FIP)** to fill the gap.
- This SIP/FIP structure functions analogously to primacy: successful SIP approval effectively grants the state primary administrative and enforcement responsibility for stationary source permitting and air quality management within federally set boundaries.

**RCRA — Hazardous Waste Program Authorization (§3006)**

- States may apply for authorization to administer the RCRA Subtitle C hazardous waste program in lieu of EPA, provided the state program is **"equivalent to," "consistent with,"** and **"no less stringent than"** the federal program.
- RCRA authorization is often **partial and incremental**: states may receive authorization for base program elements first, with subsequent authorization for specific federal rule revisions (HSWA provisions) as state law catches up to federal requirements — creating potential gaps where the state operates under its authorized (sometimes older) program while EPA's federal requirements have since been updated.

**Safe Drinking Water Act — Primary Enforcement Responsibility ("Primacy")**

- The SDWA is the statute from which the term "primacy" most directly derives; states may apply for "primary enforcement responsibility" over public water systems, requiring standards no less stringent than federal National Primary Drinking Water Regulations, adequate procedures for enforcement, and adequate record-keeping and reporting.
- Nearly all states hold SDWA primacy for public water system supervision.

**Surface Mining Control and Reclamation Act (SMCRA)**

- States may obtain "primacy" over regulation of surface coal mining operations by submitting a state regulatory program demonstrating capability to implement, administer, and enforce requirements at least as stringent as the federal program, subject to Office of Surface Mining Reclamation and Enforcement (OSMRE) approval.

### Minimum Criteria for Primacy Approval

**Key Points**

While specific statutory language varies, EPA (or the relevant delegated federal agency) generally requires a state program to demonstrate:

1. **Adequate legal authority** — state law must authorize the state agency to issue permits, set standards, and take enforcement action consistent with federal requirements.
2. **No less stringent standards** — the state program's substantive standards cannot fall below the federal floor (see related topic on floor/ceiling models).
3. **Adequate enforcement mechanisms** — meaningful civil and criminal penalty authority, inspection authority, and administrative enforcement tools.
4. **Adequate personnel and resources** — sufficient staffing, technical capacity, and funding to administer the program.
5. **Public participation procedures** — notice-and-comment procedures for permits and rulemaking comparable to federal requirements.
6. **Interstate and tribal coordination** — mechanisms to address cross-jurisdictional impacts.

### Federal Oversight and Withdrawal of Primacy

**Key Points**

- Primacy is not a one-time, irrevocable grant. Federal statutes typically authorize EPA (or the relevant agency) to **withdraw approval** of a state program if the state fails to administer it in accordance with statutory requirements, after notice and opportunity for the state to correct deficiencies.
- **Federal overfiling**: Even where a state holds primacy, EPA generally retains independent enforcement authority and may bring its own enforcement action against a violator notwithstanding the state's primacy status, particularly where EPA determines the state has failed to take timely and appropriate enforcement action. The scope of this overfiling authority and the degree of deference owed to state enforcement decisions has been the subject of ongoing litigation and varies somewhat by statute and circuit.
- **Federal grants conditioned on program maintenance**: Continued federal funding (e.g., CWA §106 grants, RCRA state grants) is often conditioned on maintaining an approved program, creating an additional financial incentive (beyond direct statutory withdrawal) for states to maintain compliance.

[Inference] The practical frequency of outright primacy withdrawal is low relative to the number of primacy states; EPA more commonly uses informal oversight tools (program reviews, corrective action agreements, memoranda of agreement) to address state program deficiencies short of formal withdrawal, though the availability of withdrawal as an ultimate backstop is a structurally important feature of the cooperative federalism design.

### Example

A state environmental agency holds NPDES primacy under the CWA. A large manufacturing facility within the state receives a discharge permit from the state agency. Two years later, EPA determines the state agency has been systematically under-enforcing permit violations at the facility, allowing repeated exceedances without penalty.

**Analysis**: EPA retains authority to (1) formally object to or veto specific future permit terms if the state agency's renewal fails to meet CWA requirements, (2) initiate its own federal enforcement action directly against the facility notwithstanding the state's primacy status (federal overfiling), and (3) in an extreme and sustained case of inadequate enforcement, initiate proceedings to withdraw the state's NPDES program approval after notice and an opportunity to correct deficiencies — though this last step is the least commonly exercised because of its disruptive effect on program administration.

### Primacy Compliance Framework

**Output**

| Program | Governing Provision | Approval Standard | Federal Backstop Mechanism |
| --- | --- | --- | --- |
| NPDES (CWA) | §402(b) | Adequate authority, no less stringent | Direct EPA administration; permit veto; overfiling |
| SIPs (CAA) | §110 | Attain/maintain NAAQS | Federal Implementation Plan (FIP) |
| Hazardous Waste (RCRA) | §3006 | Equivalent, consistent, no less stringent | Direct EPA administration; HSWA gap-filling |
| Drinking Water (SDWA) | §1413 | No less stringent than NPDWRs | Direct EPA administration |
| Surface Mining (SMCRA) | Title V | At least as stringent | OSMRE direct administration |

### Distinguishing Primacy from Related Concepts

- **Primacy vs. preemption**: Primacy is an affirmative grant of implementation authority *to* a state; preemption (particularly the ceiling model) restricts state authority *independent of* any primacy application. A state can hold primacy over a program's core structure while still being preempted from certain specific standard-setting (e.g., CWA NPDES primacy coexisting with CAA mobile-source preemption in an unrelated program).
- **Primacy vs. general state police power**: Primacy operates *within* the federal statutory and regulatory framework; it does not expand a state's independent police power beyond what the federal program authorizes, and a state cannot use its primacy status to adopt standards inconsistent with (particularly, less stringent than) federal requirements.

### Related Topics

- Federal floor and state ceiling models of regulatory design
- The Tenth Amendment anti-commandeering doctrine (*New York v. United States*, *Printz v. United States*)
- NPDES permitting procedures under the Clean Water Act
- State Implementation Plans and Federal Implementation Plans under the Clean Air Act
- RCRA Subtitle C authorization and HSWA gap-filling
- Federal overfiling and concurrent enforcement authority
- Citizen suit provisions as a check on inadequate state or federal enforcement
- Tribal primacy and treatment-as-a-state (TAS) provisions