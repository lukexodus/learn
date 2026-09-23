## Conductors, Insulators, and Semiconductors


### Overview

The classification of solids as conductors, insulators, or semiconductors is a direct consequence of band theory: it depends on the size of the band gap $E_g$ separating the valence band from the conduction band, and on how completely the valence band is filled at a given temperature. This classification determines electrical conductivity $\sigma$, which spans roughly 25 orders of magnitude across materials — from $\sim 10^{-18}\ \text{S/m}$ for good insulators to $\sim 10^{8}\ \text{S/m}$ for good conductors.

### Classification Criterion

At absolute zero, electrons fill available energy states from the lowest energy up to the Fermi energy $E_F$. Whether the resulting configuration conducts depends on band filling:

| Category | Band structure at $T = 0\,\text{K}$ | Typical $E_g$ |
| --- | --- | --- |
| Conductor (metal) | Partially filled band, or overlapping filled/empty bands | No gap (or negative/zero) |
| Semiconductor | Full valence band, empty conduction band, small gap | $\sim 0.1$–$3\ \text{eV}$ |
| Insulator | Full valence band, empty conduction band, large gap | $\gtrsim 4\ \text{eV}$ |

The distinction between semiconductor and insulator is one of degree, not kind — the same band picture applies to both, and the boundary ($E_g \approx 3$–$4\ \text{eV}$) is a convention rather than a sharp physical threshold.

### Conductors (Metals)

**Band picture**: The Fermi level $E_F$ lies inside a band, or a filled band overlaps energetically with the next (empty) band, so there is effectively no gap to cross.

**Mechanism of conduction**:

- Electrons at states near $E_F$ can be excited into adjacent unoccupied $\mathbf{k}$-states by an arbitrarily small applied electric field, since neighboring states differ in energy by an infinitesimal amount.
- This yields high conductivity even as $T \to 0\ \text{K}$ (limited only by residual impurity/defect scattering, giving finite residual resistivity).

**Temperature dependence**:

