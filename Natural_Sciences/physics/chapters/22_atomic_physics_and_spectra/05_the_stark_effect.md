## The Stark Effect

### Overview

The Stark effect describes the shifting and splitting of atomic energy levels and spectral lines in the presence of an external electric field. First observed experimentally by Johannes Stark in 1913, it is the electric-field analog of the Zeeman effect (magnetic splitting) and provides direct evidence of the quantization and symmetry properties of atomic states.

**Key Points**

- Arises from the interaction between an atom's electric dipole moment (permanent or induced) and an external electric field $\mathbf{E}$
- Two regimes: linear Stark effect (first-order, degenerate states) and quadratic Stark effect (second-order, non-degenerate states)
- Hydrogen exhibits a linear Stark effect due to the accidental degeneracy of states with the same principal quantum number $n$ but different orbital angular momentum $\ell$
- Most other atoms exhibit only the quadratic Stark effect because their $\ell$-degeneracy is lifted by the quantum defect

---

### Physical Origin

An atom placed in a uniform external electric field experiences a perturbation to its Hamiltonian:

$$H' = -\mathbf{d} \cdot \mathbf{E} = eEz$$

where $\mathbf{d} = -e\mathbf{r}$ is the electric dipole operator and the field is taken along the $z$-axis. This perturbation is odd under parity, since $z \to -z$ under spatial inversion. Consequently:

- Atomic eigenstates of definite parity have zero *permanent* dipole moment, so $\langle H' \rangle = 0$ to first order — **unless** there is degeneracy between states of opposite parity (as in hydrogen)
- In the absence of such degeneracy, the leading effect appears at second order in perturbation theory, giving an *induced* dipole moment proportional to $E$

---

### Quadratic Stark Effect (Non-Degenerate States)

For a non-degenerate state $|n\rangle$ of definite parity, first-order perturbation theory gives:

$$E_n^{(1)} = \langle n | H' | n \rangle = eE\langle n|z|n\rangle = 0$$

The first nonvanishing correction appears at second order:

