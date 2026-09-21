## Base and Derived Quantities


### Overview

Base and derived quantities form the conceptual scaffolding of the International System of Quantities (ISQ), which underlies the SI. A **base quantity** is one of a mutually independent set chosen by convention to be the foundation of a system of quantities; a **derived quantity** is defined algebraically in terms of the base quantities through the equations of physics. This distinction is foundational to dimensional analysis, uncertainty propagation, and unit traceability in precision metrology.

### The Seven Base Quantities

| Base Quantity | Symbol (quantity) | SI Base Unit | Dimension Symbol |
| --- | --- | --- | --- |
| Length | $l$ | metre (m) | L |
| Mass | $m$ | kilogram (kg) | M |
| Time | $t$ | second (s) | T |
| Electric current | $I$ | ampere (A) | I |
| Thermodynamic temperature | $T$ | kelvin (K) | Θ |
| Amount of substance | $n$ | mole (mol) | N |
| Luminous intensity | $I_v$ | candela (cd) | J |

**Key Points**

- These seven quantities are conventionally chosen as mutually independent — none can be expressed in terms of the others.
- The choice is a human convention, not a law of nature; other consistent quantity systems (e.g., using force instead of mass as fundamental) are mathematically possible but not adopted by the SI.
- Each base quantity has an associated **dimension**, denoted by a single upper-case roman letter, used in dimensional analysis independent of any particular unit choice.

### Derived Quantities

A derived quantity is expressed as a product of powers of the base quantities. The general dimensional form is:

$$\dim Q = \mathrm{L}^{\alpha}\mathrm{M}^{\beta}\mathrm{T}^{\gamma}\mathrm{I}^{\delta}\Theta^{\varepsilon}\mathrm{N}^{\zeta}\mathrm{J}^{\eta}$$

where the exponents $\alpha,\beta,\gamma,\ldots$ are the **dimensional exponents** of $Q$.

Examples central to metrology and quality control:

| Derived Quantity | Defining Relation | Dimension | SI Unit |
| --- | --- | --- | --- |
| Area | $A=l^2$ | $\mathrm{L}^2$ | m² |
| Volume | $V=l^3$ | $\mathrm{L}^3$ | m³ |
| Velocity | $v=l/t$ | $\mathrm{L T^{-1}}$ | m/s |
| Acceleration | $a=v/t$ | $\mathrm{L T^{-2}}$ | m/s² |
| Force | $F=ma$ | $\mathrm{M L T^{-2}}$ | N |
| Pressure/Stress | $p=F/A$ | $\mathrm{M L^{-1} T^{-2}}$ | Pa |
| Density | $\rho=m/V$ | $\mathrm{M L^{-3}}$ | kg/m³ |
| Energy | $E=Fl$ | $\mathrm{M L^2 T^{-2}}$ | J |
| Electric resistance | $R=V/I$ | $\mathrm{M L^2 T^{-3} I^{-2}}$ | Ω |

**Dimensionless (quantities of dimension one)**: plane angle (rad), solid angle (sr), strain, refractive index, and reflectance have the dimensional form $\mathrm{L}^0\mathrm{M}^0\mathrm{T}^0\ldots=1$. They carry SI units for clarity (rad, sr) but are numerically unitless ratios.

### Dimensional Analysis in Practice

Dimensional analysis exploits the requirement that physical equations must be **dimensionally homogeneous** — both sides of an equation must have identical dimensions.

**Example**

