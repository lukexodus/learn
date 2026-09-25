## Elastic Modulus and Hooke's Law

### Definition and Physical Origin

The elastic modulus quantifies a material's stiffness — its resistance to elastic (reversible) deformation under applied stress. Hooke's Law formalizes the linear proportionality between stress and strain observed in the elastic regime of most crystalline solids at small strains.

Physically, elastic modulus originates from the curvature of the interatomic (or interionic) potential energy well at the equilibrium spacing $r_0$ between atoms. The force between two atoms as a function of separation $r$ is:

$$F(r) = -\frac{dU(r)}{dr}$$

where $U(r)$ is the interatomic potential energy. Near equilibrium, the force-separation curve is approximately linear, and its slope at $r_0$ is directly proportional to the elastic modulus:

$$E \propto \left(\frac{dF}{dr}\right)_{r_0}$$

Materials with deep, steeply curved potential wells (strong, short-range bonds — e.g., covalent carbon-carbon bonds in diamond) exhibit very high moduli; materials with shallow, broad wells (weaker or longer-range bonds — e.g., van der Waals-bonded polymers) exhibit low moduli.

### Hooke's Law: Uniaxial Form

**[Key Points]**

For uniaxial loading within the elastic limit:

$$\sigma = E\varepsilon$$

where:

