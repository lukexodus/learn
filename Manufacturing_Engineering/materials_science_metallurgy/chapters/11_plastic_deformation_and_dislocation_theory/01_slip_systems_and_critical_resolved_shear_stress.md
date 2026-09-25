## Slip Systems and Critical Resolved Shear Stress

### Definition and Physical Basis

Plastic deformation in crystalline metals occurs predominantly by **slip**: the sliding of one crystallographic plane over an adjacent parallel plane along a specific crystallographic direction, mediated by the motion of dislocations rather than simultaneous rigid-body shear of entire atomic planes. A **slip system** is the combination of a specific **slip plane** (the plane on which sliding occurs) and a specific **slip direction** (the direction within that plane along which sliding occurs).

Slip preferentially occurs on the crystallographic planes of highest atomic packing density (close-packed planes) and along the directions of highest linear atomic density (close-packed directions), because these combinations minimize the interatomic distance dislocations must traverse and the energy barrier to slip (directly related to minimizing the Burgers vector magnitude, since dislocation energy scales with $|\mathbf{b}|^2$).

### Slip Systems by Crystal Structure

**[Key Points]**

**Face-Centered Cubic (FCC)**

- Slip plane: $\{111\}$ (close-packed planes)
- Slip direction: $\langle110\rangle$ (close-packed directions)
- Number of slip systems: 4 planes × 3 directions per plane = **12 slip systems**
- Examples: Cu, Al, Ni, Au, Ag, austenitic (γ) Fe, Pb

FCC metals generally exhibit high ductility, attributable in significant part to the large number of available slip systems, which allows deformation to be readily accommodated in polycrystalline aggregates without excessive local stress concentration (consistent with the von Mises criterion requiring at least 5 independent slip systems for arbitrary grain-shape-compatible plastic deformation).

**Body-Centered Cubic (BCC)**

- Slip plane: predominantly $\{110\}$, but also $\{112\}$ and $\{123\}$ depending on temperature and alloy — BCC metals lack a single, unambiguous close-packed plane, leading to this multiplicity.
- Slip direction: $\langle111\rangle$ (the close-packed direction in BCC)
- Number of slip systems: up to 48 when all plane families are counted, though not all are equally active under all conditions
- Examples: α-Fe (ferrite), W, Mo, Nb, V, Cr

BCC metals show pronounced temperature-dependent slip behavior: at low temperature, the effective number of easily activated slip systems is reduced (contributing to the characteristic ductile-to-brittle transition behavior of BCC ferritic steels), while at higher temperature additional slip plane families become active, increasing ductility.

**Hexagonal Close-Packed (HCP)**

- Primary slip plane: basal plane $\{0001\}$
- Slip direction: $\langle11\bar{2}0\rangle$ (close-packed direction within the basal plane)
- Number of slip systems: only **3 independent basal slip systems** for ideal HCP metals with a favorable c/a ratio, well below the 5 required by the von Mises criterion for arbitrary polycrystalline deformation
- Examples: Mg, Zn, Ti (α-phase), Zr, Co, Cd, Be

Because basal slip alone provides insufficient independent slip systems for general polycrystalline deformation, HCP metals commonly rely on additional slip systems (prismatic $\{10\bar10\}$, pyramidal $\{10\bar11\}$ or $\{11\bar22\}$ planes) and, importantly, on **mechanical twinning** to accommodate strain along the c-axis — this is why many HCP metals (Mg, Ti, Zn) exhibit markedly lower room-temperature ductility and more pronounced anisotropic/textured deformation behavior compared to FCC metals, though the specific balance of active slip and twin systems depends on the metal's c/a ratio and temperature. [Behavior may vary meaningfully among HCP metals depending on c/a ratio: metals with c/a close to the ideal value of 1.633 (e.g., Mg, c/a ≈ 1.624) favor basal slip, while those with lower c/a ratios (e.g., Ti, c/a ≈ 1.587; Zr) show comparatively greater prismatic slip activity.]

### Slip System Comparison

| Crystal Structure | Slip Plane(s) | Slip Direction | # Slip Systems | Ductility Tendency |
| --- | --- | --- | --- | --- |
| FCC | {111} | ⟨110⟩ | 12 | High |
| BCC | {110}, {112}, {123} | ⟨111⟩ | up to 48 (temperature-dependent activity) | Moderate, strongly temperature-dependent |
| HCP | {0001} (basal), plus prismatic/pyramidal | ⟨11$\bar{2}$0⟩ | 3 (basal only); more with non-basal systems active | Generally lower, anisotropic |

### Schmid's Law and Resolved Shear Stress

**[Key Points]**

An externally applied uniaxial tensile (or compressive) stress does not act directly as a shear stress on a given slip system; it must be resolved geometrically onto the slip plane and slip direction. **Schmid's Law** relates the applied axial stress $\sigma$ to the resolved shear stress $\tau_R$ acting on a specific slip system:

