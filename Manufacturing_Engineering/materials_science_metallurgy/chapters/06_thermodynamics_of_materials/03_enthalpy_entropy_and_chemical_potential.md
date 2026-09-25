## Enthalpy, Entropy, and Chemical Potential


### Overview

Enthalpy, entropy, and chemical potential are the three state functions that together determine how energy and matter redistribute within a materials system to reach equilibrium. Enthalpy and entropy combine into Gibbs free energy to establish phase stability at fixed composition; chemical potential extends this framework to open, multi-component systems, governing how atoms partition between phases and driving diffusion, segregation, and precipitation.

### Enthalpy

**Key Points**

- Enthalpy is defined as $H = U + PV$, where $U$ is internal energy, $P$ is pressure, and $V$ is volume.
- At constant pressure, $dH = \delta Q_p$ — enthalpy change equals heat absorbed or released, making it the natural energy bookkeeping variable for materials processing (most of which occurs near atmospheric pressure).
- Key materials enthalpy quantities: standard enthalpy of formation $\Delta H_f^\circ$ (energy to form a compound from elements in standard states), latent heat of fusion/vaporization, and enthalpy of mixing $\Delta H_{mix}$.

**Enthalpy of Mixing and Bonding Character**

In the regular solution model, $\Delta H_{mix} = \Omega X_A X_B$, where the sign of the interaction parameter $\Omega$ reflects relative bond energies:

$$\Omega \propto N_a z \left[\varepsilon_{AB} - \frac{1}{2}(\varepsilon_{AA} + \varepsilon_{BB})\right]$$

where $\varepsilon_{ij}$ are pairwise bond energies, $z$ is coordination number, and $N_a$ is Avogadro's number.

- $\Omega < 0$ ($\varepsilon_{AB}$ more negative/stronger than average of like-bonds): unlike-atom bonding favored → ordering tendency, compound formation.
- $\Omega > 0$: like-atom bonding favored → clustering tendency, potential miscibility gap or phase separation.

**Example**

For a hypothetical A-B system with $\Omega = -15{,}000\ \text{J/mol}$ at $X_A = X_B = 0.5$:

$$\Delta H_{mix} = (-15{,}000)(0.5)(0.5) = -3750\ \text{J/mol}$$

The negative value indicates energetically favorable mixing, consistent with a system that tends toward ordered intermediate compounds or extensive solid solubility.

### Entropy

**Key Points**

- Entropy quantifies the number of microscopic configurations ($\Omega$, the multiplicity) consistent with a macrostate: $S = k_B \ln \Omega$.
- Three principal contributions relevant to materials systems: configurational entropy (arrangement of atoms/vacancies on lattice sites), thermal/vibrational entropy (phonon population), and, in some systems, magnetic or electronic entropy.
- Configurational entropy of mixing for an ideal (random) solution:



  $$\Delta S_{mix} = -R(X_A \ln X_A + X_B \ln X_B)$$
- This expression is maximized at $X_A = X_B = 0.5$ and is always positive — mixing is always entropically favorable, which is why the $-T\Delta S_{mix}$ term in Gibbs free energy always pulls the system toward homogeneity as $T$ increases, eventually overcoming any positive $\Delta H_{mix}$ at sufficiently high temperature.

**Vibrational Entropy**

Beyond configurational effects, differences in atomic bonding stiffness between phases contribute a vibrational entropy difference $\Delta S_{vib}$, which can be significant in some transformations (e.g., between allotropes with substantially different bond stiffness) and is captured in the Debye model of lattice heat capacity. [Unverified: the relative magnitude of vibrational vs. configurational entropy contributions is system-specific and is often obtained from calorimetric or computational (DFT/phonon) data rather than estimated analytically.]

### Chemical Potential

**Key Points**

- Chemical potential $\mu_i$ is the partial molar Gibbs free energy of component $i$ — the change in total system free energy per mole of $i$ added, at constant $T$, $P$, and moles of all other components:



  $$\mu_i = \left(\frac{\partial G}{\partial n_i}\right)_{T,P,n_{j \neq i}}$$
- For an ideal solution, chemical potential relates to composition via:



  $$\mu_i = \mu_i^\circ + RT\ln X_i$$
- For non-ideal solutions, activity $a_i$ replaces mole fraction, with activity coefficient $\gamma_i$ capturing deviation from ideality:



  $$\mu_i = \mu_i^\circ + RT\ln a_i = \mu_i^\circ + RT\ln(\gamma_i X_i)$$

**Chemical Potential as the Driving Force for Diffusion**

Fick's laws describe diffusion phenomenologically in terms of concentration gradients, but the rigorous thermodynamic driving force is the chemical potential gradient, not the concentration gradient directly:

$$J_i = -M_i C_i \frac{\partial \mu_i}{\partial x}$$

