## Phonons and Lattice Vibrations


### Overview

Atoms in a crystalline solid are not static; they vibrate about their equilibrium lattice positions due to thermal energy and zero-point quantum motion. Because atoms are coupled to their neighbors via interatomic bonding forces, these vibrations do not occur independently but propagate through the crystal as collective waves. Quantizing these lattice vibrational waves yields **phonons** — quanta of vibrational energy, analogous to photons as quanta of the electromagnetic field. Phonons govern thermal properties (specific heat, thermal conductivity), sound propagation, and mediate key electronic phenomena including electrical resistivity and conventional superconductivity.

### Classical Lattice Dynamics

**1D Monatomic Chain**: Consider $N$ identical atoms of mass $M$ connected by springs of force constant $C$, with equilibrium spacing $a$. Applying Newton's second law to atom $n$ with displacement $u_n$ from equilibrium:

$$M\ddot{u}_n = C(u_{n+1} - u_n) - C(u_n - u_{n-1}) = C(u_{n+1} + u_{n-1} - 2u_n)$$

Seeking traveling-wave solutions $u_n = u_0 e^{i(qna - \omega t)}$ yields the **dispersion relation**:

$$\omega(q) = 2\sqrt{\frac{C}{M}}\left|\sin\!\left(\frac{qa}{2}\right)\right|$$

- $\omega$ is periodic in $q$ with period $2\pi/a$, so all physically distinct modes lie within the **first Brillouin zone**, $-\pi/a < q \leq \pi/a$ (directly analogous to electronic Bloch states).
- **Long-wavelength limit** ($qa \ll 1$): $\omega \approx qa\sqrt{C/M}$, linear in $q$ — this is the **acoustic** regime, corresponding to ordinary sound waves, with sound velocity $v_s = a\sqrt{C/M}$.
- **Zone boundary** ($q = \pi/a$): $\omega$ reaches a maximum, $\omega_{max} = 2\sqrt{C/M}$, and the group velocity $d\omega/dq \to 0$ — a standing wave with zero net energy transport.

**1D Diatomic Chain**: With two atom types (masses $M_1, M_2$) per unit cell, the dispersion relation splits into two branches:

$$\omega_{\pm}^2 = C\left(\frac{1}{M_1}+\frac{1}{M_2}\right) \pm C\sqrt{\left(\frac{1}{M_1}+\frac{1}{M_2}\right)^2 - \frac{4\sin^2(qa/2)}{M_1M_2}}$$

- **Acoustic branch** ($\omega_-$): $\omega \to 0$ as $q \to 0$; atoms within a unit cell move in phase (like sound waves in a continuum).
- **Optical branch** ($\omega_+$): Remains finite as $q \to 0$; atoms within a unit cell move out of phase (oscillating against each other). Named "optical" because in ionic crystals, this out-of-phase motion of oppositely charged ions creates an oscillating dipole moment that couples strongly to electromagnetic (infrared) radiation.
- A **band gap** in frequency (no allowed vibrational modes) generally exists between the acoustic and optical branches — analogous to electronic band gaps arising from periodic potentials.

**(svg_diagram) Phonon Dispersion: Diatomic Chain**

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 320" font-family="sans-serif">
<text x="250" y="20" text-anchor="middle" font-size="15" font-weight="bold">Phonon Dispersion: Diatomic Chain (svg_diagram)</text>
<line x1="60" y1="270" x2="440" y2="270" stroke="black" stroke-width="1" />
<line x1="60" y1="270" x2="60" y2="40" stroke="black" stroke-width="1" />
<text x="445" y="275" font-size="12">q</text>
<text x="45" y="35" font-size="12">ω</text>
<text x="250" y="290" text-anchor="middle" font-size="11">-π/a</text>
<text x="440" y="290" text-anchor="middle" font-size="11">π/a</text>
<text x="60" y="290" text-anchor="middle" font-size="11">0 (-π/a)</text>
<path d="M 250,270 Q 345,190 440,150" stroke="blue" fill="none" stroke-width="2" />
<path d="M 250,270 Q 155,190 60,150" stroke="blue" fill="none" stroke-width="2" />
<text x="330" y="230" font-size="11" fill="blue">Acoustic branch</text>
<path d="M 250,90 Q 345,110 440,120" stroke="red" fill="none" stroke-width="2" />
<path d="M 250,90 Q 155,110 60,120" stroke="red" fill="none" stroke-width="2" />
<text x="330" y="95" font-size="11" fill="red">Optical branch</text>
<rect x="55" y="125" width="390" height="20" fill="#f4d03f" opacity="0.3" />
<text x="250" y="140" text-anchor="middle" font-size="10">Frequency gap (no allowed modes)</text>
</svg>

In three dimensions, a crystal with a basis of $p$ atoms per unit cell has $3p$ phonon branches per $\mathbf{q}$-point: 3 acoustic branches (1 longitudinal, 2 transverse) and $3(p-1)$ optical branches.

### Quantization: The Phonon as a Quasiparticle

Treating each normal mode of vibration as an independent quantum harmonic oscillator, the energy of a given mode $(\mathbf{q}, s)$ (branch $s$) is quantized:

$$E_{\mathbf{q},s} = \hbar\omega_s(\mathbf{q})\left(n_{\mathbf{q},s} + \frac{1}{2}\right)$$

