## Poisson's Ratio and Elastic Constants

### Definition and Physical Basis

Poisson's ratio ($\nu$) quantifies the ratio of transverse (lateral) strain to axial (longitudinal) strain when a material is elastically deformed under uniaxial stress:

$$\nu = -\frac{\varepsilon_{lateral}}{\varepsilon_{axial}}$$

The negative sign accounts for the typical behavior of most materials: axial tension produces lateral contraction (negative lateral strain), and axial compression produces lateral expansion, making the ratio of the two positive for ordinary materials. Physically, this arises because elastic deformation at constant or near-constant volume requires the material to compensate for axial extension by contracting in the perpendicular directions.

### Theoretical Bounds

For an isotropic, linear elastic, thermodynamically stable material, Poisson's ratio is theoretically bounded:

$$-1 \leq \nu \leq 0.5$$

- $\nu = 0.5$ corresponds to a perfectly incompressible material (no volume change under elastic deformation) — this limit is approached by rubbers and elastomers ($\nu \approx 0.49$–$0.4999$).
- $\nu = 0$ corresponds to a material with no lateral contraction under axial load (e.g., cork approximates this behavior, $\nu \approx 0$).
- $\nu < 0$ defines **auxetic materials**, which counterintuitively expand laterally under axial tension. These are typically engineered cellular/foam structures with specific re-entrant geometries rather than conventional dense solids, though some natural crystalline materials exhibit auxetic behavior along specific crystallographic directions.

Most conventional structural metals fall within a narrower practical range of $\nu \approx 0.25$–$0.35$.

### Typical Values by Material Class

| Material | Poisson's Ratio (ν) |
| --- | --- |
| Cork | ~0.00 |
| Beryllium | ~0.03–0.10 |
| Concrete | ~0.15–0.20 |
| Ceramics (alumina, SiC) | ~0.17–0.25 |
| Glass | ~0.20–0.27 |
| Cast iron | ~0.21–0.26 |
| Steel (structural) | ~0.27–0.30 |
| Titanium alloys | ~0.31–0.34 |
| Aluminum alloys | ~0.32–0.34 |
| Copper | ~0.33–0.36 |
| Magnesium alloys | ~0.35 |
| Lead | ~0.44 |
| Rubber/elastomers | ~0.48–0.4999 |

[Representative ranges from standard references; specific alloy composition, processing, and testing conditions cause variation within these ranges.]

### Relationship to Other Elastic Constants

**[Key Points]**

For an isotropic material, only two independent elastic constants fully define elastic behavior. Poisson's ratio links Young's modulus ($E$), shear modulus ($G$), and bulk modulus ($K$):

$$G = \frac{E}{2(1+\nu)}$$



$$K = \frac{E}{3(1-2\nu)}$$



$$\nu = \frac{3K - 2G}{2(3K+G)}$$



$$E = 2G(1+\nu) = 3K(1-2\nu)$$

These relationships mean that specifying any two of $\{E, G, K, \nu\}$ determines the other two, provided the material is isotropic. Notably, as $\nu \to 0.5$, the bulk modulus expression shows $K \to \infty$, consistent with the physical requirement of infinite resistance to volume change in a perfectly incompressible material.

### Derivation Context: Generalized Hooke's Law

Poisson's ratio enters directly into the 3D (triaxial) elastic strain-stress relations for an isotropic material:

$$\varepsilon_x = \frac{1}{E}\left[\sigma_x - \nu(\sigma_y + \sigma_z)\right]$$



$$\varepsilon_y = \frac{1}{E}\left[\sigma_y - \nu(\sigma_x + \sigma_z)\right]$$



$$\varepsilon_z = \frac{1}{E}\left[\sigma_z - \nu(\sigma_x + \sigma_y)\right]$$

This shows explicitly how stress applied along one axis induces strain contributions (via $\nu$) in the perpendicular directions — the mechanistic basis of the Poisson effect in multiaxial stress states.

### Volumetric Strain and Poisson's Ratio

For small elastic strains under uniaxial loading, the volumetric strain is:

$$\frac{\Delta V}{V_0} \approx \varepsilon_x(1 - 2\nu)$$

This directly shows why $\nu = 0.5$ eliminates volumetric change under uniaxial elastic loading (perfect incompressibility), while $\nu < 0.5$ permits some volume increase under axial tension.

### Anisotropic Materials: Beyond a Single Poisson's Ratio

**[Key Points]**

For anisotropic materials (single crystals, fiber-reinforced composites, textured polycrystals), a single scalar Poisson's ratio is insufficient. Multiple independent Poisson's ratios ($\nu_{ij}$) exist, each describing lateral strain in direction $j$ due to load applied in direction $i$:

$$\nu_{ij} = -\frac{\varepsilon_j}{\varepsilon_i} \quad \text{(load applied along } i\text{)}$$

For orthotropic materials (e.g., unidirectional fiber composites), the reciprocal (Maxwell-Betti) relation applies:

$$\frac{\nu_{ij}}{E_i} = \frac{\nu_{ji}}{E_j}$$

This ensures the compliance matrix remains symmetric, a thermodynamic requirement (strain energy must be a well-defined state function). For cubic crystals, the number of independent elastic constants reduces to three ($C_{11}$, $C_{12}$, $C_{44}$), from which direction-dependent effective Poisson's ratios can be computed, and these can differ substantially from the polycrystalline average value reported in handbooks.

