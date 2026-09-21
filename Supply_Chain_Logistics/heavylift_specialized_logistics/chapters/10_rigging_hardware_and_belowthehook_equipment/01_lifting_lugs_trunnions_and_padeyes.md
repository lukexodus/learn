## Lifting Lugs, Trunnions, and Padeyes


### Overview

Lifting lugs, trunnions, and padeyes are permanently or temporarily attached lift points welded or bolted to a load to provide an engineered connection between the load and rigging (shackles, slings, or strand jack heads). They are among the most common — and most frequently mis-designed — components in heavy-lift engineering, since they concentrate the entire load path through a localized weld and plate section. Their design governs sling angle, rigging clearance, and the structural integrity of the load's attachment interface.

### Definitions and Distinctions

**Padeye**

A flat steel plate with a machined hole, welded perpendicular (or at an engineered angle) to the load's structure, through which a shackle pin or sling passes. Padeyes are the most common lift point for modules, vessels, and structural steel, generally loaded in a single plane defined by the sling/shackle direction.

**Lifting Lug**

A broader term often used interchangeably with padeye but sometimes distinguished as a plate lift point without a reinforcing cheek plate, or one designed for lighter, more localized lifts (e.g., equipment skids, small vessels, precast panels). "Lug" is also used generically for any plate-type attachment.

**Trunnion**

A cylindrical (round bar or pipe) lift point welded radially or axially to the load, engaging with a sling passed around it or a specially fabricated lifting collar/clamp. Trunnions are common on heavy cylindrical loads (pressure vessels, reactors, columns) because they distribute load around a curved bearing surface and allow the load to rotate about the trunnion axis during upending or tailing operations.

### Key Points

- **Load path criticality**: All three device types are single points of failure if under-designed; catastrophic lug failure is a leading cause of heavy-lift incidents, making design verification and NDT (non-destructive testing) mandatory for critical lifts.
- **Sling angle sensitivity**: Padeye and lug capacity is highly sensitive to the angle of applied load, both in-plane (angle from vertical) and out-of-plane (side loading). As sling angle from vertical increases, tension in the sling and the resulting load on the pin increases according to $T = \frac{W}{2\cos(\theta)}$ for a symmetric two-leg rig, where $\theta$ is the angle from vertical.
- **Out-of-plane (side) loading**: Padeyes are primarily designed for in-plane loading; significant side loading (common when the lift point must accommodate multiple non-coplanar slings) introduces bending stresses the plate was not primarily designed for and often requires cheek plates or a redesign.
- **Trunnion rotation function**: Beyond simple lifting, trunnions are frequently used as pivot points for tailing/upending operations of tall, slender loads (columns, towers), where the load rotates from horizontal to vertical using a combination of a main crane hook and a tailing crane or trunnion-mounted turning device.
- **Pin-to-hole clearance**: Shackle pin diameter versus padeye hole diameter clearance affects both bearing stress distribution and practical rigging assembly; excessive clearance concentrates bearing stress, while too little clearance makes shackle installation difficult under load.
- **Reinforcement (cheek plates)**: Doubler or cheek plates are welded to the main padeye plate near the pin hole to increase bearing area and reduce local stress concentration, particularly for higher-capacity lugs.
- **Fatigue and reuse**: Lift points intended for repeated use (e.g., standard cargo/module lift points, mobile equipment) must account for fatigue loading, whereas one-time, single-lift padeyes are typically designed to a static allowable stress with an appropriate safety factor and are sometimes cropped off after use.

### Padeye Design Components

A typical padeye assembly comprises:

1. **Main plate** — primary load-bearing plate, thickness sized for tensile, shear, and bearing stress at the pin hole
2. **Pin hole** — bored to shackle pin diameter plus engineered clearance
3. **Cheek plates** (optional) — welded doublers increasing local thickness at the hole
4. **Base/heel** — the welded connection to the parent structure, often the most critical weld in the assembly
5. **Chamfer/radius transitions** — to reduce stress concentration at geometric discontinuities

### Governing Failure Modes