$$E_n^{(2)} = \sum_{k \neq n} \frac{|\langle k|H'|n\rangle|^2}{E_n^{(0)} - E_k^{(0)}} = e^2E^2 \sum_{k\neq n}\frac{|\langle k|z|n\rangle|^2}{E_n^{(0)}-E_k^{(0)}}$$

This is conventionally written as:

$$E_n^{(2)} = -\frac{1}{2}\alpha_n E^2$$

where $\alpha_n$ is the **static electric polarizability** of the state. Since the energy shift scales as $E^2$, this is the *quadratic* (or second-order) Stark effect. It:

- Always lowers the energy of the ground state (since $\alpha_n > 0$ typically for the ground state)
- Applies to most atoms (alkali atoms, noble gases, most excited states) because their angular-momentum states are non-degenerate in energy
- Is the dominant effect for hydrogen's ground state ($n=1$) as well, since there is no $\ell$-degeneracy to exploit at $n=1$

**Example**

For the hydrogen ground state $|1s\rangle$, exact summation over the spectrum (including continuum states) yields the polarizability:

$$\alpha_{1s} = \frac{9}{2}a_0^3 \quad \text{(in Gaussian units, } a_0 = \text{Bohr radius)}$$

giving an energy shift $\Delta E = -\tfrac{9}{4}a_0^3 E^2$ (Gaussian units), a result obtainable exactly by a clever choice of variational trial function or by direct summation using the hydrogenic Green's function.

---

### Linear Stark Effect (Degenerate States, Hydrogen)

For hydrogen with $n \geq 2$, all states $\ell = 0, 1, \ldots, n-1$ are degenerate in energy (a special feature of the pure $1/r$ Coulomb potential). Since $z$ connects states of opposite parity ($\Delta \ell = \pm 1$), degenerate perturbation theory must be used within each $n$-manifold, and **first-order shifts do not vanish**.

**Parabolic Coordinates**

The degeneracy is resolved naturally using parabolic coordinates $(\xi, \eta, \phi)$ rather than spherical coordinates, since the Stark Hamiltonian separates in this basis. The good quantum numbers become the **parabolic quantum numbers** $(n_1, n_2, m)$, satisfying:

$$n = n_1 + n_2 + |m| + 1$$

The first-order energy shift is:

$$E^{(1)}_{n_1n_2m} = \frac{3}{2}n(n_1 - n_2)eEa_0$$

Defining the **electric quantum number** $k = n_1 - n_2$ (ranging over $-(n-1), \ldots, (n-1)$ in steps of 2), this is often written:

$$\Delta E = \frac{3}{2}nk\,eEa_0$$

**Key Points**

- The energy shift is **linear in $E$**, distinguishing this from the quadratic effect
- The $n=2$ level of hydrogen (4-fold degenerate: $2s$, and three $2p$ states) splits into three levels under a field, with shifts $\Delta E = 0, \pm 3eEa_0$
- This linear splitting is a direct consequence of the $1/r$ potential's dynamical symmetry (related to the Laplace–Runge–Lenz vector), and is destroyed by any deviation from a pure Coulomb potential (e.g., in alkali atoms, where core penetration breaks the $\ell$-degeneracy via the quantum defect)

---

### Energy Level Diagram: Hydrogen n=2 Stark Splitting (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 360" font-family="Helvetica, Arial, sans-serif">
<text x="320" y="25" font-size="16" text-anchor="middle" font-weight="bold">Hydrogen n=2 Stark Splitting (svg_diagram)</text>

<line x1="80" y1="60" x2="80" y2="320" stroke="black" stroke-width="1.5" />
<text x="40" y="65" font-size="12">Energy</text>
<text x="40" y="330" font-size="12">E → increases</text>

<line x1="120" y1="190" x2="220" y2="190" stroke="black" stroke-width="3" />
<text x="100" y="185" font-size="12" text-anchor="end">n=2</text>
<text x="130" y="180" font-size="11">(4-fold degenerate)</text>

<line x1="230" y1="190" x2="290" y2="190" stroke="gray" stroke-width="1" marker-end="url(#arrow)" />
<text x="260" y="175" font-size="11" text-anchor="middle">E field on</text>
<line x1="320" y1="110" x2="480" y2="110" stroke="#c0392b" stroke-width="3" />
<text x="490" y="115" font-size="12">k = +1: ΔE = +3eEa₀</text>
<line x1="320" y1="190" x2="480" y2="190" stroke="#2980b9" stroke-width="3" />
<text x="490" y="195" font-size="12">k = 0 (×2): ΔE = 0</text>
<line x1="320" y1="270" x2="480" y2="270" stroke="#27ae60" stroke-width="3" />
<text x="490" y="275" font-size="12">k = -1: ΔE = -3eEa₀</text>

<line x1="80" y1="190" x2="320" y2="190" stroke="black" stroke-dasharray="4,3" stroke-width="1" />
</svg>

---

### Comparison: Linear vs. Quadratic Stark Effect

| Property | Linear Stark Effect | Quadratic Stark Effect |
| --- | --- | --- |
| Field dependence | $\Delta E \propto E$ | $\Delta E \propto E^2$ |
| Systems | Hydrogen (and hydrogenic ions), $n \geq 2$ | Non-degenerate atoms (alkalis, most atoms); hydrogen $n=1$ |
| Origin | Degenerate opposite-parity states mixed by field | Second-order admixture of virtual states |
| Natural basis | Parabolic coordinates | Spherical coordinates |
| Sign of shift | Can be positive or negative (depends on $k$) | Typically negative for ground state (energy lowered) |

---

### Fine Structure, Ionization, and Higher-Order Effects

- **Fine structure competition**: At very weak fields, fine-structure splitting (spin-orbit coupling) can dominate over the Stark shift; the linear Stark regime requires $eEa_0 \gg$ fine-structure splitting for the simple parabolic-coordinate treatment to apply cleanly. At intermediate fields, the two effects must be diagonalized together.
- **Field ionization**: Because the Coulomb-plus-linear-field potential in one dimension is unbound (the potential barrier on one side becomes finite and eventually vanishes at large $E$), highly excited (Rydberg) states become metastable and can ionize via quantum tunneling. This is central to Rydberg-atom spectroscopy and controlled field-ionization detection schemes.
- **Higher-order terms**: For non-hydrogenic atoms, quartic and higher terms in $E$ become relevant only at very strong fields; these introduce corrections beyond the standard polarizability description. [Inference] The precise field strength at which such terms become significant is system-dependent and is best obtained from precision spectroscopy or ab initio calculation rather than a universal threshold.

---

### Applications

- **Plasma diagnostics**: Stark broadening of spectral lines (due to microfields from surrounding charged particles) is a standard technique for measuring electron density in plasmas (e.g., in astrophysical spectra and laboratory discharges)
- **Rydberg atom physics**: Because polarizability scales roughly as $n^7$, Rydberg states are extraordinarily sensitive to electric fields, forming the basis of Rydberg-atom electric-field sensors and quantum-information platforms using Stark-tunable dipole-dipole interactions
- **Precision spectroscopy**: Stark shifts must be controlled or corrected for in high-precision atomic clock and spectroscopy experiments, since stray fields can shift transition frequencies
- **Molecular physics**: The analogous molecular Stark effect (rotational/vibrational level splitting) underlies techniques like Stark spectroscopy and molecular beam electric deflection

---

### Worked Example: Polarizability-Based Shift

**Example**

Consider a non-degenerate atomic state with a known polarizability $\alpha = 5 \times 10^{-39}\ \text{C·m}^2/\text{V}$ (SI units) placed in a field $E = 10^5\ \text{V/m}$ (typical laboratory field). The energy shift is:

$$\Delta E = -\frac{1}{2}\alpha E^2 = -\frac{1}{2}(5\times10^{-39})(10^5)^2 \approx -2.5\times10^{-29}\ \text{J}$$

Converting to more convenient units ($1\ \text{eV} = 1.6\times10^{-19}\ \text{J}$):

$$\Delta E \approx -1.6\times10^{-10}\ \text{eV}$$

This illustrates why laboratory-strength fields typically produce very small quadratic shifts for ground-state atoms, whereas fields of order $10^7$–$10^8\ \text{V/m}$ (attainable in intense laser or ionic environments) are needed for shifts to approach fine-structure-scale energies. [Unverified] Exact thresholds depend strongly on the specific atomic species and state.

---

### Selection Rules and Symmetry Considerations

Under the electric dipole perturbation $H' = eEz$:

- Matrix elements $\langle n'\ell'm'|z|n\ell m\rangle$ are nonzero only for $\Delta \ell = \pm 1$, $\Delta m = 0$ (standard dipole selection rules)
- This is why degenerate hydrogen states with adjacent $\ell$ values (e.g., $2s$–$2p$) mix under the field, while states differing by $\Delta \ell \neq \pm 1$ do not couple directly at first order
- The quantum number $m$ remains good in the presence of a field along $z$, since $H'$ commutes with $L_z$

---

### Related Topics

- Zeeman Effect (magnetic-field level splitting) and Zeeman-Stark interplay in combined fields
- Rydberg Atoms and Field Ionization
- Perturbation Theory: Degenerate vs. Non-Degenerate Cases
- Stark Broadening in Plasma Spectroscopy
- Quantum Defect Theory (why linear Stark effect is unique to hydrogenic systems)
- Autler–Townes Splitting (AC Stark effect in laser fields)
- Molecular Stark Spectroscopy and Rotational Level Shifts
- Laplace–Runge–Lenz Vector and Hidden Symmetry of the Coulomb Problem