- Resistivity **increases** with temperature. Increased lattice vibration amplitude (phonon population) increases electron-phonon scattering, reducing the mean free path and mobility.
- Approximate relation (Matthiessen's rule):

$$\rho(T) = \rho_{\text{impurity}} + \rho_{\text{phonon}}(T)$$

where $\rho_{\text{phonon}}(T) \propto T$ at high temperature (above the Debye temperature) and $\propto T^5$ at low temperature (Bloch–Grüneisen behavior).

**Carrier density**: Essentially temperature-independent; set by the fixed number of valence electrons per atom (e.g., $n \sim 10^{28}\text{–}10^{29}\ \text{m}^{-3}$ for typical metals).

**Examples**: Alkali metals (Na, K — one electron in an otherwise empty band), and metals with overlapping bands such as Mg and the alkaline earths (filled $s$-band overlapping empty $p$-band) and transition metals (Cu, Fe — overlapping $s$ and $d$ bands).

### Insulators

**Band picture**: Valence band completely full; conduction band completely empty; large gap between them.

**Mechanism (lack of conduction)**:

- Thermal energy at room temperature is $k_BT \approx 0.025\ \text{eV}$, negligible compared to $E_g \gtrsim 4\ \text{eV}$.
- The probability of thermal excitation across the gap, governed by Fermi-Dirac statistics, scales as $\exp(-E_g / 2k_BT)$, making the excited carrier density vanishingly small.
- With no carriers in either band capable of easily changing $\mathbf{k}$-state (full bands cannot carry net current since contributions from all filled states cancel), the material does not conduct under ordinary fields.

**Dielectric breakdown**: Under sufficiently strong electric fields, insulators can undergo breakdown — mechanisms include impact ionization (accelerated carriers ionize lattice atoms, causing an avalanche) and direct tunneling across the gap at high field strength. [Inference] Practical breakdown fields are strongly dependent on material quality, defect density, and geometry, so quoted breakdown-field values in reference tables should be treated as approximate.

**Examples**: Diamond ($E_g \approx 5.5\ \text{eV}$), silicon dioxide/quartz ($E_g \approx 9\ \text{eV}$), most ionic crystals (NaCl, $E_g \approx 8.5\ \text{eV}$), and many polymers.

### Semiconductors

**Band picture**: Same qualitative structure as insulators (full valence band, empty conduction band at $T=0$), but with a small enough gap that thermal excitation, doping, or optical absorption produces technologically useful carrier densities.

#### Intrinsic Semiconductors

Pure, undoped semiconductor material. At $T > 0$:

- Thermal energy promotes some electrons from the valence band (VB) to the conduction band (CB), creating electron-hole pairs.
- Each excited electron leaves a **hole** (missing electron) in the VB, which behaves as a positive charge carrier with effective mass $m_h^*$.
- Electron and hole concentrations are equal: $n = p = n_i$ (intrinsic carrier concentration).

Intrinsic carrier concentration:

$$n_i = \sqrt{N_c N_v}\, \exp\!\left(-\frac{E_g}{2k_BT}\right)$$

where $N_c$ and $N_v$ are the effective densities of states in the conduction and valence bands, respectively. This exponential dependence on $T$ and $E_g$ is the defining signature of semiconductor conduction.

**Fermi level location**: For an intrinsic semiconductor, $E_F$ lies near mid-gap (exactly at mid-gap only if $N_c = N_v$, i.e., equal electron and hole effective masses).

#### Extrinsic (Doped) Semiconductors

Deliberate introduction of impurity atoms modifies carrier concentrations by orders of magnitude relative to $n_i$.

**n-type doping**:

- Dopant atoms with one more valence electron than the host (e.g., phosphorus, arsenic in silicon) are called **donors**.
- The extra electron is loosely bound, occupying a donor level $E_d$ just below the conduction band edge $E_c$ (typically tens of meV below).
- At room temperature, nearly all donors are ionized, contributing free electrons to the CB; electrons become the **majority carriers**, holes the **minority carriers**.
- $E_F$ shifts upward, closer to $E_c$.

**p-type doping**:

- Dopant atoms with one fewer valence electron (e.g., boron, gallium in silicon) are called **acceptors**.
- An acceptor level $E_a$ lies just above the valence band edge $E_v$; acceptors readily accept an electron from the VB, leaving a hole.
- Holes become majority carriers, electrons minority carriers; $E_F$ shifts downward, closer to $E_v$.

**Charge neutrality condition** (with fully ionized dopants, no compensation):

$$n \approx N_d \quad (\text{n-type}), \qquad p \approx N_a \quad (\text{p-type})$$

**Mass-action law** (holds regardless of doping level, assuming non-degenerate statistics):

$$np = n_i^2$$

**(svg_diagram) Energy Levels: Intrinsic vs. n-type vs. p-type Semiconductor**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 260" font-family="sans-serif">
<text x="360" y="18" text-anchor="middle" font-size="15" font-weight="bold">Energy Levels: Intrinsic vs. n-type vs. p-type (svg_diagram)</text>

<g>
<text x="110" y="40" text-anchor="middle" font-size="12" font-weight="bold">Intrinsic</text>
<rect x="60" y="55" width="100" height="55" fill="white" stroke="black" />
<text x="110" y="85" text-anchor="middle" font-size="10">Conduction band</text>
<rect x="60" y="150" width="100" height="55" fill="#7fb3d5" stroke="black" />
<text x="110" y="180" text-anchor="middle" font-size="10">Valence band</text>
<line x1="55" y1="132" x2="165" y2="132" stroke="red" stroke-width="1.5" stroke-dasharray="3,2" />
<text x="168" y="135" font-size="9" fill="red">E_F (mid-gap)</text>
</g>

<g>
<text x="360" y="40" text-anchor="middle" font-size="12" font-weight="bold">n-type</text>
<rect x="310" y="55" width="100" height="55" fill="white" stroke="black" />
<text x="360" y="85" text-anchor="middle" font-size="10">Conduction band</text>
<line x1="305" y1="112" x2="415" y2="112" stroke="green" stroke-width="2" />
<text x="418" y="115" font-size="9" fill="green">Donor level (E_d)</text>
<rect x="310" y="150" width="100" height="55" fill="#7fb3d5" stroke="black" />
<text x="360" y="180" text-anchor="middle" font-size="10">Valence band</text>
<line x1="305" y1="100" x2="415" y2="100" stroke="red" stroke-width="1.5" stroke-dasharray="3,2" />
<text x="418" y="102" font-size="9" fill="red">E_F (near E_c)</text>
</g>

<g>
<text x="610" y="40" text-anchor="middle" font-size="12" font-weight="bold">p-type</text>
<rect x="560" y="55" width="100" height="55" fill="white" stroke="black" />
<text x="610" y="85" text-anchor="middle" font-size="10">Conduction band</text>
<line x1="555" y1="145" x2="665" y2="145" stroke="orange" stroke-width="2" />
<text x="668" y="148" font-size="9" fill="orange">Acceptor level (E_a)</text>
<rect x="560" y="150" width="100" height="55" fill="#7fb3d5" stroke="black" />
<text x="610" y="180" text-anchor="middle" font-size="10">Valence band</text>
<line x1="555" y1="158" x2="665" y2="158" stroke="red" stroke-width="1.5" stroke-dasharray="3,2" />
<text x="668" y="172" font-size="9" fill="red">E_F (near E_v)</text>
</g>
</svg>

### Temperature Dependence of Semiconductor Conductivity

Semiconductor conductivity behaves oppositely to metals with respect to temperature:

$$\sigma = q(n\mu_n + p\mu_p)$$

- **Low-to-moderate temperature (extrinsic/saturation region)**: Nearly all dopants are ionized; carrier concentration is roughly constant (set by $N_d$ or $N_a$), so $\sigma$ changes only weakly, tracking the temperature dependence of mobility $\mu$ (which decreases with $T$ due to increased phonon scattering — similar mechanism to metals).
- **High temperature (intrinsic region)**: Thermally generated intrinsic carriers ($n_i \propto \exp(-E_g/2k_BT)$) eventually dominate over the fixed dopant concentration, causing $\sigma$ to rise sharply with $T$.
- **Very low temperature (freeze-out region)**: Insufficient thermal energy to ionize dopants; carrier concentration and $\sigma$ drop sharply.

This exponential rise in carrier density with temperature (in the intrinsic regime) is the key qualitative difference from metals, where increasing $T$ *reduces* conductivity.

### Comparative Summary

| Property | Conductor | Semiconductor | Insulator |
| --- | --- | --- | --- |
| Band gap | None/overlapping | Small ($\sim 0.1$–$3\ \text{eV}$) | Large ($\gtrsim 4\ \text{eV}$) |
| $\sigma$ at room temp | $10^6$–$10^8\ \text{S/m}$ | $10^{-6}$–$10^{4}\ \text{S/m}$ | $< 10^{-10}\ \text{S/m}$ |
| Effect of increasing $T$ | $\sigma$ decreases | $\sigma$ increases (intrinsic regime) | Negligible change (until breakdown) |
| Carrier source | Intrinsic free electrons | Thermal excitation + doping | None (ideally) |
| Doping sensitivity | Minimal effect | Extremely sensitive (ppm-level dopants change $\sigma$ by orders of magnitude) | N/A |

**Example**

Silicon doped with 1 part per million phosphorus ($N_d \approx 5 \times 10^{16}\ \text{cm}^{-3}$) increases electron concentration from $n_i \approx 1.5 \times 10^{10}\ \text{cm}^{-3}$ (undoped, 300 K) to $n \approx N_d$, a roughly six-order-of-magnitude increase in majority carrier concentration, and a correspondingly large increase in conductivity.

### Related Topics

- Band Theory of Solids
- Fermi-Dirac Statistics and the Fermi Level
- p-n Junctions and Diode Physics
- Carrier Transport: Drift, Diffusion, and Mobility
- Hall Effect
- Superconductivity
- Wide-Bandgap Semiconductors (GaN, SiC) and Applications