| Failure Mode | Description | Typical Design Check |
| --- | --- | --- |
| Tensile failure through pin hole (net section) | Plate fails across the reduced cross-section at the hole | Net area tensile stress vs. allowable |
| Shear tear-out (behind the hole) | Plate shears along two planes behind the pin toward the plate edge | Shear area check based on edge distance |
| Bearing failure | Pin crushes/deforms the hole surface | Bearing stress = Load / (pin diameter × plate thickness) |
| Weld failure at base | Heel weld fails in shear/tension under combined load | Weld throat stress vs. allowable weld stress |
| Buckling (thin plates, compressive side loads) | Local plate buckling under out-of-plane loading | Plate slenderness and side-load capacity check |
| Fatigue cracking (reusable lugs) | Crack initiation at stress concentration points under cyclic load | S-N curve fatigue life assessment |

### Padeye Design Calculation Framework

For a padeye subjected to a sling load $P$ at angle $\theta$ from the plate's plane:

**Net section tensile stress** across the pin hole:

$$\sigma_t = \frac{P}{(W - D_h) \times t}$$

where $W$ is plate width at the hole, $D_h$ is hole diameter, and $t$ is plate thickness.

**Bearing stress** at the pin:

$$\sigma_b = \frac{P}{D_p \times t}$$

where $D_p$ is pin diameter.

**Shear tear-out** (double-plane shear behind the hole):

$$\tau = \frac{P}{2 \times L_e \times t}$$

where $L_e$ is the edge distance from the hole to the plate edge in the load direction.

Design safety factors are typically governed by project-specific lift classification. [Inference] Common industry practice applies design factors on yield strength in the range of 2–3 for standard lifts and higher (3–5+) for critical or personnel lifts, but exact factors should always be confirmed against the applicable project specification, classification society rule, or standard such as ASME BTH-1, DNV-ST-N001, or client-specific heavy-lift criteria, since these vary by industry and jurisdiction.

### Trunnion Design Considerations

Trunnions are typically analyzed as a cantilevered or simply-supported cylindrical beam under combined bending, shear, and torsion (if used for rotation under load). Key checks include:

- **Bending stress** at the weld root where the trunnion attaches to the parent structure
- **Weld capacity** — trunnions are commonly full-penetration welded given the concentrated load and rotational service
- **Bearing/contact stress** at the sling-to-trunnion interface, particularly important if a wire rope sling is wrapped directly around the trunnion barrel (minimum bend radius / D/d ratio considerations to avoid excessive wire rope wear)
- **Rotational friction** if the trunnion is intended to rotate freely during upending, sometimes requiring a low-friction bushing, sleeve, or roller-supported lifting collar rather than direct sling wrap

### Lift Point Configuration Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 420" font-family="Arial, sans-serif">
<text x="450" y="28" font-size="18" font-weight="bold" text-anchor="middle">Padeye vs Trunnion Configuration (svg_diagram)</text>


<text x="180" y="60" font-size="14" font-weight="bold" text-anchor="middle">Padeye</text>

<rect x="120" y="200" width="20" height="140" fill="#888" stroke="#333" />

<path d="M140,220 L220,220 L220,300 L180,340 L140,300 Z" fill="`#c9d6ea`" stroke="#333" stroke-width="2" />

<circle cx="185" cy="255" r="18" fill="#fff" stroke="#333" stroke-width="2" />

<circle cx="185" cy="255" r="18" fill="none" stroke="#333" stroke-width="2" />

<line x1="185" y1="255" x2="185" y2="140" stroke="#333" stroke-width="3" />

<path d="M170,150 L185,120 L200,150 Z" fill="#333" />

<text x="185" y="110" font-size="11" text-anchor="middle">Sling load P</text>

<text x="120" y="365" font-size="10" text-anchor="middle">Base/heel weld</text>

<line x1="120" y1="345" x2="140" y2="345" stroke="`#dc3545`" stroke-width="2" />

<text x="230" y="258" font-size="10">Pin hole (D_h)</text>

<text x="120" y="385" font-size="10" text-anchor="middle">Parent</text>

<text x="120" y="398" font-size="10" text-anchor="middle">structure</text>



<text x="650" y="60" font-size="14" font-weight="bold" text-anchor="middle">Trunnion</text>

<rect x="560" y="220" width="180" height="30" fill="#888" stroke="#333" />

<circle cx="650" cy="235" r="40" fill="`#c9d6ea`" stroke="#333" stroke-width="2" />

<circle cx="650" cy="235" r="40" fill="none" stroke="#333" stroke-width="3" />

<path d="M610,200 A45,45 0 0,1 690,200" fill="none" stroke="#333" stroke-width="4" />

