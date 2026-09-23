## Superconductivity


### Overview

Superconductivity is a state of matter in which certain materials, below a critical temperature $T_c$, exhibit exactly zero electrical resistance and expel magnetic fields from their interior (the Meissner effect). It represents a macroscopic quantum phenomenon: below $T_c$, a fraction of the conduction electrons condense into a single coherent quantum state described by a many-body wavefunction, fundamentally altering the material's electromagnetic response.

### Defining Phenomena

**Zero DC resistance**: Below $T_c$, resistivity drops abruptly (not gradually) to an experimentally unmeasurable value. Persistent current experiments in superconducting rings have set upper bounds on resistivity many orders of magnitude below that of copper, with decay times of the induced current exceeding $10^5$ years in some measurements — consistent with truly zero resistance rather than merely "very low" resistance.

**Meissner effect**: A superconductor actively expels an applied magnetic field from its bulk interior when cooled below $T_c$, rather than merely preventing flux from entering (which a hypothetical perfect conductor with $\sigma \to \infty$ would also do, but only for changes in field after the transition). The Meissner effect demonstrates that superconductivity is a distinct thermodynamic phase, not simply "perfect conductivity."

- The field penetrates only a thin surface layer, decaying exponentially with characteristic **London penetration depth** $\lambda_L$ (typically tens to hundreds of nm).
- Described by the **London equations**:

$$\mathbf{E} = \frac{\partial}{\partial t}(\Lambda \mathbf{J}_s), \qquad \nabla \times (\Lambda \mathbf{J}_s) = -\mathbf{B}$$

where $\Lambda = m/(n_s q^2)$, $n_s$ is the superconducting carrier density, giving $\nabla^2 \mathbf{B} = \mathbf{B}/\lambda_L^2$.

**(svg_diagram) Meissner Effect: Field Expulsion Below T_c**

<svg viewBox="0 0 600 260" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
<text x="300" y="20" text-anchor="middle" font-size="15" font-weight="bold">Meissner Effect: Field Expulsion Below T_c (svg_diagram)</text>

<text x="130" y="45" text-anchor="middle" font-size="12" font-weight="bold">T > T_c (normal)</text>

<circle cx="130" cy="150" r="70" fill="none" stroke="black" stroke-width="2"/>

<line x1="30" y1="90" x2="230" y2="90" stroke="blue" stroke-width="1.5"/>

<line x1="30" y1="120" x2="230" y2="120" stroke="blue" stroke-width="1.5"/>

<line x1="30" y1="150" x2="230" y2="150" stroke="blue" stroke-width="1.5"/>

<line x1="30" y1="180" x2="230" y2="180" stroke="blue" stroke-width="1.5"/>

<line x1="30" y1="210" x2="230" y2="210" stroke="blue" stroke-width="1.5"/>

<text x="130" y="240" text-anchor="middle" font-size="10">Field lines penetrate freely</text>

<text x="470" y="45" text-anchor="middle" font-size="12" font-weight="bold">T < T_c (superconducting)</text>

<circle cx="470" cy="150" r="70" fill="`#d6eaf8`" stroke="black" stroke-width="2"/>

<path d="M370,90 C 420,90 420,90 400,150 C 420,210 420,210 370,210" stroke="blue" stroke-width="1.5" fill="none"/>

<path d="M570,90 C 520,90 520,90 540,150 C 520,210 520,210 570,210" stroke="blue" stroke-width="1.5" fill="none"/>

<text x="470" y="240" text-anchor="middle" font-size="10">Field expelled from bulk (penetration depth λ_L)</text>

</svg>

### BCS Theory (Microscopic Mechanism, Conventional Superconductors)

Developed by Bardeen, Cooper, and Schrieffer (1957), BCS theory explains conventional (phonon-mediated) superconductivity.

**Cooper pairs**: Below $T_c$, electrons near the Fermi surface form bound pairs — **Cooper pairs** — mediated by an effective attractive interaction via lattice vibrations (phonons):