- $\sigma$ = engineering stress (force/original area)
- $\varepsilon$ = engineering strain (elongation/original length)
- $E$ = modulus of elasticity (Young's modulus), units of Pa (or GPa/MPa)

This is a first-order linear approximation of the true (slightly nonlinear) atomic force-displacement relationship, valid for the small-strain regime typical of engineering elastic deformation (generally $\varepsilon < 0.01$ for most metals before yielding).

**Shear form of Hooke's Law:**

$$\tau = G\gamma$$

where $\tau$ is shear stress, $\gamma$ is shear strain (engineering, i.e., angular distortion in radians), and $G$ is the shear modulus.

**Volumetric (hydrostatic) form:**

$$P = -K\frac{\Delta V}{V_0}$$

where $P$ is hydrostatic pressure, $\Delta V/V_0$ is volumetric strain, and $K$ is the bulk modulus.

### Relationships Between Elastic Constants

For an isotropic, linear elastic material, only two independent elastic constants are needed to fully describe elastic behavior; all others can be derived. Common relationships:

$$G = \frac{E}{2(1+\nu)}$$



$$K = \frac{E}{3(1-2\nu)}$$



$$E = \frac{9KG}{3K+G}$$

where $\nu$ is Poisson's ratio (typically 0.25–0.35 for metals). These relations ensure internal consistency: knowing any two of $E$, $G$, $K$, $\nu$ allows the other two to be calculated.

### Generalized Hooke's Law (3D Elasticity)

For a general triaxial stress state on an isotropic material, the strain-stress relations are:

$$\varepsilon_x = \frac{1}{E}\left[\sigma_x - \nu(\sigma_y + \sigma_z)\right]$$



$$\varepsilon_y = \frac{1}{E}\left[\sigma_y - \nu(\sigma_x + \sigma_z)\right]$$



$$\varepsilon_z = \frac{1}{E}\left[\sigma_z - \nu(\sigma_x + \sigma_y)\right]$$

with shear components decoupled from normal components in an isotropic material:

$$\gamma_{xy} = \frac{\tau_{xy}}{G}, \quad \gamma_{yz} = \frac{\tau_{yz}}{G}, \quad \gamma_{xz} = \frac{\tau_{xz}}{G}$$

In full tensorial (anisotropic) form, Hooke's Law is written using the fourth-rank stiffness tensor $C_{ijkl}$:

$$\sigma_{ij} = C_{ijkl}\,\varepsilon_{kl}$$

For general anisotropic crystals, this reduces (using Voigt notation) to a $6\times6$ stiffness matrix $C_{mn}$, with the number of independent constants depending on crystal symmetry: 21 for fully anisotropic (triclinic), 3 for cubic ($C_{11}, C_{12}, C_{44}$), and 2 for isotropic materials.

### Typical Elastic Modulus Values

| Material | E (GPa) | G (GPa) | ν |
| --- | --- | --- | --- |
| Diamond | ~1050 | ~478 | ~0.10 |
| Tungsten carbide | ~450–650 | — | ~0.22 |
| Steel (plain carbon) | ~200–210 | ~80 | ~0.30 |
| Titanium alloys | ~100–120 | ~44 | ~0.34 |
| Aluminum alloys | ~69–73 | ~26 | ~0.33 |
| Copper | ~110–130 | ~46 | ~0.34 |
| Magnesium alloys | ~44–45 | ~17 | ~0.35 |
| Alumina (Al₂O₃) | ~370–400 | — | ~0.22 |
| High-density polyethylene | ~0.8–1.4 | — | ~0.4 |
| Rubber (unfilled elastomer) | ~0.01–0.1 | — | ~0.49 |

[Values are representative ranges from standard materials science references; exact values vary with alloy composition, processing, temperature, and testing method.]

### Factors Affecting Elastic Modulus

**[Key Points]**

- **Bonding type**: Covalent > ionic > metallic > van der Waals, in general order of decreasing modulus, reflecting bond strength and directionality.
- **Temperature**: Modulus decreases with increasing temperature, since thermal expansion increases equilibrium interatomic spacing, moving the operating point to a shallower, less-curved region of the potential energy curve. This relationship is often approximated as roughly linear over moderate temperature ranges for many metals, though it becomes markedly nonlinear near the melting point.
- **Microstructure independence (largely)**: Unlike yield strength, elastic modulus is relatively insensitive to grain size, dislocation density, cold work, and most conventional heat treatments, because it reflects atomic bonding rather than defect-mediated processes. It is, however, sensitive to:
  - **Porosity**: significantly reduces effective modulus, approximately following empirical relations such as $E \approx E_0(1 - 1.9P + 0.9P^2)$ for many ceramics, where $P$ is fractional porosity. [Inference: the specific coefficients in porosity-modulus relations are empirical fits and vary by material system and porosity morphology.]
  - **Crystallographic texture**: preferred grain orientation from rolling/forming can introduce measurable directional variation in polycrystalline aggregate modulus.
  - **Second-phase content**: composite/multiphase materials follow rule-of-mixtures bounds (Voigt upper bound, Reuss lower bound) depending on phase distribution and loading direction relative to phase morphology.
- **Crystal structure and direction (anisotropy)**: In single crystals, $E$ varies substantially with crystallographic direction. For cubic metals, the directional modulus is given by:

$$\frac{1}{E_{[hkl]}} = S_{11} - 2\left(S_{11} - S_{12} - \frac{S_{44}}{2}\right)\left(\alpha^2\beta^2 + \beta^2\gamma^2 + \alpha^2\gamma^2\right)$$

where $S_{ij}$ are compliance constants and $\alpha, \beta, \gamma$ are direction cosines. Many cubic metals (e.g., Cu, Fe, Ni) exhibit maximum stiffness along $\langle111\rangle$ and minimum along $\langle100\rangle$; the degree of anisotropy is captured by the Zener anisotropy ratio $A = 2C_{44}/(C_{11}-C_{12})$, with $A = 1$ indicating isotropy.

### Rule of Mixtures for Composite/Multiphase Modulus

For a two-phase material under iso-strain (Voigt, parallel/upper bound) loading:

$$E_c = V_1 E_1 + V_2 E_2$$

Under iso-stress (Reuss, series/lower bound) loading:

$$\frac{1}{E_c} = \frac{V_1}{E_1} + \frac{V_2}{E_2}$$

where $V_1, V_2$ are volume fractions. Real composite/multiphase moduli typically fall between these two bounds depending on phase connectivity and morphology relative to the loading direction.

### Elastic Modulus Trends Diagram

===MERMAID_DIAGRAM===

flowchart TD

A["Interatomic bonding type"] --> B["Covalent<br/>(diamond, SiC)"]

A --> C["Ionic<br/>(ceramics, oxides)"]

A --> D["Metallic<br/>(structural metals)"]

A --> E["Van der Waals /<br/>secondary bonds<br/>(polymers, elastomers)"]

B --> F["Very high E<br/>(~500-1100 GPa)"]

C --> G["High E<br/>(~200-450 GPa)"]

D --> H["Moderate E<br/>(~40-220 GPa)"]

E --> I["Low E<br/>(~0.001-4 GPa)"]



```
### Force-Separation Curve Illustration (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 400">
  <text x="320" y="24" text-anchor="middle" font-size="16" font-family="sans-serif" font-weight="bold">Interatomic Force vs. Separation (svg_diagram)</text>
  <line x1="60" y1="200" x2="600" y2="200" stroke="black" stroke-width="1.5" />
  <line x1="320" y1="40" x2="320" y2="360" stroke="black" stroke-width="1.5" />
  <text x="600" y="220" text-anchor="end" font-size="13" font-family="sans-serif">Separation, r</text>
  <text x="330" y="55" font-size="13" font-family="sans-serif">Force, F (repulsive +)</text>
  <path d="M 150 360 C 220 100, 260 60, 320 200 C 380 320, 450 260, 600 210" stroke="#1f77b4" stroke-width="2.5" fill="none" />
  <circle cx="320" cy="200" r="4" fill="red" />
  <text x="330" y="195" font-size="12" font-family="sans-serif">r₀ (equilibrium spacing)</text>
  <line x1="280" y1="140" x2="360" y2="260" stroke="#2ca02c" stroke-width="2" stroke-dasharray="5,3" />
  <text x="365" y="255" font-size="12" font-family="sans-serif" fill="#2ca02c">Slope at r₀ ∝ E</text>
</svg>

### Worked Example: Composite Modulus Estimation

**[Example]** A metal matrix composite consists of 20 vol% SiC fiber ($E_f = 400$ GPa) embedded in an aluminum matrix ($E_m = 70$ GPa), with fibers aligned parallel to the loading axis (iso-strain condition).

$$E_c = V_f E_f + V_m E_m = (0.20)(400) + (0.80)(70)$$

$$E_c = 80 + 56 = 136\ \text{GPa}$$

This longitudinal modulus (Voigt/parallel bound) represents the upper-bound estimate. If loading were instead transverse to the fibers (approximated by the Reuss/series bound):

$$\frac{1}{E_c} = \frac{V_f}{E_f} + \frac{V_m}{E_m} = \frac{0.20}{400} + \frac{0.80}{70} = 0.0005 + 0.01143 = 0.01193$$

$$E_c \approx 83.8\ \text{GPa}$$

This illustrates the substantial anisotropy in modulus that fiber-reinforced composites exhibit depending on loading direction relative to reinforcement orientation.

### Worked Example: Poisson's Ratio and Shear Modulus Derivation

**[Example]** A titanium alloy has $E = 114$ GPa and $\nu = 0.34$. Calculate the shear modulus $G$.

$$G = \frac{E}{2(1+\nu)} = \frac{114}{2(1.34)} = \frac{114}{2.68} \approx 42.5\ \text{GPa}$$

This value is consistent with commonly tabulated shear moduli for titanium alloys (~40–44 GPa).

### Measurement Techniques

**[Key Points]**
- **Static tensile/compression testing**: modulus obtained from the initial linear slope of the stress-strain curve; accuracy is highly sensitive to extensometer resolution given the small strains involved.
- **Resonant ultrasound spectroscopy (RUS)** and **pulse-echo ultrasonic velocity methods**: derive $E$ and $G$ from measured longitudinal ($v_L$) and shear ($v_S$) wave velocities via:

$$E = \rho v_S^2 \frac{3v_L^2 - 4v_S^2}{v_L^2 - v_S^2}, \qquad G = \rho v_S^2$$

  These dynamic methods are generally regarded as more precise for modulus determination than static tensile testing, since they avoid compliance and alignment errors inherent to mechanical load frames, though results can differ slightly from static values due to strain-rate and amplitude effects. [Inference: the magnitude of static-dynamic modulus discrepancy is material- and test-condition-dependent.]
- **Nanoindentation**: extracts reduced modulus from unloading curve stiffness, useful for thin films, coatings, and localized/microstructural modulus mapping.

### Deviations from Ideal Hookean Behavior

- **Elastic nonlinearity at larger strains**: real force-separation curves are only locally linear near $r_0$; at larger elastic strains (approached in some ceramics and elastomers), stress-strain response deviates measurably from linear Hookean behavior.
- **Anelasticity**: time-dependent (but still fully recoverable) elastic strain response, distinct from pure instantaneous elasticity, arising from mechanisms such as stress-induced ordering or grain boundary relaxation.
- **Viscoelasticity in polymers**: polymers frequently show a combined elastic-viscous response (time- and rate-dependent modulus), requiring viscoelastic models (Maxwell, Kelvin-Voigt) rather than simple Hookean elasticity.

### Related Topics
- Anisotropic elasticity and the stiffness tensor $C_{ij}$ for crystal systems
- Interatomic bonding and potential energy curves (Lennard-Jones, Morse potentials)
- Composite modulus prediction (Halpin-Tsai, Voigt-Reuss-Hill bounds)
- Dynamic mechanical analysis (DMA) and viscoelastic modulus (storage/loss modulus)
- Nanoindentation and thin-film mechanical characterization
- Temperature dependence of elastic constants near melting point
- Yield strength and plastic deformation mechanisms (contrast with elastic modulus microstructure-insensitivity)


```