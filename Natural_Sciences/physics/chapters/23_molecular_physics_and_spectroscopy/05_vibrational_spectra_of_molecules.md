## Vibrational Spectra of Molecules

### Overview

Vibrational spectroscopy probes the quantized oscillatory motion of nuclei about their equilibrium positions on the molecular potential energy surface. Observed primarily via infrared (IR) absorption and Raman scattering, it provides detailed information on bond strength (force constants), molecular structure, and — through combination with rotational fine structure — some of the most precise structural data available for gas-phase molecules.

**Key Points**

- The simplest model treats each vibrational mode as a **quantum harmonic oscillator**, governed by the curvature of the potential energy surface at its minimum
- Selection rule for the harmonic oscillator (IR-active, dipole mechanism): $\Delta v = \pm 1$
- Real molecular potentials are **anharmonic**, permitting weak overtone transitions and causing bond dissociation at high energy
- Polyatomic molecules possess multiple **normal modes**, each independently quantized in the harmonic approximation

---

### The Harmonic Oscillator Model

Near the equilibrium bond length $R_e$, the Born-Oppenheimer potential energy surface $E_n(R)$ can be Taylor-expanded:

$$E_n(R) \approx E_n(R_e) + \frac{1}{2}k(R-R_e)^2 + \ldots$$

where $k = \left.\dfrac{d^2E_n}{dR^2}\right|_{R_e}$ is the **force constant**. Truncating at quadratic order gives the quantum harmonic oscillator Hamiltonian for nuclear motion:

$$H_{\text{vib}} = \frac{p^2}{2\mu} + \frac{1}{2}k(R-R_e)^2$$

with quantized energy levels:

$$E_v = \hbar\omega\left(v+\frac{1}{2}\right), \qquad v = 0,1,2,\ldots$$

where $\omega = \sqrt{k/\mu}$ is the classical vibrational angular frequency and $\mu$ is the reduced mass.

**Key Points**

- Equally spaced energy levels ($\Delta E = \hbar\omega$ between adjacent levels) are the hallmark of the harmonic approximation
- The **zero-point energy** $E_0 = \tfrac{1}{2}\hbar\omega$ is a purely quantum mechanical residual vibrational energy that persists even at $T=0$, a direct consequence of the uncertainty principle
- Stiffer bonds (larger $k$) and lighter reduced masses (smaller $\mu$) give higher vibrational frequencies — this is why X-H stretches (small $\mu$) appear at characteristically high IR frequencies

---

### Selection Rules for Vibrational Transitions

**IR (electric dipole) selection rule, harmonic approximation:**

$$\Delta v = \pm 1$$

with the additional requirement that the **dipole moment must change during the vibration**:

$$\left(\frac{d\mu}{dQ}\right)_{Q=0} \neq 0$$

where $Q$ is the normal-mode coordinate. This follows from expanding the dipole moment operator in the transition matrix element and applying the harmonic oscillator's ladder-operator selection rule ($\langle v\pm1|Q|v\rangle \neq 0$, all other $\langle v'|Q|v\rangle = 0$).

**Key Points**

- Homonuclear diatomics ($H_2$, $N_2$, $O_2$) have zero dipole moment at all bond lengths by symmetry, and are therefore **IR-inactive** — they show no pure vibrational absorption spectrum
- Vibrations that do not change a molecule's dipole moment (certain symmetric stretches in centrosymmetric molecules) are also IR-inactive, even though the molecule itself has a nonzero static dipole in other configurations
- **Raman scattering**, governed by a different selection rule (change in molecular polarizability, $d\alpha/dQ \neq 0$), can detect vibrations that are IR-inactive — the two techniques are complementary, and for centrosymmetric molecules the **mutual exclusion rule** applies: a mode active in IR is inactive in Raman and vice versa

---

### Vibrational Energy Levels and Transitions (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380" font-family="Helvetica, Arial, sans-serif">
<text x="320" y="22" font-size="15" text-anchor="middle" font-weight="bold">Harmonic vs. Anharmonic Vibrational Levels (svg_diagram)</text>