### The Full Isotropic Elastic Constant Set

===MERMAID_DIAGRAM===

flowchart TD

A["Any 2 of: E, G, K, ν"] --> B["Fully defines isotropic<br/>elastic behavior"]

B --> C["E: Young's modulus<br/>(uniaxial stiffness)"]

B --> D["G: Shear modulus<br/>(shape distortion resistance)"]

B --> E["K: Bulk modulus<br/>(volumetric compressibility)"]

B --> F["ν: Poisson's ratio<br/>(lateral/axial strain ratio)"]

C -.relation.-> D

C -.relation.-> E

D -.relation.-> F

E -.relation.-> F



```
### Worked Example: Deriving K and G from E and ν

**[Example]** A nickel-based superalloy has $E = 205$ GPa and $\nu = 0.31$. Calculate the shear modulus $G$ and bulk modulus $K$.

**Shear modulus:**
$$G = \frac{E}{2(1+\nu)} = \frac{205}{2(1.31)} = \frac{205}{2.62} \approx 78.2\ \text{GPa}$$

**Bulk modulus:**
$$K = \frac{E}{3(1-2\nu)} = \frac{205}{3(1 - 0.62)} = \frac{205}{3(0.38)} = \frac{205}{1.14} \approx 179.8\ \text{GPa}$$

These values are consistent with typical nickel superalloy handbook data (G ≈ 75–80 GPa, K ≈ 165–180 GPa), confirming internal consistency of the isotropic elastic relations.

### Worked Example: Lateral Strain Under Axial Load

**[Example]** A cylindrical aluminum rod ($E = 70$ GPa, $\nu = 0.33$) with diameter $d_0 = 20\ \text{mm}$ is subjected to an axial tensile stress of 140 MPa. Determine the change in diameter.

**Axial strain:**
$$\varepsilon_{axial} = \frac{\sigma}{E} = \frac{140\times10^6}{70\times10^9} = 2.0\times10^{-3}$$

**Lateral strain:**
$$\varepsilon_{lateral} = -\nu\,\varepsilon_{axial} = -(0.33)(2.0\times10^{-3}) = -6.6\times10^{-4}$$

**Diameter change:**
$$\Delta d = \varepsilon_{lateral} \times d_0 = (-6.6\times10^{-4})(20\ \text{mm}) = -0.0132\ \text{mm}$$

The rod's diameter decreases by approximately 13.2 μm under this axial tensile load — a small but measurable lateral contraction consistent with the Poisson effect.

### Physical and Microstructural Influences

**[Key Points]**
- **Bonding character**: Materials with more isotropic, non-directional bonding (metallic bonding) tend toward moderate Poisson's ratios (~0.3); materials with strong directional covalent bonding (diamond, SiC, many ceramics) tend toward lower Poisson's ratios (~0.1–0.2) since bond angle stiffness restricts easy lateral relaxation.
- **Porosity**: Increasing porosity in ceramics and sintered materials generally decreases the effective Poisson's ratio, since void collapse provides an additional low-resistance pathway for volume accommodation that does not require lateral solid-phase contraction. [Inference: quantitative porosity-ν relationships are material- and pore-morphology-specific empirical correlations rather than universal laws.]
- **Temperature**: Poisson's ratio in metals typically shows only mild temperature dependence compared to $E$, though the ratio $G/K$ (and hence effective $\nu$) can shift measurably near phase transformations or as diffusional/anelastic relaxation mechanisms activate at elevated temperature.
- **Plastic deformation regime**: Once a material yields, the "effective Poisson's ratio" describing total (elastic + plastic) strain approaches 0.5, since plastic deformation in metals occurs at essentially constant volume (dislocation glide is a shape-changing, not volume-changing, process). This is distinct from the elastic Poisson's ratio and is a common point of confusion in stress analysis of yielded components.

### Engineering Significance

- **Pressure vessel and pipe design**: Poisson's ratio governs the coupling between hoop and axial strains under internal pressure, directly affecting stress analysis (e.g., end-cap effects, Poisson expansion coupling in thin-walled cylinder theory).
- **Seismic and geotechnical applications**: $\nu$ derived from P-wave and S-wave velocities is used to characterize subsurface material properties, since $\nu = f(v_P/v_S)$.
- **Composite and auxetic material design**: Engineered negative-Poisson's-ratio (auxetic) structures are used in impact-absorbing padding, medical stents, and fasteners, exploiting their tendency to "clamp" or thicken under tension rather than thin out.
- **Finite element analysis (FEA)**: An accurate $\nu$ is essential input for elastic constitutive models; incorrect $\nu$ specifically affects predicted multiaxial stress states and contact pressure distributions even when $E$ is correctly specified, since it controls the coupling terms in the compliance matrix.

### Related Topics
- Generalized Hooke's Law and the isotropic elastic compliance/stiffness matrix
- Anisotropic elasticity and the stiffness tensor for crystal systems (cubic, hexagonal, orthotropic)
- Auxetic (negative Poisson's ratio) material design and re-entrant lattice structures
- Ultrasonic elastic constant determination via wave velocity measurement
- Plastic incompressibility and the von Mises yield criterion
- Composite laminate theory and orthotropic Poisson's ratio reciprocity relations
- Pressure vessel design and biaxial/triaxial stress state analysis


```