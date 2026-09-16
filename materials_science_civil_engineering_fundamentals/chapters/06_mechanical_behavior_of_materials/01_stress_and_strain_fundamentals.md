## Stress and Strain Fundamentals


### Overview

Stress and strain are the two foundational quantities used to describe how materials respond to applied forces. Stress quantifies the internal intensity of force within a material, while strain quantifies the resulting deformation. Together, they form the basis for virtually all subsequent mechanical behavior analysis — elasticity, plasticity, fracture, fatigue — and are indispensable in civil engineering design of structural members, foundations, and materials selection.

### Concept of Stress

**Key Points**

- Stress ($\sigma$ or $\tau$) is defined as internal force per unit area, arising in a body in response to externally applied loads.
- Stress is not a property of the material itself but a response quantity dependent on geometry, applied load, and the orientation of the plane considered.
- Two fundamental categories exist based on the orientation of the internal force relative to the area:
  - **Normal stress** ($\sigma$): force acts perpendicular to the surface.
  - **Shear stress** ($\tau$): force acts parallel (tangential) to the surface.

**Normal Stress**

$$\sigma = \dfrac{F}{A_0}$$

Where $F$ is the applied axial force and $A_0$ is the original cross-sectional area (this defines **engineering stress**; true stress uses the instantaneous area, discussed below).

Normal stress is further classified as:

- **Tensile stress**: force tends to elongate the material (conventionally positive).
- **Compressive stress**: force tends to shorten the material (conventionally negative).

**Shear Stress**

$$\tau = \dfrac{F_s}{A_0}$$

Where $F_s$ is the force component acting parallel to the cross-sectional plane.

### Concept of Strain

**Key Points**

- Strain ($\epsilon$ or $\gamma$) is a dimensionless measure of deformation, expressing the relative change in dimension caused by stress.
- Like stress, strain is categorized as normal (linear) or shear (angular).

**Normal (Linear) Strain**

$$\epsilon = \dfrac{\Delta l}{l_0} = \dfrac{l_i - l_0}{l_0}$$

Where $l_0$ is the original length and $l_i$ is the instantaneous (deformed) length. This is **engineering strain**; it is dimensionless but frequently expressed as a percentage or in units of mm/mm.

**Shear Strain**

$$\gamma = \tan\theta$$

Where $\theta$ is the angular distortion (change in angle) between two originally perpendicular lines within the material, resulting from applied shear stress.

### Engineering vs. True Stress and Strain

**Key Points**

- **Engineering stress/strain** use the *original* cross-sectional area and gauge length, respectively, and are standard for most design purposes because original dimensions are known and constant.
- **True stress** accounts for the *instantaneous* cross-sectional area as the specimen deforms:

$$\sigma_T = \sigma(1 + \epsilon)$$

- **True strain** is defined as the integral of incremental length change over instantaneous length:

$$\epsilon_T = \ln(1 + \epsilon)$$

- These relationships between engineering and true values are valid only up to the onset of necking, since necking introduces a localized, non-uniform triaxial stress state that the simple constant-volume assumption behind these conversion formulas does not capture.
- [Inference] True stress-strain curves are generally preferred for accurate modeling of large-strain plastic deformation processes (e.g., metal forming simulations), while engineering stress-strain curves remain the standard for reporting design allowables such as yield strength and tensile strength, since they map directly to as-manufactured part dimensions.

### The Stress-Strain Curve

**Key Points**

- Obtained from a uniaxial tensile (or compressive) test, the engineering stress-strain curve reveals several characteristic regions and material properties:
  - **Elastic region**: stress and strain are linearly related (for most engineering materials at small strains); deformation is fully recoverable upon unloading.
  - **Yield point**: the stress at which the material transitions from elastic to plastic (permanent) deformation. For materials without a sharp yield point, the **0.2% offset method** is used to define an engineering yield strength.
  - **Plastic (strain-hardening) region**: permanent deformation occurs; stress generally continues to rise with strain due to strain hardening, up to the ultimate tensile strength.
  - **Necking region**: after the ultimate tensile strength (UTS) is reached, deformation localizes into a neck, engineering stress decreases (because $A_0$ in the denominator no longer reflects the shrinking actual area) even as true stress continues to rise, until fracture.

**Example**