<line x1="70" y1="340" x2="70" y2="45" stroke="black" stroke-width="1.5" />
<line x1="70" y1="340" x2="600" y2="340" stroke="black" stroke-width="1.5" />
<text x="330" y="365" font-size="12" text-anchor="middle">Internuclear Distance, R</text>

<path d="M 130,340 Q 200,60 270,340" fill="none" stroke="#2980b9" stroke-width="2" />
<text x="200" y="55" font-size="11" text-anchor="middle" fill="#2980b9">Harmonic</text>

<line x1="155" y1="300" x2="245" y2="300" stroke="#2980b9" stroke-width="2" />
<text x="250" y="304" font-size="10">v=0</text>
<line x1="150" y1="255" x2="250" y2="255" stroke="#2980b9" stroke-width="2" />
<text x="255" y="259" font-size="10">v=1</text>
<line x1="145" y1="210" x2="255" y2="210" stroke="#2980b9" stroke-width="2" />
<text x="260" y="214" font-size="10">v=2</text>
<line x1="140" y1="165" x2="260" y2="165" stroke="#2980b9" stroke-width="2" />
<text x="265" y="169" font-size="10">v=3</text>

<path d="M 380,340 Q 400,90 460,95 Q 520,100 570,180" fill="none" stroke="#c0392b" stroke-width="2" />
<text x="470" y="80" font-size="11" text-anchor="middle" fill="#c0392b">Anharmonic (Morse)</text>

<line x1="400" y1="300" x2="480" y2="300" stroke="#c0392b" stroke-width="2" />
<text x="485" y="304" font-size="10">v=0</text>
<line x1="396" y1="258" x2="484" y2="258" stroke="#c0392b" stroke-width="2" />
<text x="489" y="262" font-size="10">v=1</text>
<line x1="393" y1="222" x2="490" y2="222" stroke="#c0392b" stroke-width="2" />
<text x="495" y="226" font-size="10">v=2</text>
<line x1="391" y1="192" x2="496" y2="192" stroke="#c0392b" stroke-width="2" />
<text x="501" y="196" font-size="10">v=3</text>
<text x="500" y="150" font-size="10" fill="#c0392b">levels converge → dissociation limit</text>
</svg>

---

### Anharmonicity and the Morse Potential

The true molecular potential deviates from a perfect parabola, most notably allowing for bond dissociation at large $R$. A widely used empirical model is the **Morse potential**:

$$V(R) = D_e\left[1 - e^{-a(R-R_e)}\right]^2$$

where $D_e$ is the well depth (dissociation energy from the potential minimum) and $a$ controls the well width. This yields an anharmonic energy level expression:

$$E_v = \hbar\omega_e\left(v+\frac{1}{2}\right) - \hbar\omega_e x_e\left(v+\frac{1}{2}\right)^2$$

where $\omega_e x_e$ is the **anharmonicity constant**, typically 1–2% of $\omega_e$.

**Key Points**

- Anharmonicity causes energy levels to become progressively more closely spaced at higher $v$, eventually converging at the dissociation limit
- Anharmonicity relaxes the strict $\Delta v = \pm 1$ selection rule, permitting weak **overtone transitions** ($\Delta v = \pm2, \pm3,\ldots$) with rapidly decreasing intensity
- The true dissociation energy from the ground vibrational state, $D_0$, differs from the potential well depth $D_e$ by the zero-point energy: $D_0 = D_e - \tfrac{1}{2}\hbar\omega_e$

---

### Vibration-Rotation Spectra (Rovibrational Spectra)

Since molecules simultaneously rotate and vibrate, IR absorption spectra show vibrational transitions with superimposed rotational fine structure. For a diatomic, combining the vibrational selection rule ($\Delta v = +1$ for absorption) with the rotational selection rule ($\Delta J = \pm 1$, and $\Delta J = 0$ typically forbidden for $\Sigma$ electronic states) produces two branches:

$$\text{R-branch: } \Delta J = +1, \quad \tilde{\nu}_R = \tilde{\nu}_0 + 2B(J+1)$$



$$\text{P-branch: } \Delta J = -1, \quad \tilde{\nu}_P = \tilde{\nu}_0 - 2BJ$$

**Key Points**