$$\tau_R = \sigma \cos\phi \cos\lambda$$

where:

- $\phi$ is the angle between the loading axis and the normal to the slip plane
- $\lambda$ is the angle between the loading axis and the slip direction

The product $\cos\phi\cos\lambda$ is termed the **Schmid factor** ($m$), ranging from 0 (slip system oriented such that no resolved shear stress results) to a maximum theoretical value of 0.5 (achieved when $\phi = \lambda = 45°$).

### Critical Resolved Shear Stress (CRSS)

Slip on a given system initiates only when the resolved shear stress on that system reaches a critical value characteristic of the material — the **Critical Resolved Shear Stress (CRSS, $\tau_{CRSS}$)**. This leads to the yield condition:

$$\sigma_y = \frac{\tau_{CRSS}}{m_{max}}$$

where $m_{max}$ is the Schmid factor of the most favorably oriented slip system (i.e., the system that reaches its CRSS first as applied stress increases). This equation shows directly why single-crystal yield strength is strongly orientation-dependent: the same material, loaded along different crystallographic directions, will exhibit different macroscopic yield stress values because $m_{max}$ varies with loading orientation relative to the crystal axes, even though $\tau_{CRSS}$ itself is an intrinsic material property (for a given temperature, purity, and dislocation structure).

**[Key Points]**

- CRSS is a genuine material property, largely independent of specimen orientation, though it is sensitive to temperature, strain rate, alloy composition (solid solution strengthening), and pre-existing dislocation density (strain hardening) — it is not a universal constant across different states of the same base metal.
- The condition $m = 0$ (slip plane parallel to the loading axis, or slip direction perpendicular to the loading axis) corresponds to a **hard orientation**, where no amount of applied axial stress can activate that particular slip system.
- $m = 0.5$ corresponds to the **soft orientation**, requiring the minimum applied stress to reach CRSS on that system.

### Schmid's Law Geometry Diagram

===MERMAID_DIAGRAM===

flowchart TD

A["Applied uniaxial stress, σ"] --> B["Resolve onto slip plane<br/>normal (angle φ)"]

A --> C["Resolve onto slip<br/>direction (angle λ)"]

B --> D["τ_R = σ cos(φ) cos(λ)<br/>(Schmid factor m = cosφcosλ)"]

C --> D

D --> E{"τ_R ≥ τ_CRSS?"}

E -->|No| F["No slip on this system"]

E -->|Yes| G["Slip initiates<br/>on this system"]

G --> H["σ_y = τ_CRSS / m_max<br/>(most favorably oriented system)"]



