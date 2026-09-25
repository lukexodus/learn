## Stress Strain Relationships


### Definition and Scope

Stress-strain relationships describe the mathematical and physical connection between the applied mechanical load (normalized as stress) and the resulting deformation (normalized as strain) in a material. These relationships form the foundation for predicting elastic response, yielding, plastic flow, fracture, and design allowables in structural and mechanical engineering applications of metals, ceramics, and polymers.

### Fundamental Definitions

**Stress**

Stress ($\sigma$) is force per unit area, expressed as:

$$\sigma = \frac{F}{A_0}$$

where $F$ is applied force and $A_0$ is the original cross-sectional area (engineering stress) or the instantaneous cross-sectional area $A_i$ (true stress, $\sigma_T = F/A_i$).

Stress states are classified as:

- **Normal (axial) stress**: force perpendicular to the surface (tensile or compressive).
- **Shear stress** ($\tau$): force parallel to the surface, $\tau = F_s/A_0$.

**Strain**

Strain ($\varepsilon$) is the normalized deformation:

$$\varepsilon = \frac{\Delta l}{l_0} = \frac{l - l_0}{l_0}$$

(engineering strain), where $l_0$ is original length and $l$ is instantaneous length.

**True strain** accounts for the continuously changing gauge length during deformation:

$$\varepsilon_T = \int_{l_0}^{l} \frac{dl}{l} = \ln\left(\frac{l}{l_0}\right)$$

**Shear strain** ($\gamma$) is the tangent of the angular distortion produced by shear stress.

### Engineering vs. True Stress-Strain

For a specimen under uniaxial tension with negligible volume change (a good approximation prior to necking, assuming plastic incompressibility):

$$\sigma_T = \sigma(1 + \varepsilon)$$



$$\varepsilon_T = \ln(1 + \varepsilon)$$