- The **band origin** $\tilde{\nu}_0$ (corresponding to the forbidden $\Delta J=0$ transition) appears as a gap between the P- and R-branches rather than an observed line — the characteristic "missing line" feature of diatomic rovibrational spectra
- The spacing between adjacent lines within a branch is approximately $2B$, allowing simultaneous extraction of both vibrational frequency and rotational constant (and hence bond length) from a single rovibrational band
- For molecules with allowed $\Delta J=0$ transitions (e.g., in certain symmetric top or open-shell systems), a **Q-branch** appears at the band origin

---

### Normal Modes in Polyatomic Molecules

A nonlinear molecule with $N$ atoms has $3N-6$ vibrational degrees of freedom (3N-5 if linear), after removing 3 translational and 3 (or 2, for linear molecules) rotational degrees of freedom. In the harmonic approximation, these decouple into independent **normal modes**, each behaving as an independent harmonic oscillator with its own characteristic frequency.

**Example**

Water ($H_2O$, nonlinear, $N=3$) has $3(3)-6 = 3$ normal modes:

| Mode | Description | Approximate Frequency |
| --- | --- | --- |
| $\nu_1$ (symmetric stretch) | Both O-H bonds stretch in phase | $\approx 3657\ \text{cm}^{-1}$ |
| $\nu_2$ (bend) | H-O-H angle bends | $\approx 1595\ \text{cm}^{-1}$ |
| $\nu_3$ (asymmetric stretch) | O-H bonds stretch out of phase | $\approx 3756\ \text{cm}^{-1}$ |

All three modes change the dipole moment of water and are therefore IR-active — consistent with water's strong and well-studied infrared absorption spectrum, of major importance in atmospheric science (greenhouse effect) and astrophysics.

Carbon dioxide ($CO_2$, linear, $N=3$) has $3(3)-5 = 4$ normal modes (including a doubly degenerate bend), of which the symmetric stretch is IR-inactive (no dipole change, due to the molecule's centrosymmetry) but Raman-active, while the asymmetric stretch and bending modes are IR-active — a textbook illustration of the mutual exclusion rule.

---

### Force Constants and Bond Strength

The vibrational frequency directly encodes bond stiffness:

$$\omega = \sqrt{\frac{k}{\mu}} \quad\Rightarrow\quad k = \mu\omega^2 = 4\pi^2c^2\mu\tilde{\nu}^2$$

**Example**

For CO ($\mu \approx 6.857$ u $\approx 1.139\times10^{-26}$ kg), the observed fundamental vibrational frequency is $\tilde{\nu} \approx 2143\ \text{cm}^{-1}$. Converting to angular frequency:

$$\omega = 2\pi c\tilde{\nu} \approx 2\pi(3\times10^{10}\ \text{cm/s})(2143\ \text{cm}^{-1}) \approx 4.04\times10^{14}\ \text{rad/s}$$

giving a force constant:

$$k = \mu\omega^2 \approx (1.139\times10^{-26})(4.04\times10^{14})^2 \approx 1860\ \text{N/m}$$

This large force constant (compared to typical single bonds, $\sim 500$ N/m) is consistent with CO's very strong triple bond character.

---

### Applications

- **Infrared (IR) spectroscopy** for chemical identification: characteristic group frequencies (C=O stretch, O-H stretch, etc.) enable functional group identification in organic and inorganic chemistry
- **Raman spectroscopy**: complementary to IR, especially valuable for symmetric/centrosymmetric molecules and for aqueous samples (since water's strong IR absorption often interferes with IR measurements)
- **Atmospheric and greenhouse gas monitoring**: vibrational absorption bands of $CO_2$, $H_2O$, $CH_4$, and other gases underlie the greenhouse effect and remote sensing of atmospheric composition
- **Astrophysical spectroscopy**: vibrational (and rovibrational) transitions of interstellar and circumstellar molecules provide diagnostics of temperature, density, and chemical composition in star-forming regions

---

### Related Topics

- Rotational Spectra of Molecules
- The Born-Oppenheimer Approximation
- Molecular Bonding: Ionic and Covalent
- Molecular Orbital Theory
- The Franck-Condon Principle and Electronic-Vibrational Coupling
- Normal Mode Analysis and Group Theory
- Raman Spectroscopy and Polarizability
- Anharmonicity and Molecular Dissociation