Verify the dimensional consistency of the stress-strain relation (Hooke's Law), $\sigma=E\varepsilon$:

- Stress $\sigma$: $\mathrm{M L^{-1} T^{-2}}$ (pascal)
- Strain $\varepsilon$: dimensionless ($\mathrm{L}^0\mathrm{M}^0\mathrm{T}^0$)
- Therefore Young's modulus $E$ must have dimension $\mathrm{M L^{-1} T^{-2}}$, i.e., units of pascal — consistent with its known unit.

This kind of check is routinely used in metrology to validate measurement equations, sensor transfer functions, and uncertainty-propagation formulas before they are implemented in calibration software or reported in test methods.

### Quantity Calculus and the Value Equation

A measured quantity is formally expressed as:

$$Q = \{Q\}\cdot[Q]$$

where $\{Q\}$ is the numerical value and $[Q]$ is the unit. This "quantity calculus" convention (per the *International Vocabulary of Metrology*, VIM) underlies correct handling of units in calculation software, spreadsheets, and calibration reports — a quantity is never just a number; the unit is an inseparable multiplicative factor.

### Diagram: From Base Quantities to a Derived Quantity (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 320">
<rect x="0" y="0" width="760" height="320" fill="#ffffff" />
<text x="380" y="24" font-size="16" font-weight="bold" text-anchor="middle" fill="#111111">Deriving Pressure from Base Quantities (svg_diagram)</text>
<rect x="40" y="60" width="140" height="55" rx="6" fill="#e8f0fe" stroke="#4285f4" />
<text x="110" y="83" font-size="12" text-anchor="middle" fill="#111111">Mass (M)</text>
<text x="110" y="100" font-size="10" text-anchor="middle" fill="#333333">kilogram</text>
<rect x="220" y="60" width="140" height="55" rx="6" fill="#e8f0fe" stroke="#4285f4" />
<text x="290" y="83" font-size="12" text-anchor="middle" fill="#111111">Length (L)</text>
<text x="290" y="100" font-size="10" text-anchor="middle" fill="#333333">metre</text>
<rect x="400" y="60" width="140" height="55" rx="6" fill="#e8f0fe" stroke="#4285f4" />
<text x="470" y="83" font-size="12" text-anchor="middle" fill="#111111">Time (T)</text>
<text x="470" y="100" font-size="10" text-anchor="middle" fill="#333333">second</text>
<rect x="130" y="160" width="180" height="55" rx="6" fill="#fef7e0" stroke="#f9ab00" />
<text x="220" y="183" font-size="12" text-anchor="middle" fill="#111111">Force: F = m·a</text>
<text x="220" y="200" font-size="10" text-anchor="middle" fill="#333333">M·L·T⁻² (newton)</text>
<rect x="350" y="160" width="180" height="55" rx="6" fill="#fef7e0" stroke="#f9ab00" />
<text x="440" y="183" font-size="12" text-anchor="middle" fill="#111111">Area: A = l²</text>
<text x="440" y="200" font-size="10" text-anchor="middle" fill="#333333">L² (m²)</text>
<rect x="240" y="250" width="220" height="55" rx="6" fill="#e6f4ea" stroke="#34a853" />
<text x="350" y="273" font-size="12" font-weight="bold" text-anchor="middle" fill="#111111">Pressure: p = F/A</text>
<text x="350" y="290" font-size="10" text-anchor="middle" fill="#333333">M·L⁻¹·T⁻² (pascal)</text>
<line x1="110" y1="115" x2="210" y2="160" stroke="#999999" stroke-width="1" />
<line x1="290" y1="115" x2="230" y2="160" stroke="#999999" stroke-width="1" />
<line x1="290" y1="115" x2="420" y2="160" stroke="#999999" stroke-width="1" />
<line x1="470" y1="115" x2="250" y2="160" stroke="#999999" stroke-width="1" />
<line x1="220" y1="215" x2="320" y2="250" stroke="#999999" stroke-width="1" />
<line x1="440" y1="215" x2="390" y2="250" stroke="#999999" stroke-width="1" />
</svg>

### Application to Precision Metrology & QC

- **Calibration equation validation**: Instrument transfer functions and correction formulas (e.g., thermal expansion correction in CMM measurements) must be dimensionally consistent; dimensional analysis is a first-line sanity check.
- **Uncertainty propagation**: The law of propagation of uncertainty (per GUM) requires each partial derivative term $\left(\frac{\partial f}{\partial x_i}\right)^2 u^2(x_i)$ to carry consistent dimensions matching the output quantity's dimension — errors here are a common source of incorrect uncertainty budgets.
- **Sensor and gauge design**: Strain gauges, load cells, and pressure transducers are specified and calibrated against the derived quantities they measure (strain, force, pressure), each traceable through base quantities to SI base units.
- **Software and database design**: Metrology information systems (LIMS, calibration management software) encode quantity dimensions explicitly to prevent unit-mismatch errors (a documented root cause in several high-profile engineering failures, e.g., unit-conversion errors in mission-critical systems).

### Common Pitfalls

- Confusing a **quantity** (a measurable attribute, e.g., "length") with a **unit** (a reference magnitude, e.g., "metre") — the VIM formally distinguishes these terms.
- Treating dimensionless quantities (angle, strain) as having no unit consideration at all — radians and steradians carry semantic meaning even though dimensionally equal to 1, and dropping them can cause errors when converting between angular and linear measures (e.g., arc length $s=r\theta$).
- Assuming a derived quantity's dimension is intuitively obvious without deriving it from the defining equation — this is a frequent source of formula errors in custom-built QC calculation tools.

### Related Topics

- The International System of Units (SI)
- Dimensional Analysis and the Buckingham Pi Theorem
- Quantity Calculus and the International Vocabulary of Metrology (VIM)
- Measurement Uncertainty and Propagation of Uncertainty (GUM)
- Traceability and Calibration Hierarchies
- Dimensionless Groups in Engineering Metrology (strain, refractive index)