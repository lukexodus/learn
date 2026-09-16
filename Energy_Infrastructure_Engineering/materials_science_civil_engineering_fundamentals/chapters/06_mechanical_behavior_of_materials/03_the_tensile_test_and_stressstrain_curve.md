## The Tensile Test and Stress-Strain Curve

### Overview

The tensile test is the most widely used mechanical test for characterizing a material's response to uniaxial loading. It provides the raw load-elongation data from which the engineering stress-strain curve is constructed, yielding fundamental design properties such as elastic modulus, yield strength, tensile strength, ductility, and toughness. Standardized tensile testing procedures (e.g., ASTM E8 for metals, ASTM D638 for plastics) ensure comparability of results across laboratories.

### Test Setup and Procedure

**Key Points**

- A standardized specimen — typically a "dog-bone" shape with a reduced, uniform-diameter **gauge length** flanked by wider grip ends — is mounted in a universal testing machine.
- The gauge length ($l_0$) and initial cross-sectional area ($A_0$) are measured precisely prior to testing, as they form the denominators for engineering strain and stress calculations, respectively.
- The specimen is loaded in tension at a controlled, typically constant, strain rate (or crosshead displacement rate) while load and elongation are continuously recorded, most commonly via a load cell and an extensometer.
- The test continues until specimen fracture, after which final gauge length and final cross-sectional area (at the fracture location) may also be measured to compute ductility measures.

### Constructing the Engineering Stress-Strain Curve

**Key Points**

- Recorded load ($F$) and elongation ($\Delta l$) data are converted into engineering stress and engineering strain:

$$\sigma = \dfrac{F}{A_0} \qquad \epsilon = \dfrac{\Delta l}{l_0}$$

- Plotting $\sigma$ (y-axis) against $\epsilon$ (x-axis) produces the engineering stress-strain curve, the primary graphical output of the tensile test.
- This curve is "engineering" because both $A_0$ and $l_0$ are held as constants (original values) throughout the calculation, even though the specimen's actual dimensions change continuously during the test.

### Key Regions and Properties Extracted from the Curve

**Elastic Region and Modulus of Elasticity**

- The initial linear portion of the curve represents elastic deformation, with slope equal to the modulus of elasticity, $E = \sigma/\epsilon$.

**Yield Strength**

- The stress at which the material begins to exhibit permanent (plastic) deformation.
- For materials with a distinct yield point (e.g., low-carbon steel), an upper and lower yield point may be visible, associated with dislocation unpinning phenomena.
- For materials lacking a sharp yield point (e.g., aluminum alloys), the **0.2% offset method** is used: a line parallel to the elastic slope is drawn starting at $\epsilon = 0.002$, and its intersection with the curve defines the offset yield strength.

**Ultimate Tensile Strength (UTS)**

- The maximum engineering stress reached during the test, corresponding to the onset of necking.

$$\sigma_{UTS} = \dfrac{F_{max}}{A_0}$$

**Fracture Strength**

- The engineering stress at the point of fracture, which is typically lower than the UTS because necking causes a localized reduction in load-bearing area, decreasing the engineering stress (force divided by the *original* area) even as the true stress at the neck continues to climb.

**Ductility**

- Quantified by two standard measures obtained after fracture:

$$\%EL = \dfrac{l_f - l_0}{l_0} \times 100$$



$$\%RA = \dfrac{A_0 - A_f}{A_0} \times 100$$

Where $\%EL$ is percent elongation and $\%RA$ is percent reduction in area, with $l_f$ and $A_f$ the final gauge length and final fracture-area, respectively.

**Toughness**

- The area under the entire engineering stress-strain curve up to fracture represents the energy absorbed per unit volume prior to failure (a measure of toughness under quasi-static, monotonic loading conditions), computed as:

$$U_T = \int_0^{\epsilon_f} \sigma\, d\epsilon$$

**Resilience**

- The area under the elastic portion of the curve only, up to the yield point, represents the modulus of resilience — the recoverable elastic energy absorbed per unit volume.

