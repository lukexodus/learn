## Interstate Pollution and Good Neighbor Obligations


### Conceptual Overview

Interstate pollution refers to environmental harm generated in one state (the "upwind" or "upstream" state) that migrates across state lines to affect air or water quality in another state (the "downwind" or "downstream" state). Because cooperative federalism statutes generally assign primary implementation responsibility to the state in which pollution originates, interstate pollution creates a structural externality problem: the upwind state's regulated entities impose costs on downwind states that have no voice in the upwind state's permitting or standard-setting decisions. The **Good Neighbor Provision** of the Clean Air Act is the principal statutory mechanism addressing this externality, though common-law nuisance and interstate compact mechanisms also play a historical and supplementary role.

$$\text{Downwind Air Quality} = f(\text{In-State Emissions}) + f(\text{Interstate Transport from Upwind Sources})$$

### The Clean Air Act Good Neighbor Provision

**Statutory Text and Structure**

CAA §110(a)(2)(D)(i)(I) (42 U.S.C. §7410(a)(2)(D)(i)(I)) requires that every State Implementation Plan (SIP) contain adequate provisions prohibiting emissions within the state in amounts that will **contribute significantly to nonattainment**, or **interfere with maintenance**, of the NAAQS in any other state. This is commonly called the "Good Neighbor Provision" or "interstate transport provision."

**Key Points**

- The obligation is **self-executing** as a SIP requirement — states must address interstate transport in their SIP submissions, not merely in-state air quality.
- The provision addresses two distinct harms: (1) preventing an upwind state from **causing** nonattainment in a downwind state, and (2) preventing an upwind state from **interfering with maintenance** of attainment already achieved by a downwind state.
- If a state fails to submit an adequate SIP addressing interstate transport, EPA may promulgate a **Federal Implementation Plan (FIP)** to fill the gap, as it has done repeatedly in the interstate transport context.

```mermaid
flowchart TD
    A[Upwind State Emissions (svg_diagram)] --> B[Interstate Transport of Pollutants]
    B --> C[Downwind State Air Quality Impact]
    C --> D{Contributes Significantly to Nonattainment or Interferes with Maintenance?}
    D -->|Yes| E[Good Neighbor Obligation Triggered - CAA 110a2Di]
    E --> F{Upwind State SIP Addresses Interstate Transport?}
    F -->|Adequate| G[EPA Approves SIP]
    F -->|Inadequate/Absent| H[EPA Promulgates Federal Implementation Plan - FIP]
    D -->|No| I[No Good Neighbor Obligation for This Pollutant/State Pair]
```

### EPA's Regulatory Implementation Mechanisms

**Key Points**

EPA has implemented the Good Neighbor Provision through successive regulatory programs, each attempting to translate the statutory "significant contribution" standard into an administrable framework, generally using a two-step analytical approach:

1. **Step 1 — Screening/Linkage**: Identify downwind monitoring sites with air quality problems (nonattainment or maintenance issues) and determine which upwind states are "linked" to those problems through modeled interstate transport contribution above a threshold.
2. **Step 2 — Quantification/Allocation**: For linked upwind states, determine the state's required emissions reductions, typically using a cost-effectiveness analysis to identify the "significant contribution" amount attributable to that state and the emissions reductions achievable through cost-effective controls.

**Major Regulatory Programs**

- **NOx SIP Call** (1998): Addressed interstate transport of nitrogen oxides contributing to downwind ozone nonattainment, primarily in the eastern United States, using a cap-and-trade mechanism among upwind states.
- **Clean Air Interstate Rule (CAIR)** (2005): Addressed interstate transport of SO2 and NOx contributing to downwind PM2.5 and ozone nonattainment. Vacated and remanded by the D.C. Circuit in *North Carolina v. EPA*, 531 F.3d 896 (2008), though left temporarily in place pending replacement due to the disruptive effect of vacatur.
- **Cross-State Air Pollution Rule (CSAPR)** (2011): EPA's replacement for CAIR, again using emissions trading budgets for SO2 and NOx among linked upwind states. Initially vacated by the D.C. Circuit but **upheld by the Supreme Court** in *EPA v. EME Homer City Generation*, 572 U.S. 489 (2014).
- **CSAPR Update** and subsequent revisions: Ongoing iterative rulemakings addressing updated NAAQS (ozone, PM2.5) and responding to remand instructions from subsequent litigation.
- **"Good Neighbor Plan"** (2023): EPA's most recent FIP addressing the 2015 ozone NAAQS, which was subject to significant litigation including Supreme Court emergency-docket review.

[Inference] Because interstate transport rules are litigated continuously and are frequently subject to partial stays, remands, and revisions in response to changing NAAQS and evolving case law, the specific states and pollutants covered by an active EPA interstate transport rule at any given time should be independently verified rather than assumed static, as this is one of the most procedurally dynamic areas of Clean Air Act implementation.

### EPA v. EME Homer City Generation (2014)

**Facts**: Industry groups and several states challenged CSAPR, arguing (1) EPA's cost-based allocation methodology exceeded its statutory authority because it did not tie each state's required reduction precisely to its own proportional contribution to downwind nonattainment, and (2) EPA impermissibly required simultaneous compliance without first giving states the opportunity to submit their own SIPs addressing interstate transport.

**Holding**: The Supreme Court upheld CSAPR, holding that:

1. EPA reasonably interpreted the ambiguous "contribute significantly" standard to permit a **cost-effectiveness-based allocation** rather than requiring a strict proportional-contribution formula, deferring to EPA's technical judgment under *Chevron* framework as it then applied.
2. EPA did not need to wait for states to fail at submitting adequate SIPs before promulgating a FIP addressing interstate transport, given the practical time constraints and the states' history of transport-related SIP deficiencies.

**Significance**: *EME Homer City* remains the leading precedent validating EPA's cost-based, trading-oriented approach to interstate transport regulation, and rejecting a rigid proportionality requirement in favor of administrable, cost-effectiveness-driven allocation.

### Common-Law and Alternative Mechanisms

**Interstate Nuisance Actions**

- Prior to and alongside statutory mechanisms, states have pursued federal common-law nuisance actions against upwind polluters, tracing to early cases like *Georgia v. Tennessee Copper Co.*, 206 U.S. 230 (1907), recognizing a state's quasi-sovereign interest in protecting its citizens' health and its territory from out-of-state pollution.
- ***American Electric Power Co. v. Connecticut***, 564 U.S. 410 (2011), held that the Clean Air Act **displaces** federal common-law nuisance claims for greenhouse gas emissions from stationary sources, because the CAA provides a comprehensive statutory and regulatory mechanism (including the Good Neighbor Provision and related tools) that occupies the same regulatory space, leaving no room for a parallel federal common-law remedy.
- [Unverified] Whether state common-law nuisance claims (as opposed to federal common law) remain available for interstate pollution harms not addressed by displacement principles continues to be litigated and may depend on choice-of-law questions regarding which state's common law governs a transboundary harm.

**CAA §126 Petitions**

- CAA §126 allows a downwind state (or affected political subdivision) to petition EPA directly, alleging that a specific major source or group of sources in an upwind state is emitting in violation of the Good Neighbor Provision, providing an alternative, source-specific enforcement pathway distinct from the broader SIP/FIP rulemaking process.

**Interstate Compacts**

- States may enter into congressionally consented interstate compacts to jointly manage shared airsheds or watersheds (e.g., regional ozone transport commissions established under CAA §184 for the Ozone Transport Region), providing a cooperative, negotiated alternative to unilateral federal regulation.

### Interstate Water Pollution

**Key Points**

- The Clean Water Act's NPDES structure similarly raises interstate transport concerns, though the CWA's Good Neighbor-style obligations are less centralized than the CAA's explicit statutory provision.
- ***International Paper Co. v. Ouellette***, 479 U.S. 481 (1987): Held that a downwind (downstream) state's common-law nuisance claims against an out-of-state point source discharger are preempted by the CWA, and that the source's compliance obligations are governed exclusively by the law of the **source state** (the state issuing the NPDES permit), not the law of the affected downstream state — reinforcing that interstate water pollution disputes are generally channeled through the CWA's permitting structure rather than parallel state tort law from the affected state.
- Downstream states retain more limited tools compared to the CAA's explicit Good Neighbor Provision: primarily participation in the source state's permitting process, EPA's oversight and veto authority over NPDES permits, and water quality standard consultation mechanisms.

### Example

A coal-fired power plant in an upwind state emits sulfur dioxide and nitrogen oxides that, through atmospheric transport, contribute to ozone and particulate matter nonattainment at monitors in a downwind state several hundred miles away. Applying the Good Neighbor framework:

1. EPA's modeling links the upwind state to the downwind nonattainment problem, exceeding the significant-contribution threshold.
2. The upwind state's SIP is found inadequate because it does not address this interstate transport contribution.
3. EPA promulgates a FIP imposing emissions budgets (potentially through a cap-and-trade allocation, consistent with the *EME Homer City* cost-effectiveness approach) on sources including this plant.
4. The downwind state additionally retains the option to file a CAA §126 petition targeting the specific plant if it believes the FIP's timeline or stringency is inadequate to redress the specific contribution.

### Comparative Framework: CAA vs. CWA Interstate Mechanisms

**Output**

| Feature | Clean Air Act | Clean Water Act |
| --- | --- | --- |
| Express statutory Good Neighbor provision | Yes — §110(a)(2)(D)(i)(I) | No direct equivalent |
| Federal backstop if state fails to address | FIP | Limited; primarily EPA permit veto/oversight |
| Source-specific petition mechanism | §126 petitions | No direct equivalent |
| Governing law for interstate common-law claims | Displaced by CAA (*AEP v. Connecticut*, greenhouse gases) | Source-state law governs (*International Paper v. Ouellette*) |
| Primary judicial gloss | *EME Homer City* — cost-effectiveness allocation upheld | *Ouellette* — preemption of affected-state nuisance law |

### Related Topics

- Federal floor and state ceiling models of regulatory design
- State Implementation Plans and Federal Implementation Plans under the Clean Air Act
- NAAQS attainment and nonattainment classifications
- *American Electric Power Co. v. Connecticut* and displacement of federal common law
- *International Paper Co. v. Ouellette* and choice-of-law in interstate water pollution
- Cap-and-trade mechanisms in Clean Air Act implementation (Acid Rain Program, CSAPR)
- Ozone Transport Region and CAA §184 interstate compacts
- Citizen suit provisions and their interaction with interstate enforcement gaps