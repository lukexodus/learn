## TSV Electrical Modeling and Keep-Out Zone Design


### Overview

TSV electrical modeling characterizes the parasitic resistance, capacitance, and inductance (RLC) that a Through-Silicon Via introduces into a signal or power path, while keep-out zone (KOZ) design defines the silicon exclusion area around each TSV needed to prevent thermo-mechanical stress from degrading nearby transistor performance. Both disciplines are essential inputs to 3D-IC physical design flows, since TSVs behave electrically unlike planar interconnect (they couple capacitively through the surrounding silicon substrate rather than a dedicated low-loss dielectric) and mechanically unlike a simple via (they induce a stress field extending measurably beyond their physical diameter).

### TSV Electrical Structure

A typical copper-filled TSV (via-middle or via-last) is modeled as a coaxial-like structure:

- **Core conductor**: copper via fill
- **Dielectric liner**: thin SiO2 layer providing electrical isolation
- **Surrounding medium**: bulk silicon substrate, which is a **lossy semiconductor**, not an ideal insulator — this is the key distinction from a conventional metal interconnect via, and the source of most TSV-specific modeling complexity

Because the surrounding silicon has finite, frequency-dependent conductivity, the TSV forms a **metal-insulator-semiconductor (MIS) structure**, similar in concept to a MOS capacitor, which introduces both a capacitive and a resistive coupling path to the substrate.

### Parasitic Resistance Modeling

#### DC Resistance

The intrinsic via resistance follows the standard resistivity relationship:

$$R = \rho \frac{L}{A}$$

where $\rho$ is the fill material's resistivity (copper, or higher-resistivity doped polysilicon for via-first TSVs), $L$ is the via length (roughly equal to substrate thickness), and $A$ is the via cross-sectional area.

#### AC Resistance and Skin Effect

At high signal frequencies, current crowds toward the via's outer surface (skin effect), increasing effective resistance above the DC value. The skin depth is:

$$\delta = \sqrt{\frac{2\rho}{\omega\mu}}$$

where $\omega$ is the angular frequency and $\mu$ is the permeability of the conductor. As via diameter approaches or exceeds several skin depths at the operating frequency, AC resistance rises measurably above DC resistance, an effect that becomes design-relevant for high-speed signaling applications (e.g., HBM-class interfaces operating in the multi-GHz range).

- **[Inference]** Because TSV diameters (commonly 1–10 µm) are generally small relative to skin depth at typical digital signaling frequencies, skin effect resistance penalties are often modest compared to the substrate coupling effects described below, though this depends on the specific via geometry, frequency of operation, and fill material.

### Parasitic Capacitance Modeling

TSV capacitance has two physically distinct components that must both be modeled:

#### Liner (Oxide) Capacitance

The capacitance across the SiO2 liner, analogous to a cylindrical capacitor:

$$C_{ox} = \frac{2\pi\varepsilon_{ox}L}{\ln(r_{via+liner}/r_{via})}$$

where $\varepsilon_{ox}$ is the liner dielectric permittivity, $L$ is via length, and the radii define the liner geometry.

#### Silicon Depletion Capacitance

Because the TSV forms an MIS structure with the surrounding silicon, a depletion region forms in the silicon at the liner-silicon interface, contributing a **voltage-dependent, bias-sensitive capacitance in series with the oxide capacitance**, exactly analogous to the depletion capacitance in a MOS capacitor:

$$C_{TSV} = \left(\frac{1}{C_{ox}} + \frac{1}{C_{dep}}\right)^{-1}$$

This series combination means total TSV capacitance is **not a fixed, bias-independent value** — it varies with the DC bias applied to the via relative to the substrate, and with substrate doping concentration, mirroring standard MOS C-V characteristics. This behavior distinguishes TSV capacitance modeling fundamentally from conventional BEOL interconnect capacitance modeling, where the surrounding dielectric is bias-independent.

### Substrate Coupling and Crosstalk

Because silicon is a lossy, finite-conductivity medium rather than an ideal insulator, **TSV-to-TSV coupling occurs partly through the substrate itself**, not just through direct electromagnetic (capacitive/inductive) coupling between adjacent vias:

- Signal energy on one TSV can couple into the substrate, propagate through the bulk silicon, and induce noise on a nearby TSV or on nearby active transistor circuitry
- This substrate-coupled noise mechanism is a well-established concern in mixed-signal and RF silicon design generally, and TSVs introduce new potential noise injection/victim points into this coupling network
- **[Inference]** Substrate coupling severity generally scales with substrate doping/resistivity, TSV pitch, and TSV depth, with denser TSV arrays at fine pitch presenting greater crosstalk risk; exact coupling coefficients require full 3D electromagnetic/substrate co-simulation rather than simple closed-form estimation, since the coupling network path is inherently three-dimensional.

### Inductance Considerations

TSV self-inductance and mutual inductance (to adjacent TSVs and return-path structures) become relevant primarily for:

- High-speed digital signaling where rise/fall times are fast enough that $L\frac{di}{dt}$ voltage drops are non-negligible
- Power delivery network (PDN) TSVs, where inductance contributes to power supply noise and simultaneous switching noise (SSN)