### Annotated Stress-Strain Curve Diagram

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 450">
<text x="350" y="25" font-size="16" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Annotated Tensile Stress-Strain Curve (svg_diagram)</text>
<line x1="80" y1="390" x2="650" y2="390" stroke="#1a1a1a" stroke-width="2" />
<line x1="80" y1="390" x2="80" y2="50" stroke="#1a1a1a" stroke-width="2" />
<text x="360" y="425" font-size="14" text-anchor="middle" fill="#1a1a1a">Engineering Strain, ε</text>
<text x="30" y="220" font-size="14" text-anchor="middle" fill="#1a1a1a" transform="rotate(-90 30 220)">Engineering Stress, σ</text>
<path d="M 80 390 L 190 230" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 190 230 Q 260 195 330 175" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 330 175 Q 420 130 480 118" stroke="#0057b7" stroke-width="3" fill="none" />
<path d="M 480 118 Q 560 145 610 210" stroke="#0057b7" stroke-width="3" fill="none" />
<line x1="110" y1="390" x2="235" y2="230" stroke="#999" stroke-width="1" stroke-dasharray="3,3" />
<circle cx="196" cy="230" r="4" fill="#c0392b" />
<text x="200" y="255" font-size="11" fill="#c0392b">Yield Strength (0.2% offset)</text>
<circle cx="480" cy="118" r="4" fill="#c0392b" />
<text x="440" y="100" font-size="11" fill="#c0392b">Ultimate Tensile Strength</text>
<circle cx="610" cy="210" r="4" fill="#c0392b" />
<text x="565" y="235" font-size="11" fill="#c0392b">Fracture</text>

<text x="95" y="340" font-size="11" fill="#555">Elastic</text>

<text x="250" y="160" font-size="11" fill="#555">Uniform plastic deformation</text>

<text x="510" y="170" font-size="11" fill="#555">Necking</text>

</svg>

### True Stress-True Strain Behavior

**Key Points**

- Because engineering stress decreases after UTS due to necking, the true stress-strain curve is often plotted for a more accurate representation of material flow behavior at large strains.
- True stress and true strain are related to engineering values (valid up to necking) by:

$$\sigma_T = \sigma(1+\epsilon) \qquad \epsilon_T = \ln(1+\epsilon)$$

- Unlike the engineering curve, the true stress-strain curve rises continuously (monotonically) up to fracture, since true stress accounts for the actual, reduced cross-sectional area at the neck.
- Many metals follow a power-law hardening relationship in the plastic region:

$$\sigma_T = K\epsilon_T^n$$

Where $K$ is the strength coefficient and $n$ is the strain-hardening exponent — both empirically determined material constants.

### Test Variables Affecting Results

**Key Points**

- **Strain rate**: higher strain rates generally increase apparent yield and tensile strength for many metals, particularly at elevated temperature or for strain-rate-sensitive materials (e.g., some polymers).
- **Temperature**: elevated test temperature generally reduces strength and modulus while often increasing ductility; low temperature can increase strength but reduce ductility and promote brittle behavior in some materials (notably ferritic steels near their ductile-to-brittle transition temperature).
- **Specimen geometry and gauge length**: percent elongation values are gauge-length-dependent, which is why standards specify gauge length precisely (or require normalization) to allow valid comparison between reported ductility values.
- [Inference] Because ductility measures are geometry-sensitive, comparing %EL values from tests using different gauge lengths or specimen standards without correction can produce misleading conclusions about relative ductility.

### Civil Engineering Application: Reinforcing Steel Testing

**Example**

Tensile testing of reinforcing steel bars (rebar) is a standard quality control and design verification procedure:

- Yield strength ($f_y$) and ultimate tensile strength ($f_u$) obtained from standardized rebar tensile tests are used directly as design input parameters in reinforced concrete design per governing structural codes.
- The ratio $f_u/f_y$ (sometimes required to fall within a specified range by code or specification) is used as an indicator of ductility and strain-hardening capacity, particularly important for structures designed for seismic performance, where adequate post-yield ductility allows energy dissipation before failure.
- [Unverified] Specific minimum elongation and $f_u/f_y$ ratio requirements vary by grade of steel and governing specification/code, so applicable values should be confirmed against the relevant standard for a given project.

### Comparative Summary Table

| Property | Symbol | Formula | Obtained From |
| --- | --- | --- | --- |
| Modulus of elasticity | $E$ | Slope of elastic region | Initial linear portion of curve |
| Yield strength | $\sigma_y$ | 0.2% offset or direct yield point | Onset of plastic deformation |
| Ultimate tensile strength | $\sigma_{UTS}$ | $F_{max}/A_0$ | Peak of engineering curve |
| Fracture strength | $\sigma_f$ | $F_{fracture}/A_0$ | Point of specimen failure |
| Percent elongation | $\%EL$ | $(l_f - l_0)/l_0 \times 100$ | Post-fracture gauge length measurement |
| Percent reduction in area | $\%RA$ | $(A_0 - A_f)/A_0 \times 100$ | Post-fracture cross-section measurement |
| Toughness | $U_T$ | $\int \sigma\, d\epsilon$ | Total area under curve |
| Resilience | $U_r$ | $\sigma_y^2/(2E)$ | Area under elastic region |

**Next Steps**

- Stress and Strain Fundamentals
- Elastic Deformation and Hooke's Law
- Plastic Deformation Mechanisms
- Ductility, Toughness, and Resilience
- True Stress-True Strain and Strain Hardening Behavior
- Hardness Testing and Correlation to Tensile Strength
- Mechanical Testing Standards for Reinforcing Steel