A schematic labeled stress-strain curve is illustrated below.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 420">
<text x="350" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Engineering Stress-Strain Curve (svg_diagram)</text>
<line x1="80" y1="370" x2="650" y2="370" stroke="#1a1a1a" stroke-width="2" />
<line x1="80" y1="370" x2="80" y2="40" stroke="#1a1a1a" stroke-width="2" />
<text x="360" y="405" font-size="14" text-anchor="middle" fill="#1a1a1a">Strain, ε</text>
<text x="30" y="205" font-size="14" text-anchor="middle" fill="#1a1a1a" transform="rotate(-90 30 205)">Stress, σ</text>
<path d="M 80 370 L 180 220" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 180 220 Q 260 175 340 155" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 340 155 Q 420 115 480 105" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 480 105 Q 550 125 600 190" stroke="#0057b7" stroke-width="3" fill="none" />
<circle cx="180" cy="220" r="4" fill="#c0392b" />
<text x="185" y="245" font-size="12" fill="#c0392b">Yield Point (σy)</text>
<circle cx="480" cy="105" r="4" fill="#c0392b" />
<text x="440" y="90" font-size="12" fill="#c0392b">Ultimate Tensile Strength (UTS)</text>
<circle cx="600" cy="190" r="4" fill="#c0392b" />
<text x="560" y="215" font-size="12" fill="#c0392b">Fracture</text>
<line x1="80" y1="370" x2="180" y2="220" stroke="#888" stroke-width="1" stroke-dasharray="4,3" />
<text x="90" y="320" font-size="11" fill="#555">Elastic region</text>
<text x="240" y="180" font-size="11" fill="#555">Plastic / strain hardening</text>
<text x="500" y="160" font-size="11" fill="#555">Necking</text>
</svg>

### Hooke's Law and Elastic Constants

**Key Points**

- Within the elastic (linear) region, stress and strain are related by Hooke's Law:

$$\sigma = E\epsilon$$

Where $E$ is the **modulus of elasticity** (Young's modulus), a measure of material stiffness.

- For shear:

$$\tau = G\gamma$$

Where $G$ is the **shear modulus**.

- **Poisson's Ratio** ($\nu$) relates lateral strain to axial strain under uniaxial loading:

$$\nu = -\dfrac{\epsilon_{lateral}}{\epsilon_{axial}}$$

- For isotropic materials, the elastic constants are interrelated:

$$G = \dfrac{E}{2(1+\nu)}$$



$$K = \dfrac{E}{3(1-2\nu)}$$

Where $K$ is the **bulk modulus**, relating hydrostatic stress to volumetric strain.

### Types of Loading and Stress States

**Key Points**

- **Uniaxial stress**: load applied along a single axis (basic tensile/compression test assumption).
- **Biaxial stress**: stress acting in two perpendicular directions within a plane (e.g., thin-walled pressure vessels).
- **Triaxial stress**: stress acting in three mutually perpendicular directions (common in soil mechanics, confined concrete, deep foundation elements).
- **Pure shear**: equal and opposite shear stresses with no normal stress component, relevant to torsion and certain connection/bolt design scenarios.

### Civil Engineering Application: Structural Member Design

**Example**

In reinforced concrete beam design, the following stress/strain relationships are applied directly:

- Concrete strain in the compression zone is assumed to follow an idealized stress-strain relationship (e.g., a parabolic-rectangular or simplified rectangular stress block per most modern design codes) with a defined ultimate compressive strain, commonly taken as $\epsilon_{cu} = 0.003$ in many code frameworks. [Unverified] The exact ultimate strain value and stress block shape depend on the specific design code being applied (e.g., ACI, Eurocode), so the applicable code should always be verified for a given design.
- Reinforcing steel strain is assumed to follow an idealized elastic-perfectly-plastic (or strain-hardening) stress-strain model, with yield strain $\epsilon_y = f_y/E_s$.
- Structural analysis of members under combined axial load, bending, and shear requires resolving the stress state at each cross-section into normal and shear components consistent with the beam theory being applied (e.g., Euler-Bernoulli or Timoshenko beam assumptions).

### Comparative Summary Table

| Quantity | Symbol | Formula | Units (SI) |
| --- | --- | --- | --- |
| Normal (engineering) stress | $\sigma$ | $F/A_0$ | Pa ($N/m^2$) |
| Shear stress | $\tau$ | $F_s/A_0$ | Pa |
| Normal (engineering) strain | $\epsilon$ | $\Delta l / l_0$ | dimensionless |
| Shear strain | $\gamma$ | $\tan\theta$ | dimensionless (radians) |
| True stress | $\sigma_T$ | $\sigma(1+\epsilon)$ | Pa |
| True strain | $\epsilon_T$ | $\ln(1+\epsilon)$ | dimensionless |
| Modulus of elasticity | $E$ | $\sigma/\epsilon$ (elastic region) | Pa |
| Shear modulus | $G$ | $\tau/\gamma$ (elastic region) | Pa |
| Poisson's ratio | $\nu$ | $-\epsilon_{lateral}/\epsilon_{axial}$ | dimensionless |

**Next Steps**

- Elastic Deformation and Hooke's Law
- Plastic Deformation Mechanisms
- Yield Criteria (Tresca and von Mises)
- Ductility, Toughness, and Resilience
- True Stress-True Strain Relationships and Strain Hardening
- Fatigue and Fracture Mechanics
- Stress-Strain Behavior of Reinforced Concrete Sections