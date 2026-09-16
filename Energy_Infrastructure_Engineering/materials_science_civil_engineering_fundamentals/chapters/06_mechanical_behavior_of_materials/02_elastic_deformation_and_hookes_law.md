## Elastic Deformation and Hooke's Law

### Overview

Elastic deformation is the reversible change in shape or size a material undergoes under applied load, with the material returning fully to its original dimensions upon unloading. It is governed, in its simplest form, by Hooke's Law, which establishes a linear relationship between stress and strain. This behavior underlies the design of nearly all structural systems operating within their service load range, where permanent deformation must be avoided.

### Nature of Elastic Deformation

**Key Points**

- Elastic deformation arises from the temporary stretching, compressing, or angular distortion of interatomic/interionic bonds without permanent displacement of atoms relative to their neighbors.
- Upon removal of the applied stress, stored strain energy is released, and atoms return to their original equilibrium positions.
- Elastic deformation is fully recoverable and, for most engineering materials at typical service stresses, is time-independent (as opposed to viscoelastic or creep behavior, where recoverable deformation accumulates over time under sustained load).
- The elastic range is bounded by the **proportional limit** (where linearity ends) and the **elastic limit** (the maximum stress from which the material still fully recovers); these two limits are close but not always numerically identical, especially in materials with gradual curvature entering the plastic region.

### Hooke's Law

**Key Points**

- Hooke's Law states that, within the elastic region, stress is directly proportional to strain:

$$\sigma = E\epsilon$$