where $M_i$ is atomic mobility. This distinction matters because in systems with strongly non-ideal solution behavior (particularly near miscibility gaps, $\partial \mu_i/\partial X_i$ can become negative even though $\partial C_i/\partial x \neq 0$ in the conventional direction — this is precisely the mechanism behind uphill diffusion, where atoms diffuse from low to high concentration regions (observed during spinodal decomposition), which a naive concentration-gradient-only picture cannot explain.

**Equilibrium Condition via Chemical Potential**

At equilibrium between two phases $\alpha$ and $\beta$, the chemical potential of each component must be equal in both phases:

$$\mu_i^\alpha = \mu_i^\beta \quad \text{for every component } i$$

This is the rigorous, multi-component generalization of the common-tangent construction: geometrically, the common tangent line's slope equals $\mu_B - \mu_A$, and its intercepts on the pure-component axes give $\mu_A$ and $\mu_B$ directly. Equal chemical potentials in coexisting phases is precisely what the common tangent construction encodes graphically.

**Example**

For a dilute solution of carbon in austenite obeying Henry's law behavior ($a_C \approx \gamma_C X_C$ with $\gamma_C$ roughly constant at low $X_C$), the chemical potential difference driving carbon diffusion from a high-activity carburizing atmosphere ($a_C^{surface}$) into the lower-activity bulk ($a_C^{bulk}$) is:

$$\Delta \mu_C = RT \ln\left(\frac{a_C^{surface}}{a_C^{bulk}}\right)$$

This is the rigorous thermodynamic driving force underlying the carburizing process (see: Industrial Applications of Diffusion), which in the simplified Fickian treatment is instead approximated by the concentration difference $C_s - C_0$.

### Gibbs-Duhem Relation

**Key Points**

- The chemical potentials of components in a solution are not independent; they are constrained at constant $T$, $P$ by the Gibbs-Duhem equation:



  $$X_A\,d\mu_A + X_B\,d\mu_B = 0$$
- This means that if the chemical potential of one component increases with composition, the other must decrease correspondingly — a consistency constraint used to check thermodynamic models and to derive one component's activity behavior from the other's (e.g., via the Gibbs-Duhem integration method in experimental thermodynamics).

### Interrelationship Summary

| Quantity | Symbol | Physical Meaning | Role |
| --- | --- | --- | --- |
| Enthalpy | $H$ | Heat content at constant P | Bond energy, latent heats, $\Delta H_{mix}$ |
| Entropy | $S$ | Configurational/vibrational disorder | $\Delta S_{mix}$, always favors mixing |
| Gibbs Free Energy | $G = H - TS$ | Overall stability at const. T, P | Phase equilibrium, $\Delta G < 0$ spontaneity |
| Chemical Potential | $\mu_i = \partial G/\partial n_i$ | Per-atom free energy of species $i$ | True driving force for diffusion, phase partitioning |

### Diagram: Chemical Potential and Common Tangent Relationship (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 400">
<rect x="0" y="0" width="700" height="400" fill="white" />
<text x="350" y="25" font-size="16" text-anchor="middle" font-family="sans-serif" font-weight="bold">Chemical Potential from Common Tangent (svg_diagram)</text>
<line x1="80" y1="350" x2="620" y2="350" stroke="black" stroke-width="1.5" />
<line x1="80" y1="350" x2="80" y2="60" stroke="black" stroke-width="1.5" />
<text x="350" y="380" font-size="12" text-anchor="middle" font-family="sans-serif">Composition, X_B</text>
<text x="40" y="200" font-size="12" text-anchor="middle" font-family="sans-serif" transform="rotate(-90 40 200)">G</text>
<text x="88" y="345" font-size="10" font-family="sans-serif">A</text>
<text x="600" y="345" font-size="10" font-family="sans-serif">B</text>

<path d="M 100 300 Q 300 100 580 260" stroke="#2980b9" stroke-width="2.5" fill="none" />

<line x1="80" y1="210" x2="620" y2="330" stroke="#c0392b" stroke-width="2" stroke-dasharray="5,3" />
<circle cx="330" cy="270" r="4" fill="black" />

<circle cx="80" cy="210" r="4" fill="#27ae60" />
<circle cx="620" cy="330" r="4" fill="#8e44ad" />
<line x1="80" y1="210" x2="80" y2="350" stroke="#27ae60" stroke-dasharray="2,2" />
<line x1="620" y1="330" x2="620" y2="350" stroke="#8e44ad" stroke-dasharray="2,2" />

<text x="20" y="205" font-size="11" font-family="sans-serif" fill="`#27ae60`">mu_A</text>

<text x="625" y="325" font-size="11" font-family="sans-serif" fill="`#8e44ad`">mu_B</text>

<text x="330" y="295" font-size="10" font-family="sans-serif">tangent point at X0</text>

</svg>

### Process Flow Diagram

```mermaid
flowchart TD
    A[Enthalpy H: bond energy bookkeeping] --> D[Gibbs Free Energy G = H - TS]
    B[Entropy S: configurational + vibrational disorder] --> D
    D --> E[mu_i = partial G / partial n_i]
    E --> F{Equilibrium Condition}
    F -->|mu_i alpha = mu_i beta for all i| G[Two-Phase Equilibrium]
    G --> H[Common Tangent Geometrically Encodes Equal mu]
    E --> I[Chemical Potential Gradient]
    I --> J[J = -M * C * d(mu)/dx]
    J --> K{Sign of d(mu)/dX}
    K -->|Normal: same sign as dC/dx| L[Down-gradient Diffusion]
    K -->|Anomalous: near miscibility gap| M[Uphill Diffusion - Spinodal]
```

### Related Topics

- Regular solution model and derivation of the interaction parameter $\Omega$
- Activity coefficients and deviations from Raoult's/Henry's law in real solutions
- Spinodal decomposition and the thermodynamic origin of uphill diffusion
- Common tangent construction and binary phase diagram derivation
- Gibbs-Duhem relation applications in experimental activity determination
- CALPHAD modeling: sublattice models and Gibbs energy assessment
- Diffusion in Solids: Fick's laws vs. chemical-potential-driven flux formulations
- Third Law absolute entropy and standard-state reference conventions