```
### Slip Geometry Illustration (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 420">
  <text x="320" y="24" text-anchor="middle" font-size="16" font-family="sans-serif" font-weight="bold">Schmid's Law Geometry (svg_diagram)</text>
  <line x1="320" y1="380" x2="320" y2="60" stroke="black" stroke-width="2" />
  <text x="330" y="60" font-size="12" font-family="sans-serif">Loading axis, σ</text>
  <ellipse cx="320" cy="220" rx="140" ry="45" fill="none" stroke="#1f77b4" stroke-width="2" transform="rotate(-20 320 220)" />
  <text x="440" y="160" font-size="12" font-family="sans-serif" fill="#1f77b4">Slip plane</text>
  <line x1="230" y1="260" x2="410" y2="180" stroke="#2ca02c" stroke-width="3" />
  <text x="415" y="180" font-size="12" font-family="sans-serif" fill="#2ca02c">Slip direction</text>
  <line x1="320" y1="220" x2="380" y2="130" stroke="#d62728" stroke-width="1.5" stroke-dasharray="4,3" />
  <text x="385" y="125" font-size="11" font-family="sans-serif" fill="#d62728">plane normal</text>
  <path d="M 320 220 A 40 40 0 0 0 350 185" fill="none" stroke="#d62728" stroke-width="1.5" />
  <text x="345" y="200" font-size="11" font-family="sans-serif" fill="#d62728">φ</text>
  <path d="M 320 220 A 55 55 0 0 0 300 265" fill="none" stroke="#2ca02c" stroke-width="1.5" />
  <text x="290" y="245" font-size="11" font-family="sans-serif" fill="#2ca02c">λ</text>
</svg>

### Worked Example: Single-Crystal Yield Stress Calculation

**[Example]** A copper single crystal has a critical resolved shear stress of $\tau_{CRSS} = 1.0$ MPa. For a particular tensile loading orientation, the slip plane normal makes an angle $\phi = 35°$ with the loading axis, and the slip direction makes an angle $\lambda = 60°$ with the loading axis. Calculate the applied tensile stress required to initiate yielding.

**Schmid factor:**
$$m = \cos\phi\cos\lambda = \cos(35°)\cos(60°) = (0.8192)(0.5000) = 0.4096$$

**Required applied stress:**
$$\sigma_y = \frac{\tau_{CRSS}}{m} = \frac{1.0\ \text{MPa}}{0.4096} \approx 2.44\ \text{MPa}$$

This applied stress of approximately 2.44 MPa is needed for this specific orientation. Note that this Schmid factor (0.41) is relatively close to the maximum possible value of 0.5, indicating a comparatively favorable ("soft") orientation for slip.

### Worked Example: Comparing Two Loading Orientations

**[Example]** Using the same crystal ($\tau_{CRSS} = 1.0$ MPa), compare the required yield stress for a second orientation where $\phi = 60°$ and $\lambda = 60°$.

$$m = \cos(60°)\cos(60°) = (0.5)(0.5) = 0.25$$

$$\sigma_y = \frac{1.0}{0.25} = 4.0\ \text{MPa}$$

This orientation requires nearly **1.6 times** the applied stress of the first example (4.0 MPa vs. 2.44 MPa) to initiate slip on the same slip system, despite both crystals having identical CRSS — directly demonstrating how single-crystal yield strength is fundamentally orientation-dependent, governed entirely by geometric resolution of stress onto the active slip system via the Schmid factor.

### Multiple Slip and Work Hardening Onset

**[Key Points]**
- **Single (easy) glide**: at the onset of yielding, deformation typically occurs primarily on the single slip system with the highest Schmid factor, producing relatively low initial work-hardening rates (Stage I hardening in single-crystal deformation curves).
- **Multiple slip**: as deformation (and consequently specimen rotation relative to the loading axis in a single-crystal tensile test) proceeds, the crystal lattice rotates toward orientations that increase the Schmid factor of secondary slip systems, eventually activating multiple systems simultaneously. This onset of multiple/duplex slip is associated with a sharp increase in work-hardening rate (Stage II hardening), attributable to dislocation interactions (forest dislocation intersection, junction formation) between the now-simultaneously-active slip systems.
- **Polycrystalline behavior**: in a polycrystalline aggregate, individual grains are constrained by their neighbors and generally cannot deform by single slip alone (a consequence of the von Mises compatibility requirement of 5 independent slip systems for arbitrary grain shape change), so multiple slip is typically active from very early in plastic deformation — a key reason polycrystalline yield and hardening behavior differs systematically from single-crystal behavior even in the same base metal.

### Factors Affecting CRSS

- **Temperature**: CRSS generally decreases with increasing temperature for FCC metals (thermally assisted dislocation motion past obstacles), while BCC metals show a more pronounced CRSS increase at low temperature associated with the thermally activated nature of screw dislocation core motion in BCC lattices — a mechanistic contributor to BCC ductile-to-brittle transition behavior.
- **Solid solution alloying**: solute atoms interact with dislocation stress fields, increasing CRSS (solid-solution strengthening), with the magnitude of increase depending on solute concentration and atomic size/modulus mismatch with the solvent lattice.
- **Strain rate**: CRSS generally increases with increasing strain rate, reflecting the reduced time available for thermally activated dislocation obstacle-bypass mechanisms.
- **Pre-existing dislocation density**: CRSS increases with increasing dislocation density (strain hardening / work hardening), since dislocation-dislocation interactions impede further dislocation motion, forming the physical basis of the Taylor hardening relationship ($\tau \propto \sqrt{\rho}$, where $\rho$ is dislocation density).

### Engineering and Metallurgical Significance

- **Texture and anisotropy prediction**: knowledge of active slip systems and their Schmid factors under different loading directions underlies crystal plasticity modeling used to predict texture evolution and resulting anisotropic mechanical behavior during metal forming.
- **Alloy design for ductility**: the number and ease of activation of independent slip systems is a primary reason FCC metals are generally favored over HCP metals when high room-temperature formability is required, directly informing alloy/crystal-structure selection in applications demanding extensive cold forming.
- **Single-crystal component design**: directionally solidified and single-crystal Ni-based superalloy turbine blades are deliberately oriented to exploit favorable (or, in some design contexts, deliberately unfavorable to suppress creep-relevant slip) Schmid factor considerations relative to the primary service stress direction.
- **Basis for continuum plasticity theory**: Schmid's Law and CRSS provide the fundamental micromechanical link between crystallography and the macroscopically observed yield criteria (Tresca, von Mises) used in conventional engineering stress analysis, even though those macroscopic criteria are typically applied without explicit reference to underlying slip system crystallography.

### Related Topics
- Dislocation theory: edge, screw, and mixed dislocations
- Taylor hardening and dislocation density-strength relationships
- Mechanical twinning as a supplementary deformation mode (especially HCP metals)
- Crystallographic texture development during forming
- Von Mises and Taylor criteria for polycrystalline plasticity compatibility
- Ductile-to-brittle transition in BCC metals
- Single-crystal superalloy processing and turbine blade design


```