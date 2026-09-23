## Magnetic Properties of Solids


### Overview

The magnetic behavior of solids arises from the quantum mechanical properties of their constituent electrons — orbital motion and intrinsic spin — combined with the Pauli exclusion principle, electron-electron interactions, and the crystal environment. Materials are classified into distinct categories (diamagnetic, paramagnetic, ferromagnetic, antiferromagnetic, ferrimagnetic) based on how they respond to an applied magnetic field $\mathbf{H}$ and whether they exhibit spontaneous magnetic order in the absence of a field.

### Fundamental Origin: Magnetic Moments

The magnetic moment of an atom arises from two contributions:

**Orbital angular momentum**: An electron orbiting the nucleus constitutes a microscopic current loop, producing an orbital magnetic moment:

$$\boldsymbol{\mu}_L = -\frac{e}{2m_e}\mathbf{L}$$

**Spin angular momentum**: Each electron carries an intrinsic spin magnetic moment:

$$\boldsymbol{\mu}_S = -g_s\frac{e}{2m_e}\mathbf{S}, \qquad g_s \approx 2$$

The total atomic magnetic moment combines both contributions (via Hund's rules and spin-orbit coupling, described by the Landé $g$-factor for the total angular momentum $\mathbf{J} = \mathbf{L}+\mathbf{S}$). In many solids, particularly those with itinerant (delocalized) electrons, orbital moments are largely **quenched** by the crystal field, leaving spin as the dominant contribution.

### Classification by Macroscopic Response

The **magnetization** $\mathbf{M}$ (magnetic moment per unit volume) relates to the applied field via the magnetic susceptibility $\chi$:

$$\mathbf{M} = \chi \mathbf{H}$$

| Type | Sign/magnitude of $\chi$ | Microscopic origin | Field dependence |
| --- | --- | --- | --- |
| Diamagnetic | Small negative ($\sim -10^{-5}$) | Induced opposition to applied field (Lenz's law at atomic scale) | $T$-independent |
| Paramagnetic | Small positive ($\sim 10^{-3}$ to $10^{-5}$) | Alignment of pre-existing, independent atomic moments | $\propto 1/T$ (Curie law) |
| Ferromagnetic | Large positive, $\chi \gg 1$ | Spontaneous parallel alignment of moments (exchange interaction) | Nonlinear, hysteretic |
| Antiferromagnetic | Small positive | Spontaneous antiparallel alignment, zero net moment | Peaks at $T_N$ |
| Ferrimagnetic | Large positive | Antiparallel alignment of unequal sublattice moments | Nonlinear, net moment |

### Diamagnetism

Present in **all** materials (a fundamental response of any charged system to an applied field), but only dominant when no permanent magnetic moment exists (e.g., closed-shell atoms/ions, most covalent/ionic solids).

**Mechanism**: An applied field induces a change in electron orbital motion (via Faraday's law acting at the atomic scale) that opposes the applied field, per Lenz's law — producing a small induced moment antiparallel to $\mathbf{H}$.

**Classical (Langevin) estimate**:

$$\chi_{dia} = -\frac{\mu_0 n e^2}{6m_e}\langle r^2 \rangle$$

where $n$ is the number density of atoms and $\langle r^2 \rangle$ is the mean-square orbital radius of the electrons.

- Temperature-independent (to good approximation).
- Examples: noble gases, ionic crystals (NaCl), most organic compounds, and notably **superconductors**, which exhibit perfect diamagnetism ($\chi = -1$) via the Meissner effect — a qualitatively distinct, macroscopic quantum mechanism rather than the ordinary atomic-scale effect described above.

### Paramagnetism

Occurs in materials with atoms/ions possessing a net permanent magnetic moment (e.g., unpaired electrons in partially filled shells — transition metal ions, rare earth ions, free radicals, and conduction electrons in metals) but with negligible interaction between neighboring moments, so thermal agitation keeps them randomly oriented in the absence of a field.

**Curie's Law**: With an applied field, moments partially align, with the alignment opposed by thermal randomization:

$$\chi = \frac{C}{T}, \qquad C = \frac{\mu_0 n \mu_{eff}^2}{3k_B}$$

where $\mu_{eff}$ is the effective magnetic moment per atom (from Hund's-rule ground state term).

**Pauli paramagnetism** (distinct mechanism, in metals): Conduction electrons, being fermions filling a Fermi sea, only allow spins near $E_F$ to respond to an applied field (most electrons are Pauli-blocked from flipping spin since paired states are already occupied). This yields a weak, essentially **temperature-independent** paramagnetic contribution:

$$\chi_{Pauli} \propto g(E_F)$$

proportional to the density of states at the Fermi level — a direct link back to band theory. This behavior contrasts with the $1/T$ Curie law of localized-moment paramagnetism.

### Ferromagnetism

Exhibits **spontaneous magnetization** — net magnetic moment even in zero applied field — below a critical temperature, the **Curie temperature** $T_C$.

**Exchange interaction**: The dominant mechanism is not direct magnetic dipole-dipole interaction (too weak by orders of magnitude to explain observed ordering temperatures), but the **quantum mechanical exchange interaction**, arising from the interplay of the Pauli exclusion principle and Coulomb repulsion. Modeled via the **Heisenberg Hamiltonian**:

$$H = -J\sum_{\langle i,j \rangle} \mathbf{S}_i \cdot \mathbf{S}_j$$

- $J > 0$ favors parallel spin alignment (ferromagnetic coupling).
- $J < 0$ favors antiparallel alignment (antiferromagnetic coupling).
- The sign and magnitude of $J$ depend on orbital overlap and electron configuration (formalized in various regimes by direct exchange, superexchange, and RKKY interaction mechanisms, depending on material class).

**Above $T_C$**: Thermal energy overcomes the exchange interaction, and the material becomes paramagnetic, following the **Curie-Weiss law**:

$$\chi = \frac{C}{T - T_C}$$

**Domains and hysteresis**: Below $T_C$, a bulk ferromagnet typically does not show net magnetization macroscopically because it subdivides into **magnetic domains** — regions of uniform spontaneous magnetization pointing in different directions, minimizing total magnetostatic energy. Applying an external field grows favorably oriented domains at the expense of others (via domain wall motion) and/or rotates domain magnetization, producing the characteristic **hysteresis loop**:

**(svg_diagram) Ferromagnetic Hysteresis Loop**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 400" font-family="sans-serif">
<text x="250" y="20" text-anchor="middle" font-size="15" font-weight="bold">Ferromagnetic Hysteresis Loop (svg_diagram)</text>
<line x1="50" y1="200" x2="450" y2="200" stroke="black" stroke-width="1" />
<line x1="250" y1="30" x2="250" y2="370" stroke="black" stroke-width="1" />
<text x="460" y="205" font-size="12">H</text>
<text x="255" y="40" font-size="12">M</text>
<path d="M 100,190 C 150,60 200,60 250,60 C 320,60 380,90 400,100" stroke="blue" fill="none" stroke-width="2" />
<path d="M 400,100 C 380,150 320,180 250,200 C 180,220 130,240 100,320" stroke="blue" fill="none" stroke-width="2" />
<path d="M 100,320 C 130,240 180,220 250,200 C 320,180 380,150 400,100" stroke="blue" fill="none" stroke-width="2" opacity="0" />
<path d="M 400,300 C 380,240 320,220 250,200 C 180,180 130,150 100,80" stroke="green" fill="none" stroke-width="2" />
<path d="M100,80 C 150,140 200,180 250,200 C 300,220 350,260 400,300" stroke="green" fill="none" stroke-width="2" opacity="0" />
<circle cx="250" cy="60" r="3" fill="black" />
<text x="255" y="55" font-size="10">M_s (saturation)</text>
<circle cx="285" cy="200" r="3" fill="black" />
<text x="290" y="215" font-size="10">H_c (coercivity)</text>
<circle cx="250" cy="130" r="3" fill="black" />
<text x="255" y="125" font-size="10">M_r (remanence)</text>

<text x="250" y="390" text-anchor="middle" font-size="10">Enclosed area = energy dissipated per cycle</text>

</svg>

- **Saturation magnetization** $M_s$: maximum magnetization when all domains are fully aligned.
- **Remanence** $M_r$: magnetization remaining after the field is removed.
- **Coercivity** $H_c$: reverse field required to bring $M$ back to zero.
- **Soft magnetic materials** (small $H_c$, e.g., Fe-Si alloys) minimize hysteresis losses — used in transformer cores.
- **Hard magnetic materials** (large $H_c$, e.g., Nd-Fe-B, Alnico) retain magnetization strongly — used in permanent magnets.

**Examples**: Fe ($T_C \approx 1043\ \text{K}$), Co ($T_C \approx 1400\ \text{K}$), Ni ($T_C \approx 630\ \text{K}$), Gd.

### Antiferromagnetism

Exchange interaction favors antiparallel alignment ($J<0$) between neighboring moments, typically modeled as two interpenetrating sublattices with equal and opposite moments, yielding **zero net macroscopic magnetization** in the ordered state.

- Ordering disappears above the **Néel temperature** $T_N$, above which the material is paramagnetic.
- Susceptibility peaks at $T_N$ and decreases on both sides (rises again above $T_N$ following a Curie-Weiss-like law with a negative Weiss constant).
- Examples: MnO, NiO, Cr metal.
- Detected experimentally primarily via neutron diffraction, since neutrons (possessing spin but no charge) scatter from magnetic moment ordering directly, unlike X-rays.

### Ferrimagnetism

Two (or more) sublattices with antiparallel alignment, as in antiferromagnets, but with **unequal magnitude** moments on each sublattice, resulting in a **net spontaneous magnetization** — macroscopically resembling ferromagnetism but microscopically closer to antiferromagnetism.

- Ordering also vanishes above a Curie temperature.
- Classic example: **magnetite** ($\text{Fe}_3\text{O}_4$), the first magnetic material known to humanity (lodestone), and various **ferrites** (e.g., $\text{MFe}_2\text{O}_4$, used extensively in high-frequency inductor cores and microwave devices due to their combination of magnetism and high electrical resistivity, which suppresses eddy current losses).

### Itinerant vs. Localized Magnetism

- **Localized moment picture**: Appropriate for insulating magnetic materials and rare-earth metals, where magnetic electrons ($d$ or $f$ shell) remain tied to specific atomic sites; well described by the Heisenberg model.
- **Itinerant (band) magnetism**: Appropriate for metallic ferromagnets like Fe, Co, Ni, where the magnetic electrons are also the conduction electrons. Described by the **Stoner model**, in which ferromagnetism arises when the exchange energy gain from spontaneously splitting spin-up and spin-down bands exceeds the kinetic energy cost of populating a higher band — the **Stoner criterion**:

$$I \cdot g(E_F) > 1$$

where $I$ is an exchange interaction parameter and $g(E_F)$ is the density of states at the Fermi level (again connecting directly to band theory: materials with narrow, high-DOS $d$-bands near $E_F$, like Fe/Co/Ni, are far more prone to itinerant ferromagnetism).

### Applications

- **Data storage**: Hard disk drives and magnetic tape rely on stable, switchable domains in hard/semi-hard magnetic thin films; modern read heads exploit **giant magnetoresistance (GMR)** and **tunneling magnetoresistance (TMR)**, spintronic effects sensitive to relative magnetic alignment across thin-film stacks.
- **Transformers and inductors**: Require soft magnetic cores (low $H_c$, high permeability) to minimize hysteresis and eddy-current losses.
- **Permanent magnets**: Motors, generators, and magnetic couplings rely on hard magnetic materials (Nd-Fe-B, SmCo) with high $M_r$ and $H_c$.
- **MRI**: While the strong static field is superconducting-magnet-generated, some specialized designs and shim components use permanent or soft magnetic materials for field shaping.
- **Spintronics**: An emerging field exploiting electron spin, not just charge, for information processing (e.g., spin-transfer torque MRAM), building directly on GMR/TMR physics.

### Related Topics

- Band Theory of Solids
- Exchange Interaction and the Heisenberg/Stoner Models
- Neutron Diffraction and Magnetic Structure Determination
- Giant Magnetoresistance (GMR) and Spintronics
- Superconductivity (Meissner Effect as Perfect Diamagnetism)
- Phase Transitions: Curie/Néel Points and Critical Exponents
- Magnetic Domain Theory and Micromagnetics