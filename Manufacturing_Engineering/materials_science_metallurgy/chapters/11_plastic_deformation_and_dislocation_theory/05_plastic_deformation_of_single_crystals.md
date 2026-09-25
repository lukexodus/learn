## Plastic Deformation of Single Crystals


### Overview and Significance

Plastic deformation of single crystals represents the simplest, most fundamental experimental and theoretical system for studying crystal plasticity, since it isolates the intrinsic crystallographic and dislocation-mechanistic response of a material without the complicating influence of grain boundaries, grain-to-grain compatibility constraints, or crystallographic texture that dominate polycrystalline behavior. Single-crystal deformation studies underlie much of the foundational framework (Schmid's Law, CRSS, work-hardening stages) later extended to explain polycrystalline plasticity.

### The Single-Crystal Tensile Test

**[Key Points]**

When a single crystal is deformed in uniaxial tension, the specimen is free to change shape (unlike a constrained grain within a polycrystal), and deformation proceeds by slip on the crystallographically favored system(s) as governed by Schmid's Law and the critical resolved shear stress (CRSS). As slip proceeds, two important geometric effects occur:

- **Lattice rotation**: as the specimen elongates via slip, the crystal lattice progressively rotates relative to the fixed loading axis, because the slip plane itself must remain approximately parallel to the specimen's elongating axis geometry, causing the slip plane normal and slip direction to rotate toward the loading axis.
- **Cross-sectional shape change**: single crystals can deform into markedly non-cylindrical (elliptical or otherwise irregular) cross-sections during tensile testing, since slip is confined to specific crystallographic planes rather than distributing deformation isotropically, unlike the more geometrically uniform necking typically observed in polycrystalline specimens.

### The Three Stages of Single-Crystal Work Hardening

**[Key Points]**

The stress-strain (or, more commonly for single crystals, resolved shear stress vs. shear strain) curve of an FCC single crystal deformed in tension characteristically exhibits three distinct stages:

**Stage I — Easy Glide**

Following initial yield (at $\tau = \tau_{CRSS}$ on the most favorably oriented, primary slip system), deformation proceeds predominantly by slip on this single primary system. Because only one slip system is significantly active, dislocations can travel relatively long distances with comparatively few obstacles, resulting in a low work-hardening rate — Stage I is characterized by an approximately linear region with a shallow slope, often only a few times the shear modulus divided by a large numerical factor (i.e., a hardening rate that is a small fraction of what is observed in subsequent stages).

**Stage II — Linear Hardening**

As deformation and the associated lattice rotation proceed, the Schmid factor of a secondary slip system increases (while that of the primary system may correspondingly change), eventually bringing the secondary system to its own CRSS and activating **multiple (duplex) slip**. Once multiple slip systems operate simultaneously, dislocations on intersecting slip planes interact strongly — forming sessile dislocation junctions (e.g., Lomer-Cottrell locks in FCC metals), forest dislocation intersections, and other obstacles — causing a sharp, roughly constant increase in work-hardening rate. Stage II typically shows a substantially higher and more linear hardening rate than Stage I, often cited as roughly $G/300$ to $G/200$ for many FCC metals as a representative order of magnitude. [Inference: the specific numerical hardening rate in Stage II varies measurably with crystal orientation, purity, temperature, and the specific metal, so any single quoted value should be understood as a representative order-of-magnitude figure rather than a universal constant.]

**Stage III — Dynamic Recovery**

At higher strains, the work-hardening rate begins to decrease (the curve becomes concave, bending over from the linear Stage II slope) as **dynamic recovery** mechanisms become active — cross-slip of screw dislocations allows some dislocations to bypass obstacles and annihilate with dislocations of opposite sign on nearby parallel planes, partially offsetting the ongoing increase in dislocation density from continued deformation. The onset stress of Stage III is temperature- and strain-rate-dependent (since cross-slip is thermally activated), decreasing as temperature increases or strain rate decreases — meaning Stage III onset occurs at progressively lower strain as temperature is raised, a direct consequence of easier thermally-assisted cross-slip at higher temperature.

### Three-Stage Hardening Curve Diagram

===MERMAID_DIAGRAM===

flowchart LR

A["Yield<br/>(τ = τ_CRSS on<br/>primary system)"] --> B["Stage I: Easy Glide<br/>single slip system,<br/>low hardening rate"]

B --> C["Lattice rotation increases<br/>secondary system Schmid factor"]

C --> D["Stage II: Linear Hardening<br/>multiple slip active,<br/>forest dislocation interactions,<br/>high constant hardening rate"]

D --> E["Cross-slip becomes<br/>thermally activated"]

E --> F["Stage III: Dynamic Recovery<br/>cross-slip-assisted annihilation,<br/>decreasing hardening rate"]



```
### Single-Crystal Hardening Curve Schematic (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 420">
  <text x="320" y="24" text-anchor="middle" font-size="16" font-family="sans-serif" font-weight="bold">Single-Crystal Resolved Shear Stress-Strain Curve (svg_diagram)</text>
  <line x1="70" y1="360" x2="600" y2="360" stroke="black" stroke-width="2" />
  <line x1="70" y1="360" x2="70" y2="40" stroke="black" stroke-width="2" />
  <text x="335" y="395" text-anchor="middle" font-size="14" font-family="sans-serif">Resolved shear strain, γ</text>
  <text x="25" y="200" text-anchor="middle" font-size="14" font-family="sans-serif" transform="rotate(-90 25 200)">Resolved shear stress, τ</text>
  <path d="M 70 360 L 130 300" stroke="#1f77b4" stroke-width="2.5" fill="none" />
  <path d="M 130 300 L 260 265" stroke="#2ca02c" stroke-width="2.5" fill="none" />
  <path d="M 260 265 L 430 130" stroke="#d62728" stroke-width="2.5" fill="none" />
  <path d="M 430 130 Q 520 90 580 75" stroke="#9467bd" stroke-width="2.5" fill="none" />
  <text x="90" y="290" font-size="12" font-family="sans-serif" fill="#1f77b4">Yield (τ_CRSS)</text>
  <text x="150" y="330" font-size="12" font-family="sans-serif" fill="#2ca02c">Stage I: Easy glide</text>
  <text x="290" y="220" font-size="12" font-family="sans-serif" fill="#d62728">Stage II: Linear hardening</text>
  <text x="450" y="105" font-size="12" font-family="sans-serif" fill="#9467bd">Stage III: Dynamic recovery</text>
</svg>

### Orientation Dependence of Single-Crystal Behavior

**[Key Points]**
- The initial yield stress, the extent of Stage I (easy glide), and the strain at which multiple slip and Stage II onset occur are all strongly dependent on the initial crystal orientation relative to the loading axis, since orientation directly determines the initial Schmid factors of all available slip systems.
- Crystals oriented with the loading axis along a **high-symmetry direction** (e.g., $\langle100\rangle$ or $\langle111\rangle$ in cubic crystals) may have multiple slip systems with equal, high Schmid factors from the very onset of loading, resulting in immediate multiple slip and a greatly reduced or entirely absent Stage I — such crystals proceed almost directly into Stage-II-like hardening behavior.
- Crystals oriented near the center of the standard stereographic triangle (away from high-symmetry poles) typically show the most extended and clearly defined Stage I easy-glide behavior, since a single slip system's Schmid factor advantage over competing systems persists over a larger range of lattice rotation.

### Worked Example: Lattice Rotation Toward Multiple Slip

**[Example]** An FCC single crystal is initially oriented such that the primary slip system has a Schmid factor of $m_1 = 0.48$ and a secondary slip system has $m_2 = 0.30$, with $\tau_{CRSS} = 1.0$ MPa identical for both systems (a reasonable approximation for a single-phase, chemically homogeneous crystal). Estimate the applied stress at which slip initiates on the primary system, and comment qualitatively on why continued deformation eventually activates the secondary system despite its initially lower Schmid factor.

**Applied stress for primary system yield:**
$$\sigma_y = \frac{\tau_{CRSS}}{m_1} = \frac{1.0}{0.48} \approx 2.08\ \text{MPa}$$

At this applied stress, the resolved shear stress on the secondary system is only $\tau_2 = \sigma_y \times m_2 = 2.08 \times 0.30 \approx 0.625$ MPa — well below its CRSS of 1.0 MPa, so the secondary system remains inactive and Stage I (easy glide on the primary system alone) proceeds.

As primary slip continues, the specimen elongates and the lattice progressively rotates such that the primary slip direction rotates toward the loading axis (reducing $m_1$ over time) while the secondary system's geometry typically rotates in the opposite sense, increasing $m_2$. Deformation continues in Stage I until the rotating $m_2$ increases (and/or the required applied stress for continued primary slip increases due to hardening) sufficiently that $\tau_2$ reaches $\tau_{CRSS}$, at which point Stage II (duplex slip) begins. [This qualitative rotation behavior is a well-established general feature of single-crystal deformation; the precise strain at which crossover to duplex slip occurs depends on the specific initial orientation and the detailed rotation kinematics, which require full crystallographic tracking to determine quantitatively for a given case.]

### Effect of Crystal Structure on Single-Crystal Deformation Character

**[Key Points]**
- **FCC single crystals**: exhibit the clearest and most extensively studied three-stage hardening behavior described above, owing to the relatively large number of available slip systems (12) and generally moderate-to-high stacking fault energies (in metals like Al, Cu, Ni) that permit significant cross-slip-mediated Stage III recovery.
- **BCC single crystals**: often show more complex, less clearly delineated hardening stages, additional temperature sensitivity (since screw dislocation core structure and mobility in BCC metals is itself strongly temperature-dependent), and sometimes asymmetric slip behavior (differences in CRSS depending on the sense of applied shear on a given plane) — a distinctive complication less commonly significant in FCC metals.
- **HCP single crystals**: show pronounced orientation sensitivity due to the strongly anisotropic availability of slip systems (dominant basal slip vs. much higher-CRSS non-basal systems), such that crystals oriented for easy basal slip deform very differently (often at much lower stress, with limited hardening before extensive twinning or fracture) than crystals oriented such that basal slip is geometrically suppressed (hard orientation, $m \approx 0$ for basal slip), which instead requires activation of higher-CRSS prismatic or pyramidal slip, or twinning, to accommodate deformation at all.

### Relationship to Polycrystalline Deformation

**[Key Points]**
- Polycrystalline yield and flow stress can be understood, in an approximate averaging sense, as arising from an aggregate of differently oriented single crystals (grains), each individually constrained by Schmid's Law on its own slip systems but additionally constrained by the requirement of maintaining compatibility (no gaps or overlaps) with neighboring grains — this compatibility constraint is why individual grains in a polycrystal generally cannot deform by single slip alone and instead engage multiple slip systems from very early in deformation (directly related to the von Mises 5-independent-slip-system requirement).
- The **Taylor factor** ($M$), an average orientation factor analogous to but distinct from the single-crystal Schmid factor, is used to relate polycrystalline yield stress to CRSS in an averaged sense: $\sigma_y \approx M\tau_{CRSS}$, with $M \approx 3.06$ commonly cited for random-texture FCC polycrystals (compared to the single-crystal maximum Schmid factor of 0.5, corresponding to $1/m = 2.0$) — the higher Taylor factor reflects the additional constraint imposed by grain-to-grain compatibility requirements not present in unconstrained single-crystal deformation. [Inference: the specific Taylor factor value depends on the assumed grain interaction model (Taylor/Sachs/self-consistent) and the actual crystallographic texture present; 3.06 is a commonly cited value for the fully constrained Taylor model applied to random-texture FCC metals specifically.]
- Single-crystal studies of Stage I–III hardening behavior, while not directly transferable in a quantitative sense to polycrystalline stress-strain curves (since polycrystals engage multiple slip from the start and lack a true Stage I), nonetheless provide the essential underlying dislocation-mechanistic basis (forest hardening, cross-slip-mediated dynamic recovery) used to interpret and model polycrystalline work-hardening behavior.

### Experimental and Practical Applications

- **Fundamental dislocation mechanics research**: single-crystal deformation studies remain a primary experimental tool for isolating and quantifying specific dislocation interaction mechanisms (forest hardening coefficients, cross-slip activation parameters) without the confounding averaging effects of polycrystalline grain interactions.
- **Single-crystal turbine blade design**: directionally solidified/single-crystal Ni-based superalloy turbine blades are deliberately manufactured without grain boundaries specifically to exploit favorable single-crystal creep and fatigue resistance (grain boundaries being preferential sites for creep cavitation and crack initiation at high temperature), with blade crystallographic orientation ($\langle001\rangle$ typically aligned along the blade axis) deliberately selected based on single-crystal elastic and slip-system Schmid-factor considerations relative to the primary service stress direction.
- **Semiconductor and electronic materials processing**: single-crystal silicon and other semiconductor materials require careful control of dislocation-mediated plastic deformation (or, more often, its avoidance) during crystal growth and wafer processing, drawing directly on single-crystal slip system and CRSS concepts even though these materials are covalently bonded rather than metallic.
- **Crystal plasticity finite element (CPFE) model validation**: single-crystal mechanical test data provides essential calibration and validation benchmarks for the constitutive slip-system-level parameters (CRSS values, hardening law coefficients) used as inputs to crystal plasticity models subsequently applied to predict polycrystalline behavior.

### Related Topics
- Slip systems and critical resolved shear stress (Schmid's Law)
- Dislocation glide and climb mechanisms
- Dislocation multiplication and Frank-Read sources
- Taylor factor and polycrystalline yield stress averaging models
- Single-crystal superalloy processing (directional solidification)
- Crystal plasticity finite element (CPFE) modeling
- Deformation by twinning


```