**[Inference]** Because TSVs are relatively short compared to typical package-level interconnect (their length is bounded by substrate thickness, commonly tens to a couple hundred microns), their self-inductance per via is generally small in absolute terms; however, dense via arrays used for power delivery may still require inductance-aware modeling to properly capture PDN impedance behavior, particularly at the resonant frequencies relevant to a given power distribution design.

### Keep-Out Zone (KOZ): Mechanical Origin

The KOZ requirement originates from **thermo-mechanical stress**, not electrical coupling. Its physical basis:

1. Copper has a substantially higher coefficient of thermal expansion (CTE) than silicon (copper CTE is roughly an order of magnitude larger than silicon's)
2. During thermal processing (anneals) and later thermal cycling in the field, this CTE mismatch causes the copper via to expand/contract differently than the surrounding silicon
3. This differential expansion induces a **radially-varying mechanical stress field** in the silicon immediately surrounding the via, extending outward from the via sidewall
4. Silicon transistor performance (carrier mobility, and hence drive current) is piezoresistive — i.e., mobility shifts under mechanical stress, following well-established piezoresistivity relationships used broadly in strain engineering (e.g., stressed-liner and embedded SiGe techniques intentionally exploit this same physical effect to boost mobility)
5. Transistors placed too close to a TSV therefore experience an **uncontrolled, position-dependent mobility shift**, which can degrade circuit timing predictability if not accounted for in design

### KOZ Design Practice

- **KOZ radius**: A specified exclusion distance from the TSV sidewall within which active transistor placement is restricted or prohibited, provided by the foundry/process design kit (PDK) as a design rule
- **[Inference]** KOZ dimensions typically scale with via diameter and depth (larger vias generally induce a larger absolute stress field), and are foundry- and process-node-specific values obtained from stress characterization (finite element modeling combined with silicon test-structure measurement); exact KOZ radii are not standardized across the industry and must be obtained from each foundry's PDK.
- Modern TSV-aware EDA place-and-route tools incorporate KOZ as a native design rule check (DRC), automatically flagging or preventing transistor placement within the exclusion radius around every TSV instance
- Some advanced flows go further with **stress-aware timing analysis**, incorporating the graded (non-binary) mobility shift as a function of distance from the TSV, rather than treating the KOZ boundary as a simple hard keep-out cutoff — since stress-induced mobility shift decays gradually with distance rather than dropping to zero abruptly at the KOZ edge

### Trade-off: KOZ Area Cost vs. Design Simplicity

- A larger, conservative KOZ simplifies timing closure (fewer transistors are exposed to variable stress) but consumes more silicon area, directly reducing achievable TSV density and overall die area efficiency
- A smaller, more aggressive KOZ (often paired with stress-aware timing analysis rather than a hard cutoff) can reclaim area but increases design and verification complexity
- **[Inference]** This area-vs-complexity trade-off is a recurring theme in TSV-dense designs such as HBM base logic dies, where TSV array density directly competes with useful logic area, making KOZ minimization an active area of process and design co-optimization; specific optimization outcomes are design- and product-specific.

### TSV Electrical Model and KOZ Cross-Section (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="30" text-anchor="middle" font-size="15" font-weight="bold" fill="#1a1a1a">TSV MIS Structure and Keep-Out Zone (svg_diagram)</text>

<circle cx="350" cy="220" r="150" fill="#f4cccc" stroke="#c00" stroke-width="1" stroke-dasharray="5,3" />
<text x="350" y="90" text-anchor="middle" font-size="10" fill="#c00">Stress-induced Keep-Out Zone (KOZ)</text>
<circle cx="350" cy="220" r="90" fill="#e8e8e8" stroke="#666" />
<text x="350" y="150" text-anchor="middle" font-size="9" fill="#666">Silicon substrate</text>
<circle cx="350" cy="220" r="55" fill="#d9d2e9" stroke="#674ea7" />
<text x="350" y="180" text-anchor="middle" font-size="8">Depletion region (C_dep)</text>
<circle cx="350" cy="220" r="40" fill="#c9daf8" stroke="#0b5394" />
<text x="350" y="205" text-anchor="middle" font-size="8">SiO2 liner (C_ox)</text>
<circle cx="350" cy="220" r="25" fill="#e69138" stroke="#333" />
<text x="350" y="224" text-anchor="middle" font-size="8" fill="#fff">Cu core</text>

<rect x="60" y="360" width="30" height="20" fill="#38761d" />
<text x="75" y="395" text-anchor="middle" font-size="9">Transistor (outside KOZ, unaffected)</text>
<rect x="360" y="65" width="30" height="20" fill="#c00" />
<text x="375" y="405" text-anchor="middle" font-size="9" fill="#c00">Transistor position at KOZ edge</text>
</svg>

**Related Topics**

- TSV formation approaches (via-first, via-middle, via-last) and their stress/electrical trade-offs
- Copper electroplating fill and its influence on via-induced stress
- Piezoresistivity and strain engineering in transistor mobility design
- 3D-IC place-and-route flows and TSV-aware DRC
- HBM base die logic-to-TSV-array co-design
- Substrate noise coupling and mixed-signal isolation techniques
- Power delivery network (PDN) modeling for TSV-based 3D-IC
- Finite element modeling (FEM) of TSV thermo-mechanical stress fields