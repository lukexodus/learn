## Electric Charge and Coulomb's Law

### Overview

Electric charge is a fundamental property of matter that gives rise to electromagnetic interactions, one of the four fundamental forces of nature. Coulomb's Law quantifies the electrostatic force between stationary charged particles, forming the mathematical foundation of electrostatics and, more broadly, classical electromagnetism.

### Electric Charge

#### Fundamental Properties

**Key Points**

- Electric charge exists in two types, conventionally labeled positive and negative; like charges repel, unlike charges attract.
- Charge is **quantized**: all observed free charge is an integer multiple of the elementary charge $e \approx 1.602\times10^{-19}\ \text{C}$ (protons carry $+e$, electrons carry $-e$; quarks carry fractional charge but are never observed in isolation due to color confinement).
- Charge is **conserved**: the total electric charge of an isolated system remains constant; charge can be transferred between objects but never created or destroyed in any known process (consistent with all experimental observation).
- Charge is a **relativistic invariant**: the charge of a particle does not change with its velocity or reference frame, unlike mass (relativistic mass) or other quantities.

#### Charge Interactions and Induction

**Key Points**

- **Conductors**: materials (typically metals) in which charge carriers (electrons) move freely, allowing charge to redistribute in response to external fields.
- **Insulators**: materials in which charge carriers are tightly bound and cannot move freely, so charge tends to remain localized where deposited.
- **Charging methods**: friction (triboelectric effect), conduction (direct contact transfer), and induction (redistribution of charge in a nearby conductor without direct contact, typically followed by grounding to leave a net induced charge).

### Coulomb's Law

#### Statement

The electrostatic force between two point charges $q_1$ and $q_2$ separated by distance $r$ is:

$$\vec{F} = k_e\frac{q_1q_2}{r^2}\hat{r}$$

where $\hat{r}$ is the unit vector pointing from one charge to the other, and $k_e$ is **Coulomb's constant**:

$$k_e = \frac{1}{4\pi\epsilon_0} \approx 8.988\times10^9\ \text{N m}^2/\text{C}^2$$

with $\epsilon_0 \approx 8.854\times10^{-12}\ \text{C}^2/(\text{N m}^2)$ the **permittivity of free space**.

**Key Points**

- The force is directed along the line connecting the two charges (a central force).
- Like charges ($q_1q_2 > 0$) produce a repulsive force; unlike charges ($q_1q_2 < 0$) produce an attractive force, with the sign convention embedded directly in the formula.
- The force obeys an inverse-square law, structurally identical in form to Newton's law of universal gravitation, but electromagnetic forces can be either attractive or repulsive, unlike gravity, and are vastly stronger for elementary particles (the electrostatic force between two electrons exceeds their mutual gravitational attraction by a factor of roughly $10^{42}$).
- By Newton's third law, the force $q_1$ exerts on $q_2$ is equal and opposite to the force $q_2$ exerts on $q_1$.

#### Vector Form for Multiple Charges

For charge $q_i$ located at position $\vec{r}_i$, exerted by charge $q_j$ at $\vec{r}_j$:

$$\vec{F}_{ij} = k_e\frac{q_iq_j}{|\vec{r}_i-\vec{r}_j|^2}\hat{r}_{ij}$$

where $\hat{r}_{ij} = \dfrac{\vec{r}_i-\vec{r}_j}{|\vec{r}_i-\vec{r}_j|}$.

### Superposition Principle

**Key Points**

- The net electrostatic force on any charge due to multiple other charges is the **vector sum** of the individual pairwise Coulomb forces.
- Mathematically: $\vec{F}_{net} = \sum_{j\neq i} \vec{F}_{ij}$.
- This linearity is a direct consequence of the linearity of Maxwell's equations in vacuum and is essential for calculating forces and fields from extended (continuous) charge distributions.

### Worked Example: Force Between Two Point Charges

**Example**