These conversions are valid only up to the onset of necking; beyond that point, the assumption of uniform deformation breaks down and true stress must be computed from the actual (reduced) cross-sectional area at the neck, which requires direct measurement rather than the formula above. [Inference: the exact point of divergence and the magnitude of correction needed depends on the specific material's necking behavior and is typically determined experimentally rather than from a universal formula.]

### The Elastic Region: Hooke's Law

**Linear elastic response**

At sufficiently low stress, most crystalline engineering materials exhibit a linear, reversible relationship between stress and strain, governed by Hooke's Law:

$$\sigma = E\varepsilon$$

where $E$ is the modulus of elasticity (Young's modulus), a material property reflecting interatomic bonding stiffness. Typical values: $E_{steel} \approx 200$ GPa, $E_{Al} \approx 70$ GPa, $E_{Ti} \approx 110$ GPa, $E_{polymers} \approx 0.01$–$4$ GPa.

For shear loading, the analogous relationship is:

$$\tau = G\gamma$$

where $G$ is the shear modulus.

**Poisson's ratio**

Axial elastic deformation is accompanied by lateral contraction (or expansion under compression), quantified by Poisson's ratio:

$$\nu = -\frac{\varepsilon_{lateral}}{\varepsilon_{axial}}$$

Typical metallic values: $\nu \approx 0.30$–$0.35$. For an isotropic linear elastic solid, $E$, $G$, and $\nu$ are related by:

$$G = \frac{E}{2(1+\nu)}$$

**Generalized Hooke's Law (multiaxial elasticity)**

For a general 3D stress state in an isotropic material, the elastic strain components are:

$$\varepsilon_x = \frac{1}{E}\left[\sigma_x - \nu(\sigma_y + \sigma_z)\right]$$

with analogous expressions for $\varepsilon_y$, $\varepsilon_z$, capturing the coupling between orthogonal stress and strain components via Poisson contraction.

**Bulk modulus**

Under hydrostatic loading, volumetric strain relates to pressure via the bulk modulus $K$:

$$K = \frac{E}{3(1-2\nu)}$$

**[Key Points]**

- $E$, $G$, $K$, and $\nu$ are not independent — any two fully define isotropic elastic behavior.
- Elastic modulus is governed by the interatomic bonding force-distance curve curvature at the equilibrium spacing; it is largely insensitive to microstructure (grain size, heat treatment, cold work) in a given alloy, unlike yield strength.
- Modulus decreases with increasing temperature as atomic bonding weakens and interatomic spacing increases.

### The Elastic-Plastic Transition: Yielding

**Yield point (ferrous alloys)**

Low-carbon steels often exhibit a distinct upper and lower yield point, followed by a Lüders strain plateau of heterogeneous deformation (Lüders bands) before uniform strain hardening resumes. This behavior arises from dislocation unpinning from interstitial (carbon/nitrogen) atmospheres (Cottrell atmospheres).

**0.2% Offset yield strength**

Most metals (aluminum, many steels beyond the Lüders regime, titanium, etc.) show a gradual transition from elastic to plastic behavior without a distinct yield point. The **0.2% offset method** is the standard convention: a line parallel to the linear elastic slope is drawn from $\varepsilon = 0.002$, and its intersection with the stress-strain curve defines the offset yield strength ($\sigma_{0.2}$).

### The Plastic Region: Strain Hardening

**Hollomon (power-law) relationship**

Beyond yielding, many metals exhibit a true stress-true strain relationship well approximated by:

$$\sigma_T = K \varepsilon_T^{\,n}$$

where $K$ is the strength coefficient and $n$ is the strain-hardening exponent. Higher $n$ indicates greater capacity for uniform strain distribution/hardening before instability, correlating with better formability (relevant to sheet metal forming, deep drawing).

**Considère's criterion (necking onset)**

Plastic instability (necking) initiates when the rate of strain hardening can no longer compensate for the reduction in cross-sectional area, i.e., when:

$$\frac{d\sigma_T}{d\varepsilon_T} = \sigma_T$$

For a Hollomon material, this condition is satisfied at $\varepsilon_T = n$, meaning the true strain at necking (and hence the uniform elongation limit) equals the strain-hardening exponent — a widely used practical estimate in sheet-forming analysis.

### Full Stress-Strain Curve: Characteristic Regions

**[Key Points]**

1. **Elastic region**: linear, fully recoverable, governed by $E$.
2. **Yield point / proportional limit**: onset of permanent (plastic) deformation.
3. **Uniform plastic deformation (strain hardening)**: dislocation multiplication and interaction increase flow stress; described by Hollomon or similar hardening laws.
4. **Necking (post-uniform elongation)**: localized reduction in cross-section; engineering stress decreases while true stress continues to rise until fracture.
5. **Fracture**: final separation, at the fracture strain/stress.

Key derived metrics from the engineering curve:

- **Ultimate tensile strength (UTS)**: maximum engineering stress, corresponding to onset of necking.
- **Ductility**: percent elongation ($\%EL = (l_f - l_0)/l_0 \times 100$) and percent reduction in area ($\%RA$).
- **Toughness**: area under the engineering stress-strain curve up to fracture, representing energy absorbed per unit volume.
- **Resilience**: area under the elastic portion of the curve, $U_r = \sigma_y^2/2E$, representing recoverable elastic energy storage capacity.

### Material Class Comparison

**[Key Points]**

- **Ductile metals** (annealed Cu, Al, mild steel): extended plastic region, high toughness, significant necking, $\%EL$ often >20%.
- **High-strength/brittle metals** (hardened tool steel, cast iron): minimal plastic region, low toughness, fracture near or shortly after yield.
- **Ceramics**: essentially linear elastic to fracture; negligible plasticity at room temperature due to limited dislocation mobility (strong covalent/ionic bonding, high Peierls stress); strength governed by flaw population (Weibull statistics) rather than a deterministic yield criterion.
- **Polymers**: highly temperature- and rate-dependent; can show glassy brittle behavior, yielding with strain softening, cold drawing (a necking-stabilization phenomenon distinct from metals due to molecular chain alignment), or rubbery elastomeric behavior depending on the regime relative to $T_g$.

### Curve Schematic

===MERMAID_DIAGRAM===

flowchart LR

A["Origin (0,0)"] --> B["Linear elastic region<br/>slope = E"]

B --> C["Yield point /<br/>0.2% offset σ_y"]

C --> D["Uniform plastic<br/>strain hardening<br/>σ_T = Kε_T^n"]

D --> E["UTS<br/>(necking onset,<br/>dσ_T/dε_T = σ_T)"]

E --> F["Necking /<br/>localized deformation"]

F --> G["Fracture"]



```
### Stress-Strain Curve (Illustrative) (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 420">
  <text x="320" y="24" text-anchor="middle" font-size="16" font-family="sans-serif" font-weight="bold">Engineering Stress-Strain Curve (svg_diagram)</text>
  <line x1="70" y1="360" x2="600" y2="360" stroke="black" stroke-width="2" />
  <line x1="70" y1="360" x2="70" y2="40" stroke="black" stroke-width="2" />
  <text x="335" y="395" text-anchor="middle" font-size="14" font-family="sans-serif">Strain, ε (engineering)</text>
  <text x="25" y="200" text-anchor="middle" font-size="14" font-family="sans-serif" transform="rotate(-90 25 200)">Stress, σ (engineering)</text>
  <path d="M 70 360 L 150 200" stroke="#1f77b4" stroke-width="2.5" fill="none" />
  <path d="M 150 200 Q 220 150 300 140" stroke="#1f77b4" stroke-width="2.5" fill="none" />
  <path d="M 300 140 Q 400 110 460 105" stroke="#1f77b4" stroke-width="2.5" fill="none" />
  <path d="M 460 105 Q 520 130 560 220" stroke="#1f77b4" stroke-width="2.5" fill="none" />
  <circle cx="150" cy="200" r="4" fill="red" />
  <text x="158" y="195" font-size="12" font-family="sans-serif">Yield point (σ_y)</text>
  <circle cx="460" cy="105" r="4" fill="red" />
  <text x="420" y="90" font-size="12" font-family="sans-serif">UTS</text>
  <circle cx="560" cy="220" r="4" fill="red" />
  <text x="500" y="240" font-size="12" font-family="sans-serif">Fracture</text>
  <line x1="70" y1="360" x2="150" y2="200" stroke="#999" stroke-dasharray="4,4" />
  <text x="90" y="270" font-size="11" font-family="sans-serif" fill="#555">slope = E</text>
  <text x="90" y="145" font-size="12" font-family="sans-serif" fill="#1f77b4">Elastic</text>
  <text x="220" y="130" font-size="12" font-family="sans-serif" fill="#1f77b4">Uniform plastic</text>
  <text x="470" y="150" font-size="12" font-family="sans-serif" fill="#1f77b4">Necking</text>
</svg>

### Worked Example: Elastic Deformation and Yield Prediction

**[Example]** A steel rod ($E = 200$ GPa, $\sigma_y = 350$ MPa) has an original length $l_0 = 2\ \text{m}$ and cross-sectional area $A_0 = 5\times10^{-4}\ \text{m}^2$. Determine (a) the elongation at an applied load of 100 kN, and (b) whether the rod has yielded.

**Solution:**

(a) Engineering stress:
$$\sigma = \frac{F}{A_0} = \frac{100{,}000\ \text{N}}{5\times10^{-4}\ \text{m}^2} = 2\times10^{8}\ \text{Pa} = 200\ \text{MPa}$$

Since $200\ \text{MPa} < \sigma_y = 350\ \text{MPa}$, the rod remains in the elastic region, so Hooke's Law applies:

$$\varepsilon = \frac{\sigma}{E} = \frac{200\times10^6}{200\times10^9} = 1\times10^{-3}$$

$$\Delta l = \varepsilon \cdot l_0 = 1\times10^{-3} \times 2\ \text{m} = 2\times10^{-3}\ \text{m} = 2\ \text{mm}$$

(b) Since applied stress (200 MPa) is below $\sigma_y$ (350 MPa), the rod has **not yielded**; deformation is fully elastic and recoverable upon unloading.

### Worked Example: True Stress from Hollomon Equation

**[Example]** A material has $K = 600$ MPa and $n = 0.20$. Determine the true stress at a true strain of $\varepsilon_T = 0.15$, and estimate the true strain at necking onset.

$$\sigma_T = K\varepsilon_T^{\,n} = 600 \times (0.15)^{0.20}$$

$$(0.15)^{0.20} = e^{0.20 \ln(0.15)} = e^{0.20 \times (-1.897)} = e^{-0.3794} \approx 0.684$$

$$\sigma_T \approx 600 \times 0.684 \approx 410\ \text{MPa}$$

By Considère's criterion for a Hollomon material, necking initiates at $\varepsilon_T = n = 0.20$, so uniform elongation is expected up to a true strain of approximately 0.20 before localized necking begins.

### Anisotropy and Real Material Behavior

**[Key Points]**
- Real polycrystalline metals may show mild anisotropy in $E$ due to crystallographic texture from rolling or forming; single crystals are strongly anisotropic (e.g., $E$ varies significantly with crystallographic direction in cubic metals, being generally highest along $\langle111\rangle$ and lowest along $\langle100\rangle$ for many FCC/BCC metals). [Behavior may vary by specific crystal structure and alloy; exact anisotropy ratios depend on elastic stiffness constants $C_{11}$, $C_{12}$, $C_{44}$.]
- Bauschinger effect: prior plastic deformation in one direction (e.g., tension) can reduce the yield strength upon reverse loading (compression), reflecting the influence of dislocation pile-ups and back-stresses on subsequent yielding.
- Strain-rate sensitivity: yield and flow stress increase with strain rate for most metals, described phenomenologically by $\sigma \propto \dot{\varepsilon}^m$, where $m$ is the strain-rate sensitivity exponent (small for conventional metals at room temperature, larger for superplastic alloys and at elevated temperature).

### Testing and Measurement Standards

- **Uniaxial tensile testing** (ASTM E8/E8M, ISO 6892-1) is the primary method for generating stress-strain curves, using extensometers or strain gauges for accurate strain measurement in the elastic and early plastic regime.
- **Compression testing** is used where tensile geometry is impractical (brittle ceramics, some cast materials) but is complicated by frictional end effects and barreling.
- **Digital Image Correlation (DIC)** is increasingly used for full-field strain mapping, capturing local strain heterogeneity (e.g., Lüders bands, necking strain fields) beyond what a single extensometer can resolve.

### Related Topics
- Elastic constants and anisotropy in single crystals ($C_{ij}$ stiffness tensor)
- Dislocation theory and strain-hardening mechanisms
- True stress-true strain analysis and post-necking correction methods (Bridgman correction)
- Strain-rate and temperature effects on flow stress (constitutive models: Johnson-Cook, Zerilli-Armstrong)
- Fracture mechanics and toughness (distinct from stress-strain-derived toughness)
- Hardness testing and its empirical correlation to tensile strength
- Viscoelastic and time-dependent deformation (creep) behavior


```