Where $E$ is the modulus of elasticity (Young's modulus), representing the slope of the linear (elastic) portion of the stress-strain curve.

- For shear loading, the analogous relationship is:

$$\tau = G\gamma$$

Where $G$ is the shear modulus.

- For a general three-dimensional (triaxial) stress state in an isotropic, linear elastic material, Hooke's Law is generalized via the **generalized Hooke's Law** equations, incorporating Poisson's ratio effects:

$$\epsilon_x = \dfrac{1}{E}\left[\sigma_x - \nu(\sigma_y + \sigma_z)\right]$$



$$\epsilon_y = \dfrac{1}{E}\left[\sigma_y - \nu(\sigma_x + \sigma_z)\right]$$



$$\epsilon_z = \dfrac{1}{E}\left[\sigma_z - \nu(\sigma_x + \sigma_y)\right]$$

These equations capture the fact that a stress applied along one axis induces strain not only along that axis but also (via the Poisson effect) in the two perpendicular directions.

### Physical Origin: Interatomic Bonding and Modulus

**Key Points**

- The modulus of elasticity is fundamentally related to the curvature of the interatomic potential energy well near its equilibrium spacing — steeper curvature (stronger bonding) corresponds to a higher elastic modulus.
- Materials with strong primary bonding (covalent or ionic), such as ceramics, generally exhibit higher elastic moduli than metallically or, especially, van der Waals-bonded materials (many polymers).
- [Inference] Because the modulus derives from the fundamental bonding energy curve rather than from microstructural processing (which mainly affects strength, not stiffness), $E$ is relatively insensitive to grain size, cold work, or heat treatment for a given material composition, unlike yield strength or hardness.
- Temperature affects the modulus indirectly: as temperature increases, the equilibrium interatomic spacing increases (thermal expansion) and the potential well curvature typically decreases, gradually reducing $E$.

### Elastic Constants and Their Relationships

**Key Points**

- For isotropic linear elastic materials, only two independent elastic constants are needed to fully describe the elastic response; all others can be derived from any two.

$$G = \dfrac{E}{2(1+\nu)}$$



$$K = \dfrac{E}{3(1-2\nu)}$$

Where:

- $G$ = shear modulus
- $K$ = bulk modulus (relates hydrostatic pressure to volumetric strain)
- $\nu$ = Poisson's ratio

**Example**

For structural steel, with $E \approx 200\ GPa$ and $\nu \approx 0.30$:

$$G = \dfrac{200}{2(1+0.30)} \approx 76.9\ GPa$$

This calculated shear modulus is consistent with commonly tabulated values for structural steel, illustrating the internal consistency of the isotropic elastic constant relationships.

### Anisotropic Elastic Behavior

**Key Points**

- Many engineering materials — particularly wood, fiber-reinforced composites, and some rolled or textured metals — are **anisotropic**, meaning $E$ (and other elastic constants) vary with direction relative to material structure (e.g., grain direction in wood, fiber orientation in composites).
- [Inference] For such materials, a single scalar $E$ is insufficient, and design must reference direction-specific elastic properties (e.g., $E_{parallel}$ and $E_{perpendicular}$ to the grain/fiber direction), since applying an isotropic assumption to a strongly anisotropic material can significantly misestimate deflection or stress distribution.

### Elastic Strain Energy

**Key Points**

- Elastic deformation stores recoverable strain energy within the material. For uniaxial loading within the elastic range, the strain energy per unit volume (**modulus of resilience**, $U_r$) is:

$$U_r = \dfrac{1}{2}\sigma\epsilon = \dfrac{\sigma^2}{2E}$$

- This quantity represents the material's capacity to absorb energy elastically without permanent deformation and is significant in the design of components subject to impact or spring-back behavior.

### Elastic Deformation in Multiaxial and Structural Contexts

**Key Points**

- **Axial deformation** of a member under simple loading is computed as:

$$\delta = \dfrac{PL}{AE}$$

Where $P$ is applied axial force, $L$ is original length, $A$ is cross-sectional area, and $E$ is the modulus of elasticity — a direct application of Hooke's Law integrated over the member length.

- **Beam deflection** under elastic bending is governed by the flexural relationship:

$$\dfrac{d^2y}{dx^2} = -\dfrac{M(x)}{EI}$$

Where $M(x)$ is the bending moment distribution, $E$ is the modulus of elasticity, and $I$ is the moment of inertia of the cross-section — this is the elastic curve (beam deflection) differential equation, a direct structural extension of Hooke's Law.

### Civil Engineering Application: Serviceability and Structural Stiffness Design

**Example**

Elastic deformation principles govern **serviceability limit state** design in structural engineering, distinct from strength (ultimate limit state) design:

- Beam and slab deflections under service loads are calculated using elastic beam theory ($\delta = PL^3/(3EI)$ for a cantilever tip load, or similar standard formulas) and compared against code-specified deflection limits (e.g., span/360 for live load deflection in many building codes) to prevent cracking of finishes, ponding, or occupant discomfort.
- Elastic modulus of concrete, $E_c$, is typically estimated from empirical relationships to compressive strength (e.g., forms such as $E_c = 4700\sqrt{f'_c}$ in MPa units, per common code-based approximations), since concrete's modulus depends on aggregate type, mix proportions, and age in addition to strength — [Unverified] the exact empirical coefficient and applicability vary between design codes and should be confirmed against the governing code for a specific project.
- Elastic settlement of foundations (as opposed to long-term consolidation settlement) is estimated using elasticity theory applied to the soil mass, treating soil as a linear elastic continuum for this specific calculation despite soil's generally more complex real behavior.

### Diagram: Linear Elastic Region and Modulus

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 380">
<text x="300" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Elastic Region and Modulus of Elasticity (svg_diagram)</text>
<line x1="80" y1="330" x2="560" y2="330" stroke="#1a1a1a" stroke-width="2" />
<line x1="80" y1="330" x2="80" y2="50" stroke="#1a1a1a" stroke-width="2" />
<text x="320" y="360" font-size="14" text-anchor="middle" fill="#1a1a1a">Strain, ε</text>
<text x="30" y="190" font-size="14" text-anchor="middle" fill="#1a1a1a" transform="rotate(-90 30 190)">Stress, σ</text>
<line x1="80" y1="330" x2="300" y2="120" stroke="#0057b7" stroke-width="3" />
<path d="M 300 120 Q 380 90 460 100" stroke="#888" stroke-width="2" stroke-dasharray="5,4" fill="none" />
<circle cx="300" cy="120" r="4" fill="#c0392b" />
<text x="310" y="115" font-size="12" fill="#c0392b">Proportional Limit</text>
<line x1="140" y1="290" x2="200" y2="290" stroke="#2e7d32" stroke-width="1" />
<line x1="200" y1="290" x2="200" y2="250" stroke="#2e7d32" stroke-width="1" />
<text x="145" y="305" font-size="11" fill="#2e7d32">Δε</text>
<text x="205" y="270" font-size="11" fill="#2e7d32">Δσ</text>
<text x="150" y="230" font-size="12" fill="#1a1a1a">Slope = E = Δσ/Δε</text>
<text x="350" y="200" font-size="11" fill="#555">(Beyond proportional limit —</text>
<text x="350" y="215" font-size="11" fill="#555">plastic behavior begins)</text>
</svg>

### Comparative Summary Table

| Quantity | Symbol | Relationship | Typical Range (Structural Steel) |
| --- | --- | --- | --- |
| Modulus of elasticity | $E$ | $\sigma/\epsilon$ | ~200 GPa |
| Shear modulus | $G$ | $E/[2(1+\nu)]$ | ~77 GPa |
| Bulk modulus | $K$ | $E/[3(1-2\nu)]$ | ~167 GPa |
| Poisson's ratio | $\nu$ | $-\epsilon_{lateral}/\epsilon_{axial}$ | ~0.30 |
| Modulus of resilience | $U_r$ | $\sigma^2/(2E)$ | Material- and stress-dependent |

**Next Steps**

- Stress and Strain Fundamentals
- Plastic Deformation Mechanisms
- Generalized Hooke's Law and Multiaxial Stress States
- Beam Deflection and Structural Stiffness Analysis
- Modulus of Elasticity of Concrete and Empirical Code Relationships
- Anisotropic and Composite Material Elasticity
- Viscoelasticity and Time-Dependent Deformation