Two point charges, $q_1 = +3\ \mu\text{C}$ and $q_2 = -5\ \mu\text{C}$, are separated by $r = 0.2\ \text{m}$ in vacuum. The magnitude of the force is:

$$F = k_e\frac{|q_1q_2|}{r^2} = (8.988\times10^9)\frac{(3\times10^{-6})(5\times10^{-6})}{(0.2)^2}$$



$$F = (8.988\times10^9)\frac{1.5\times10^{-11}}{0.04} \approx 3.37\ \text{N}$$

Since the charges have opposite signs, the force is **attractive**, directed along the line joining the two charges.

### Worked Example: Superposition with Three Charges

**Example**

Three point charges lie on the x-axis: $q_1 = +2\ \mu\text{C}$ at $x=0$, $q_2 = -4\ \mu\text{C}$ at $x = 0.3\ \text{m}$, and $q_3 = +1\ \mu\text{C}$ at $x = 0.5\ \text{m}$. To find the net force on $q_3$:

$$F_{13} = k_e\frac{q_1q_3}{(0.5)^2} = (8.988\times10^9)\frac{(2\times10^{-6})(1\times10^{-6})}{0.25} \approx 0.0719\ \text{N (repulsive, pointing in +x direction)}$$



$$F_{23} = k_e\frac{|q_2q_3|}{(0.2)^2} = (8.988\times10^9)\frac{(4\times10^{-6})(1\times10^{-6})}{0.04} \approx 0.899\ \text{N (attractive, pointing in -x direction, toward } q_2\text{)}$$

Taking rightward (+x) as positive:

$$F_{net} = F_{13} - F_{23} \approx 0.0719 - 0.899 \approx -0.827\ \text{N}$$

The net force on $q_3$ is approximately $0.827\ \text{N}$ directed in the $-x$ direction (toward $q_2$), since the attractive interaction with the larger, closer negative charge dominates.

### Coulomb's Law Diagram (SVG)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 260">
<text x="300" y="24" text-anchor="middle" font-size="16" font-family="sans-serif" font-weight="bold">Coulomb Force Between Point Charges (svg_diagram)</text>

<circle cx="120" cy="100" r="22" fill="#cc3333" />
<text x="120" y="106" text-anchor="middle" font-size="16" fill="white" font-family="sans-serif">+</text>
<circle cx="240" cy="100" r="22" fill="#cc3333" />
<text x="240" y="106" text-anchor="middle" font-size="16" fill="white" font-family="sans-serif">+</text>
<line x1="100" y1="100" x2="60" y2="100" stroke="black" stroke-width="2" marker-end="url(#arrow)" />
<line x1="260" y1="100" x2="300" y2="100" stroke="black" stroke-width="2" marker-end="url(#arrow)" />
<text x="180" y="150" text-anchor="middle" font-size="12" font-family="sans-serif">Like charges: repulsive force</text>

<circle cx="120" cy="210" r="22" fill="#cc3333" />
<text x="120" y="216" text-anchor="middle" font-size="16" fill="white" font-family="sans-serif">+</text>
<circle cx="240" cy="210" r="22" fill="#2266cc" />
<text x="240" y="216" text-anchor="middle" font-size="16" fill="white" font-family="sans-serif">-</text>
<line x1="145" y1="210" x2="185" y2="210" stroke="black" stroke-width="2" marker-end="url(#arrow)" />
<line x1="215" y1="210" x2="175" y2="210" stroke="black" stroke-width="2" marker-end="url(#arrow)" />
<line x1="360" y1="60" x2="360" y2="240" stroke="#cccccc" stroke-width="1" />
<text x="450" y="210" text-anchor="middle" font-size="12" font-family="sans-serif">Unlike charges: attractive force</text>
</svg>

### Continuous Charge Distributions

For extended objects, discrete summation is replaced by integration over the charge distribution. The electric field at a field point due to a continuous distribution is obtained by treating each infinitesimal charge element $dq$ as a point charge and integrating:

$$\vec{E} = k_e\int \frac{dq}{r^2}\hat{r}$$

**Key Points**

- **Linear charge density**: $\lambda = dq/dl$ (C/m), used for charged wires or rods.
- **Surface charge density**: $\sigma = dq/dA$ (C/m²), used for charged sheets or plates.
- **Volume charge density**: $\rho = dq/dV$ (C/m³), used for charged solids.
- These integrals become the standard technique for deriving the electric field of rings, disks, rods, and spheres in introductory electrostatics, and connect directly to Gauss's Law for distributions with sufficient symmetry.

### Coulomb's Law in Different Media

**Key Points**

- In a medium other than vacuum, the permittivity $\epsilon_0$ is replaced by $\epsilon = \epsilon_r\epsilon_0$, where $\epsilon_r$ is the material's relative permittivity (dielectric constant), reducing the force magnitude compared to vacuum: $F = \dfrac{1}{4\pi\epsilon}\dfrac{q_1q_2}{r^2}$.
- This reduction reflects the polarization of the medium's molecules, which partially screens the applied field — the basis for dielectric behavior in capacitors and insulating materials.

### Relation to the Electric Field Concept

**Key Points**

- Coulomb's Law can be reformulated by defining the electric field $\vec{E}$ of a source charge $Q$ at distance $r$: $\vec{E} = k_e\dfrac{Q}{r^2}\hat{r}$, such that the force on a test charge $q$ placed in that field is $\vec{F} = q\vec{E}$.
- This reformulation separates the source charge's influence (the field, existing independently of any test charge) from the force experienced by a specific test charge, a conceptual shift that becomes essential for understanding fields, potential, and later, electromagnetic radiation.
- Coulomb's Law for static point charges is the special case of the more general Maxwell's equations (specifically Gauss's Law) applied to electrostatics.

### Historical Context and Experimental Verification

**Key Points**

- Charles-Augustin de Coulomb established the inverse-square force law experimentally in 1785 using a torsion balance, measuring the force between charged spheres as a function of separation and charge magnitude.
- Modern precision tests (using Cavendish-style null experiments) confirm the exponent in the inverse-square law is 2 to extraordinarily high precision, with any deviation constrained to be smaller than approximately $10^{-16}$, providing strong experimental support for the masslessness of the photon (a non-zero photon mass would introduce a Yukawa-type modification to the force law at large distances).

### Validity and Limitations

**Key Points**

- Coulomb's Law strictly applies to point charges (or spherically symmetric charge distributions, treated as point charges from outside the distribution, by analogy with the shell theorem in gravitation) at rest or moving slowly (electrostatics regime).
- For charges in relative motion, magnetic forces and retardation effects become significant, requiring the full framework of Maxwell's equations and, for high-precision or high-velocity situations, relativistic electrodynamics.
- [Inference] At subatomic distances, quantum electrodynamics (QED) provides the more fundamental description of electromagnetic interactions, with Coulomb's Law emerging as the classical, low-energy limit of photon exchange between charged particles.

### Conclusion

Electric charge and Coulomb's Law together establish the foundational framework of electrostatics: charge is a conserved, quantized property of matter, and the force between static charges follows a precise inverse-square law mediated by the vacuum permittivity constant. Coulomb's Law, combined with the superposition principle, provides the essential toolkit for calculating forces and, through the electric field concept, sets the stage for the broader theory of electromagnetism developed in Gauss's Law, electric potential, and ultimately Maxwell's equations.

**Related Topics**

- Electric Field and Field Lines
- Gauss's Law and Symmetric Charge Distributions
- Electric Potential and Potential Energy
- Conductors, Insulators, and Dielectrics
- Continuous Charge Distributions (Rods, Rings, Disks, Spheres)
- Superposition Principle in Electromagnetism
- Charge Quantization and the Elementary Charge
- Maxwell's Equations