1. An electron moving through the lattice slightly attracts nearby positive ions, creating a transient region of enhanced positive charge density.
2. A second electron is attracted to this charge distortion before the lattice relaxes, producing a net effective attraction between the two electrons despite their direct Coulomb repulsion.
3. This attraction, however weak, allows two electrons with opposite momentum and spin ($\mathbf{k}\uparrow$, $-\mathbf{k}\downarrow$) to form a bound state (a Cooper pair) — remarkable because any attractive interaction, however weak, causes pairing instability of the Fermi sea at $T=0$ (Cooper's theorem).

**Energy gap**: Formation of the paired state opens an energy gap $\Delta$ at the Fermi surface — a minimum energy required to break a Cooper pair into two unpaired ("quasiparticle") excitations. At $T=0$:

$$\Delta(0) \approx 1.76\, k_B T_c$$

This is a specific, testable prediction of weak-coupling BCS theory, and has been broadly confirmed for many conventional superconductors, though the ratio deviates in strong-coupling materials.

**Macroscopic wavefunction**: All Cooper pairs (which behave as composite bosons) condense into the same quantum ground state, described by a single macroscopic wavefunction with a well-defined phase $\phi$. This phase coherence over macroscopic distances underlies both zero resistance (no scattering mechanism can dissipate energy from the collective condensate without breaking pairs, which costs energy $\geq \Delta$) and flux quantization.

**Isotope effect**: $T_c \propto M^{-\alpha}$ (where $M$ is the ionic mass, $\alpha \approx 0.5$ for many conventional superconductors) — direct experimental evidence implicating lattice vibrations (phonons) in the pairing mechanism.

### Type I vs. Type II Superconductors

**Type I**: Exhibit a single critical field $H_c$; below $H_c$, the Meissner state is complete (total flux expulsion); above $H_c$, superconductivity is abruptly destroyed. Mostly pure elemental superconductors (Hg, Pb, Sn, Al), with generally low $T_c$ (below $\sim 10\ \text{K}$).

**Type II**: Exhibit two critical fields, $H_{c1} < H_{c2}$:

- Below $H_{c1}$: complete Meissner state.
- Between $H_{c1}$ and $H_{c2}$: **mixed (vortex) state** — magnetic flux penetrates in discrete quantized flux tubes (vortices), each carrying one flux quantum $\Phi_0 = h/2e \approx 2.07 \times 10^{-15}\ \text{Wb}$. Each vortex has a normal (non-superconducting) core surrounded by circulating supercurrent.
- Above $H_{c2}$: superconductivity destroyed.
- Includes most technologically useful superconductors (Nb-Ti, Nb₃Sn, and all high-$T_c$ cuprates), since Type II materials can sustain superconductivity to much higher fields, enabling high-field magnet applications.

**Vortex pinning**: In practical Type II wires, defects and impurities "pin" vortices in place, preventing them from moving under applied current (vortex motion would dissipate energy and reintroduce resistance). Effective pinning is essential for achieving high critical current densities $J_c$ in applications like MRI magnets.

### High-Temperature Superconductors (Cuprates and Beyond)

Discovered in 1986 (Bednorz and Müller, La-Ba-Cu-O, $T_c \approx 35\ \text{K}$), cuprate superconductors reach $T_c$ well above the traditionally assumed BCS ceiling, with materials such as $\text{YBa}_2\text{Cu}_3\text{O}_7$ (YBCO, $T_c \approx 92\ \text{K}$, notable for exceeding the boiling point of liquid nitrogen, 77 K) and mercury-based cuprates reaching $T_c \approx 133\ \text{K}$ at ambient pressure.

- Structurally characterized by stacked $\text{CuO}_2$ planes, believed to host the primary superconducting currents.
- [Unverified] The precise microscopic pairing mechanism in cuprates remains an active research question; conventional phonon-mediated BCS pairing is generally considered insufficient to explain the observed $T_c$ values, and alternative mechanisms (e.g., mediated by spin fluctuations) have been proposed, but no complete, universally accepted microscopic theory analogous to BCS currently exists for these materials.
- Iron-based superconductors (discovered 2008) and other unconventional families (heavy-fermion superconductors) further illustrate that phonon-mediated BCS pairing is not the only route to superconductivity, though [Speculation] a full unified theoretical framework across all superconductor families is not established.

### Josephson Effect

When two superconductors are separated by a thin insulating barrier (a **Josephson junction**), Cooper pairs can tunnel across the barrier while preserving macroscopic phase coherence.

**DC Josephson effect**: A supercurrent flows across the junction with zero applied voltage, driven by the phase difference $\delta$ across the barrier:

$$I = I_c \sin(\delta)$$

**AC Josephson effect**: With a constant applied voltage $V$, an oscillating supercurrent results, with frequency:

$$f = \frac{2eV}{h}$$

This relation is exact and is exploited in the definition of the volt via the Josephson voltage standard, and forms the operating principle of **SQUIDs** (Superconducting Quantum Interference Devices), used for extremely sensitive magnetic field measurement.

### Applications

- **MRI and NMR magnets**: Nb-Ti superconducting solenoids provide the stable, high-field, low-power environment required for medical and research magnetic resonance.
- **Particle accelerators**: Superconducting RF cavities and dipole/quadrupole magnets (e.g., at the LHC, using Nb-Ti and Nb₃Sn) enable high-field beam steering with low energy loss.
- **SQUID magnetometry**: Used in magnetoencephalography and geophysical surveying due to extreme sensitivity to magnetic flux changes.
- **Quantum computing**: Josephson junctions form the basis of superconducting qubits (e.g., transmon qubits), a leading architecture in current quantum computing hardware.
- [Inference] Widespread grid-scale or ambient-condition applications remain limited primarily by the cryogenic cooling requirements of all currently confirmed superconductors; despite periodic claims of room-temperature superconductivity, none had been independently reproduced and broadly accepted within the mainstream physics community as of general knowledge available prior to this system's training cutoff, so any such claim should be checked against current peer-reviewed literature before being treated as established.

### Related Topics

- Band Theory of Solids
- BCS Theory: Cooper Pairs and the Energy Gap (in depth)
- Ginzburg-Landau Theory and Order Parameters
- Quantum Computing: Superconducting Qubit Architectures
- Magnetic Flux Quantization and SQUIDs
- Unconventional Superconductivity (Cuprates, Iron-Based, Heavy Fermion Systems)
- Phase Transitions and Critical Phenomena