<line x1="610" y1="200" x2="610" y2="150" stroke="#333" stroke-width="3" />

<line x1="690" y1="200" x2="690" y2="150" stroke="#333" stroke-width="3" />

<path d="M600,160 L610,130 L620,160 Z" fill="#333" />

<path d="M680,160 L690,130 L700,160 Z" fill="#333" />

<text x="650" y="120" font-size="11" text-anchor="middle">Sling wrapped around barrel</text>

<text x="650" y="290" font-size="10" text-anchor="middle">Weld to parent structure</text>

<text x="650" y="360" font-size="10" text-anchor="middle">Rotation axis (upending)</text>

<path d="M600,340 A50,15 0 1,0 700,340" fill="none" stroke="#666" stroke-width="1.5" stroke-dasharray="4,3" />

</svg>

### Rigging Interface and Sling Angle Effects

Sling angle from vertical directly multiplies the tension seen at the padeye. For a two-leg bridle lifting a load $W$:

$$T_{leg} = \frac{W}{n \times \cos(\theta)}$$

where $n$ is the number of legs sharing load equally and $\theta$ is measured from vertical. As $\theta$ approaches 90° (near-horizontal sling), tension approaches infinity — practical rigging design typically avoids sling angles less than 30–45° from horizontal (i.e., limits $\theta$ from vertical), since capacity derates sharply beyond this range. [Inference] Specific minimum angle thresholds vary by rigging standard and should be verified against project lift procedures.

### Example: Vessel Lift with Combined Padeye and Trunnion

**Scenario**: A horizontal pressure vessel requires lifting from a horizontal laydown position to vertical installation orientation ("upending"), then final set.

**Approach**:

1. **Top padeye** — positioned at the vessel's top head, engaged by the main crane hook for the primary vertical lift once upended.
2. **Bottom trunnion** — positioned near the base, engaged by a tailing crane (or a hydraulic tailing device) during the upending rotation, allowing controlled rotation about the trunnion axis as the vessel transitions from horizontal to vertical.
3. As the vessel approaches vertical, load transfers progressively from the tailing rig to the main hook, with the trunnion providing a stable rotational bearing point throughout.

**Design considerations**: Both lift points must be engineered for the full range of load vectors experienced throughout the rotation — the trunnion sees changing bending direction as the vessel angle changes, not just a single static load case.

### Verification and Quality Control

- **Non-destructive testing (NDT)**: Magnetic particle inspection (MPI) or dye penetrant testing (DPT) of welds is standard practice for critical lift points; ultrasonic testing (UT) may be used for weld volume inspection on thicker sections.
- **Proof load testing**: Some project specifications require lift points to be proof-tested at a percentage above design working load (commonly 1.25–2x SWL) [Unverified — project-specific] prior to use on a critical lift.
- **Design documentation**: Calculations should be independently checked/certified, referencing the specific applicable code (e.g., ASME BTH-1 for below-the-hook lifting devices, or DNV/relevant classification society rules for marine and offshore lifts).
- **Marking**: Rated capacity, safe working load (SWL), and orientation should be clearly stamped or stenciled on or near the lift point.

[Behavior may vary based on specific project design codes, material specifications, weld procedures, and site-specific loading conditions — always verify against the current applicable design standard and a certified lift engineering package before execution.]

### Common Design Pitfalls

- Neglecting side/out-of-plane loading when multiple slings converge non-coplanarly on a single padeye
- Insufficient edge distance behind the pin hole, leading to shear tear-out risk
- Underestimating dynamic/impact factors during pick-up (snatch loading) versus static load cases
- Inadequate weld penetration or sizing at the heel/base connection
- Reusing single-use padeyes beyond their designed fatigue life or without re-inspection
- Ignoring reduced capacity at non-vertical sling angles when planning rigging geometry

### Related Topics

- Shackle selection and pin bearing compatibility with padeye hole sizing
- Sling angle factor calculations and rigging geometry planning
- Spreader bars and lifting beams as alternatives to direct multi-leg rigging
- ASME BTH-1 design of below-the-hook lifting devices
- Non-destructive testing (NDT) methods for weld quality verification
- Upending and tailing procedures for tall/slender loads
- Dynamic amplification factors (DAF) in lift engineering
- Proof load testing procedures and documentation requirements