- $n_{\mathbf{q},s} = 0, 1, 2, \dots$ is the number of **phonons** occupying that mode — quanta of lattice vibrational energy $\hbar\omega$.
- The $\frac{1}{2}\hbar\omega$ term represents **zero-point energy**, present even at $T=0$, a purely quantum mechanical effect with no classical analogue.
- Phonons are **bosons** (not conserved in number; they can be created and destroyed in scattering processes), and their thermal occupation at temperature $T$ follows the **Bose-Einstein distribution**:

$$\langle n_{\mathbf{q},s} \rangle = \frac{1}{\exp(\hbar\omega_s(\mathbf{q})/k_BT) - 1}$$

Phonons carry quasi-momentum $\hbar\mathbf{q}$ (defined modulo a reciprocal lattice vector, like electron crystal momentum) but not true momentum, since the lattice as a whole can absorb momentum.

### Phonon Contribution to Heat Capacity

**Dulong-Petit law** (classical, high-$T$ limit): Treating each atom as 3 classical harmonic oscillators (equipartition: $\frac{1}{2}k_BT$ per quadratic degree of freedom, 6 total per oscillator) predicts a temperature-independent molar heat capacity:

$$C_V = 3nR$$

Accurately describes most solids at room temperature and above but fails badly at low $T$, where $C_V$ is observed to vanish as $T \to 0$ — a failure classical physics cannot explain, resolved only by phonon quantization.

**Einstein model**: Treats all $3N$ oscillators as vibrating independently at a single frequency $\omega_E$. Correctly predicts $C_V \to 0$ as $T \to 0$ (since discrete quanta $\hbar\omega_E$ become hard to thermally excite), but the predicted approach to zero (exponential) is faster than experimentally observed.

**Debye model**: Improves on Einstein's model by treating the phonon spectrum as that of a continuous elastic medium up to a maximum cutoff frequency $\omega_D$ (the **Debye frequency**), chosen so the total number of modes equals $3N$. Yields the **Debye temperature** $\Theta_D = \hbar\omega_D/k_B$, and predicts:

$$C_V \propto T^3 \quad \text{for } T \ll \Theta_D \qquad (\text{Debye } T^3 \text{ law})$$



$$C_V \to 3nR \quad \text{for } T \gg \Theta_D \qquad (\text{recovers Dulong-Petit})$$

The Debye $T^3$ law is well confirmed experimentally at low temperature for most non-metallic and metallic solids (with metals requiring an additional linear-in-$T$ electronic contribution, $C_V = \gamma T + AT^3$, from conduction electrons near $E_F$).

### Phonons and Thermal Conductivity

In insulators (with no free electrons to conduct heat), thermal conductivity is carried almost entirely by phonons, treatable via a kinetic-theory expression analogous to gas kinetic theory:

$$\kappa = \frac{1}{3}C_V v_s \ell$$

where $v_s$ is phonon (sound) velocity and $\ell$ is the phonon mean free path, limited by:

- **Phonon-phonon scattering**: due to anharmonicity in the interatomic potential (a purely harmonic crystal would have infinite thermal conductivity, since phonons would never scatter off one another). The dominant anharmonic process is **Umklapp scattering**, in which the combined momentum of colliding phonons exceeds the first Brillouin zone boundary and is "folded back" via a reciprocal lattice vector — this process, unlike normal (momentum-conserving) scattering, directly degrades net heat current and dominates thermal resistance at moderate-to-high temperature.
- **Boundary/defect scattering**: dominates at low temperature (where phonon-phonon scattering becomes rare) and in nanostructured or highly defective materials, giving $\ell$ a temperature-independent geometric limit.

### Electron-Phonon Interaction

Phonons couple to the electronic system, with far-reaching consequences:

- **Electrical resistivity in metals**: Above the Debye temperature, electron-phonon scattering dominates resistivity, giving $\rho \propto T$; at low temperature, the Bloch-Grüneisen formula predicts $\rho \propto T^5$.
- **Conventional superconductivity**: As described by BCS theory, phonon-mediated attraction between electrons near the Fermi surface produces Cooper pairing — direct experimental confirmation comes from the **isotope effect**, $T_c \propto M^{-\alpha}$.
- **Polarons**: In some materials, strong electron-phonon coupling causes an electron to locally distort the surrounding lattice, forming a composite quasiparticle (electron + associated lattice distortion) with enhanced effective mass.

### Measurement Techniques

- **Inelastic neutron scattering**: The primary experimental technique for mapping full phonon dispersion relations $\omega(\mathbf{q})$ across the Brillouin zone, exploiting the comparable energy/momentum scales of thermal neutrons and phonons.
- **Raman and infrared spectroscopy**: Probe zone-center ($\mathbf{q} \approx 0$) optical phonon modes via light scattering/absorption selection rules, widely used for rapid, non-destructive material characterization (e.g., identifying crystal phases, strain, doping levels).
- **Inelastic X-ray scattering**: An alternative to neutron scattering, particularly useful for small samples or where large neutron flux is unavailable.

### Related Topics

- Band Theory of Solids
- Superconductivity (BCS Theory and the Isotope Effect)
- Specific Heat of Solids: Debye and Einstein Models (in depth)
- Thermal Conductivity and Umklapp Scattering
- Crystal Structure and Reciprocal Lattice
- Anharmonic Effects: Thermal Expansion and Grüneisen Parameter
- Raman Spectroscopy for Materials Characterization